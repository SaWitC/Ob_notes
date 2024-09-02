#net
#questions
### Description
Polly is a .NET resilince and transient-fault-handling library that allows developers to express resilence strategies such as Retry, Circuit Breaker, Hedging Timeout, Rate Limiter and Fallback in a fluent and thread-safe manner

Get Started
1
```
dotnet add package Polly.Core
```
2
```c#
// Create an instance of builder that exposes various extensions for adding resilience strategies
ResiliencePipeline pipeline = new ResiliencePipelineBuilder()
    .AddRetry(new RetryStrategyOptions()) // Add retry using the default options
    .AddTimeout(TimeSpan.FromSeconds(10)) // Add 10 seconds timeout
    .Build(); // Builds the resilience pipeline

// Execute the pipeline asynchronously
await pipeline.ExecuteAsync(static async token => { /* Your custom logic goes here */ }, cancellationToken);
```
**OR**
1
```
dotnet add package Polly.Extensions
```
2
```c#
var services = new ServiceCollection();

// Define a resilience pipeline with the name "my-pipeline"
services.AddResiliencePipeline("my-pipeline", builder =>
{
    builder
        .AddRetry(new RetryStrategyOptions())
        .AddTimeout(TimeSpan.FromSeconds(10));
});

// Build the service provider
var serviceProvider = services.BuildServiceProvider();

// Retrieve a ResiliencePipelineProvider that dynamically creates and caches the resilience pipelines
var pipelineProvider = serviceProvider.GetRequiredService<ResiliencePipelineProvider<string>>();

// Retrieve your resilience pipeline using the name it was registered with
ResiliencePipeline pipeline = pipelineProvider.GetPipeline("my-pipeline");

// Alternatively, you can use keyed services to retrieve the resilience pipeline
pipeline = serviceProvider.GetRequiredKeyedService<ResiliencePipeline>("my-pipeline");

// Execute the pipeline
await pipeline.ExecuteAsync(static async token =>
{
    // Your custom logic goes here
});
```
##### Resilience strategies
1. Reactive
these strategies handle specific exceptions that are thrown or results that are returned by the callback executed through the strategy.
2. Proactive 
Unlike reactive strategies proactive strategies do not focus on handling errors but the callbacks might throw or return. They can make proactive decision to cancel or reject the execution of fallback

### Questions
1. What we use it for (we use it )
2. What are the advantages
3. How to implement
4. What are the examples in practice
## Polly
1)what for we use it 
- to automaticly retry failed operations a specified number of times
- To specify Time out policy
- Fall back policy
- Cache policy
2)what are the advantages
- **Improved Resilience**: Automatically handle transient faults and improve the overall reliability of your application.
- **Simplified Error Handling**: Centralize error handling logic through policies, reducing boilerplate code.
3)how to implement
- Create polliy and then apply it to a specific httpClient
- 
4)What are the examples in practice 
- Create retry Policy