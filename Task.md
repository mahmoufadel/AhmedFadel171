__Design Patterns Task 20 Feb__
 - https://www.linkedin.com/learning/c-sharp-design-patterns-part-1-14140825/object-oriented-design-patterns-in-c-sharp?dApp=53239054&leis=LAA&u=2113185
 - https://www.linkedin.com/learning/c-sharp-design-patterns-part-2-8579116/object-oriented-design-patterns-in-c-sharp-part-2?dApp=53239054&leis=LAA&u=2113185 


__Linq Task__ 18 Feb 25
- Make all Data access package 9.0.0 to not have confilct (Microsoft.EntityFrameworkCore.SqlServer)..  
- Do Bulk Update by ExecuteUpdateAsync
- Do bulk Delete ExecuteDeleteAsync
- Read those 10 videos and prepare min 10 qustions . https://www.youtube.com/watch?v=9bW8dp1M1Ac&list=PLpbZuj8hP-I6F-Zj1Ay8nQ1rMnmFnlK2f
- Appy **High order Function** (Function accept Function as param)
- Apply **function compisition** (Function return Function)
- Polly again :
  -- Move Retry Policy config from Service  to  "services.AddHttpClient" config
  -- Apply Circuit Breaker Policy as well.
  --  Apply Rate limit policy .
 ``` builder.Services.AddHttpClient<IExternalServiceProvider, ExternalServiceProvider>()
           .ConfigureHttpClient((service,client) => {
               client.BaseAddress = new Uri(externalSettings.Url);
           })
           .ConfigurePrimaryHttpMessageHandler(() => new HttpClientHandler
           {
               ServerCertificateCustomValidationCallback = HttpClientHandler.DangerousAcceptAnyServerCertificateValidator
           })
         .AddPolicyHandler(PollyPolicies.GetRateLimitPolicy()) // Apply rate limiting
         .AddPolicyHandler(PollyPolicies.GetRetryPolicy()) // Apply retry on failure
         .AddPolicyHandler(PollyPolicies.GetCircuitBreakerPolicy()); // Apply circuit breaker
```
  
__Linq Task__ 17 Feb 25
- Add Join with products Table
- Add 5 new ext methods
- Do Bulk Update
- Do bulk Delete .
- Add SQL Logger for Quries

  
__Linq Task__ 16 Feb 25
 - Create new end point to retrive attachments with 2 params (Type, name [use contains]) 
 - Write 4 linq queruies to retirve attachments
   - Using LINQ Method Syntax.
   - Using Dynamic LINQ
   - Using **Dynamic Expressions**
   - Using **Extension Methods**
   - Try to use SQL profiles to see genereted SQL queris (i will show you but after u search)
   - Try to configure you logging to see genereted SQL queris
   - Diff between **Delegate**, **Action<T>**, **Lambda Expression** and for sure **Func<T>** try to use them on your new 4 methods :)

__Links__
- <a  target="_blank"  href="https://www.tutorialsteacher.com/linq" > Working with LINQ: </a>
- <a  target="_blank"  href="https://tyrrrz.me/blog/expression-trees" >Working with expressions trees in C#:</a>
- <a  target="_blank"  href="https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/concepts/expression-trees/" >Expression Trees:</a>
- <a  target="_blank"  href="https://www.tutorialsteacher.com/linq/expression-tree" >Expression Tree: </a>
- <a  target="_blank"  href="https://youtu.be/dwr40KytyaY" >Video. Expression Trees</a>


-----------------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------------

__Http Task__ 10 Feb 25

__Ahmed Basha__
In this task, you will develop a service that fetches product attachments from two external services, handles resilience using Polly, caches the results in MemoryCache, and saves the results to the database. 
You will also use the Strategy Pattern to handle different external services and implement parallel programming for efficiency.

**Requirements**

__External Services__ (don't invist time in implmention)
- Service A Mock : Fetch product attachments (5 props) from the first external service :: it contains 2 types of Attachment (with 2 diff endpoints).
- Service B Mock : Fetch product attachments from the second external service. it contains 3 types of Attachment (with 3 diff endpoints).
 - Use MemoryCache (Use abstract layer) to store fetched results for 10 minutes, preventing duplicate API calls. (use product Id   + attachment type)

__Database Storage__
- Save the fetched attachment data into a Product Attachments table in the database (new Table), ensuring no duplicates are saved.

__Parallel Execution__
- Use parallel programming (e.g., Task.WhenAll) to fetch data from the external services concurrently to improving performance.

__Caching and Resilience__
 - Use Polly to add retries with exponential backoff for failed requests.

__Strategy Pattern__
- Implement the Strategy Pattern to handle fetching attachments from different sources (Service A OR Service B). this should be done from Configs.
