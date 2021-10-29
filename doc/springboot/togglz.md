# Tooglz

## Set property as default

```
public enum MyFeatures implements Feature {

    @EnabledByDefault
    @Label("First Feature")
    FEATURE_ONE,

    @Label("Second Feature")
    FEATURE_TWO;
}

@Bean
public FeatureProvider featureProvider() {
    return new EnumBasedFeatureProvider(MyFeatures.class);
}
```

or in `application.properties`

```
togglz.features.SCHEDULER.enabled=true
```


