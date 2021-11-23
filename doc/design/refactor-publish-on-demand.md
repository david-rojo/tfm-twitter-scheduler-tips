# Refactor: publish on demand

## Add new feature toggle

On `Features.java` add new feature toggle:

```
	@Label("Publish on demand")
	PUBLISH_ON_DEMAND
```

It is disabled by default

![on-demand-disabled](../img/refactor-on-demand/publish-on-demand-togglz-disabled.png)

## Add V2 flyway script

Include script `V2__add_publication_type.sql` with new column and setting default value as `SCHEDULED`

```
ALTER TABLE TWEET
ADD PUBLICATION_TYPE varchar(255) DEFAULT 'SCHEDULED' NOT NULL
```

## Add REST endpoint to controller but returning 405 and hide it from OpenApi documentation

As it is described [here](https://www.baeldung.com/spring-swagger-hiding-endpoints#hiding-an-endpoint-with-hidden), any REST method can be hidden using `@Hidden` annotation when OpenApi v3 is used:

```
@Hidden
	@Operation(
			summary = "Publish a pending tweet immediately", 
			description = "Publish a pending tweet immediately", 
			tags = { "pending" })
    @ApiResponses(value = { 
        @ApiResponse(responseCode = "200", description = "pending tweet successfully published",
                content = @Content(schema = @Schema(implementation = PublishOnDemandResponse.class))),
        @ApiResponse(responseCode = "404", description = "pending tweet not found"),
        @ApiResponse(responseCode = "405", description = "Feature in progress") })
	public ResponseEntity<PublishOnDemandResponse> publishOnDemand(@PathVariable Long id);
```

But method is reachable as it is shown:

![on-demand-disabled](../img/refactor-on-demand/publish-on-demand-controller-toggle-disabled.png)

Tests added:

- Mapper: PublishOnDemandResponseMapperTest (unitary)
- Controller: check that 405 is returned as httpStatus
    - PendingApiControllerTest.publishOnDemandPendingTweetTest() (unitary)
    - PendingApiControllerIT.publishOnDemandPendingTweetTest() (integration)

## Add publicationType to JPA Tweet entity

Publication type has two possible values: SCHEDULED and ON_DEMAND, so best choice to model it is using an enum that later will be used in domain:

```
public enum PublicationType implements ValueObject {

	SCHEDULED,
	ON_DEMAND
}
```

As it is described [here](https://www.baeldung.com/jpa-persisting-enums-in-jpa#string) in order to use this enum in JPA:

```
	@Enumerated(EnumType.STRING)
	private PublicationType publicationType;
```

## Add publicationType to domain and adapt current implementation

Add new attribute in Tweet class:

```
private PublicationType publicationType;
```

Set SCHEDULED value when service needs to persist new Tweet:

- PublisherService.publishPending

```
				tweetPort.create(Tweet.builder()
						.id(published.getId())
						.message(published.getMessage())
						.url(published.getUrl())
						.requestedPublicationDate(pending.publicationDate().instant())
						.publishedAt(published.getPublishedAt())
						.createdAt(NullableInstant.now().instant())
						.publicationType(PublicationType.SCHEDULED)
						.build());	
```

Adapt unitary tests TweetTest in order to take this change in account


## Add PublishPendingTweetOnDemand useCase definition

```
public interface PublishPendingTweetOnDemandUseCase {

	public Optional<Tweet> publishImmediatly(PublishPendingTweetOnDemandOperation operation);
}
```

## Add PublishPendingTweetOnDemand service implementation

Implement service in PublisherService

```
	@Override
	public Optional<Tweet> publishImmediatly(PublishPendingTweetOnDemandOperation operation) {

		final var pending = pendingTweetPort.findOne(operation.getId());

		if (pending.isPresent()) {

			logger.info("Found pending tweet with id = " + pending.get().id() + " to publish on demand");
			final var publishedTweet = twitterService.publish(PublishTweetRequest.builder()
					.message(pending.get().message().message())
					.build());

			logger.info("Successful on demand publication for pending tweet with id = " + pending.get().id().id());
			if (publishedTweet.isPresent()) {

				pendingTweetPort.delete(pending.get().id().id());

				final var tweet = tweetPort.create(Tweet.builder()
						.id(publishedTweet.get().getId())
						.message(publishedTweet.get().getMessage())
						.url(publishedTweet.get().getUrl())
						.requestedPublicationDate(pending.get().publicationDate().instant())
						.publishedAt(publishedTweet.get().getPublishedAt())
						.createdAt(NullableInstant.now().instant())
						.publicationType(PublicationType.ON_DEMAND)
						.build());

				return Optional.of(tweet);
			}		
		}
		return Optional.empty();
	}
```

## Add publicationType to controller

## Enable feature toggle

## Show method in OpenApi

## Remove feature toggle