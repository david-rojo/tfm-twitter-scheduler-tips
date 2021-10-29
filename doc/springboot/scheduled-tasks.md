# Scheduled tasks

## Fixed Rate vs Fixed Delay

Both values are expressed in millisenconds

**The `fixedDelay` property makes sure that there is a delay of n millisecond between the finish time of an execution of a task and the start time of the next execution of the task.**

This property is specifically useful when we need to make sure that only one instance of the task runs all the time. For dependent jobs, it is quite helpful.

**The `fixedRate` property runs the scheduled task at every n millisecond. It doesn't check for any previous executions of the task.**

This is useful when all executions of the task are independent. If we don't expect to exceed the size of the memory and the thread pool, fixedRate should be quite handy.

## Schedule a Task at a Fixed Rate

This option should be used when each execution of the task is independent.

Note that scheduled tasks don't run in parallel by default. So even if we used fixedRate, the next task won't be invoked until the previous one is done.

**If we want to support parallel behavior in scheduled tasks, we need to add the @Async annotation:**

```
@EnableAsync
public class ScheduledFixedRateExample {
    
    @Async
    @Scheduled(fixedRate = 1000)
    public void scheduleFixedRateTaskAsync() throws InterruptedException {
        System.out.println(
          "Fixed rate task async - " + System.currentTimeMillis() / 1000);
        Thread.sleep(2000);
    }
}
```

Now this asynchronous task will be invoked each second, even if the previous task isn't done.

## Parameterizing the Schedule

A fixedDelay task:

```
@Scheduled(fixedDelayString = "${fixedDelay.in.milliseconds}")
```

A fixedRate task:

```
@Scheduled(fixedRateString = "${fixedRate.in.milliseconds}")
```

A cron expression based task:

```
@Scheduled(cron = "${cron.expression}")
```

## Conditionally Enable Scheduled Jobs with @ConditionalOnProperty

It takes a Spring property name and runs only if the property evaluates to true.

First, we create a new class that encapsulates the scheduled job code, including the schedule interval:

```
public class ScheduledJob {
    @Scheduled(fixedDelay = 60000)
    public void cleanTempDir() {
        // do work here
  }
}
```
Then we conditionally create a bean of that type:

```
@Configuration
@EnableScheduling
public class ScheduledJobs {
    @Bean
    @ConditionalOnProperty(value = "jobs.enabled", matchIfMissing = true, havingValue = "true")
    public ScheduledJob scheduledJob() {
        return new ScheduledJob();
    }
}
```

In this case, the job will run if the property jobs.enabled is set to true, or if it's not present at all.

## References

- [Spring.io: Scheduling Tasks](https://spring.io/guides/gs/scheduling-tasks/)
- [Baeldung: The @Scheduled Annotation in Spring](https://www.baeldung.com/spring-scheduled-tasks)
- [Baeldung: Conditionally Enable Scheduled Jobs in Spring](https://www.baeldung.com/spring-scheduled-enabled-conditionally)
- [Baeldung: parametrizing the Schedule](https://www.baeldung.com/spring-scheduled-tasks#parameterizing-the-schedule)