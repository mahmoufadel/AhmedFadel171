*Ahmed Basha *
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
Implement the Strategy Pattern to handle fetching attachments from different sources (Service A OR Service B). this should be done from Configs.
