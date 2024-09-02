Http/1.1 and Http/2 are two versions of HTTP (hyper text transfer protocol)
whisch is the fundation of data comunication on the web .

**Differences**
### 1  **Request and Response Model**
- Http/1.1 Uses a request-response model where each request requires a separate connection. this Means that for each resource like CSS images or js the client has to establish a new TCP connection or wait for the previous request to be finish before initiating a new one.
- HTTP/2 Introduces multiplexing allowing multiple requests to be sent over a single connection simultaneously .
### 2  **Header Compression**
- HTTP/1.1 headers are sent as plain text and can become large adding overhead to each request
- HTTP/2 Uses HPACK compression for headers whish significly reduces the size of the Headers being transmitted, improving perfomance especialy for repeted requests.

### 3. **Binary Protocol vs Text Protocol**

- **HTTP/1.1**: Is a **text-based** protocol, where headers and the body of messages are in plain text. Parsing and processing can be slower as text is more complex to handle.
- **HTTP/2**: Uses a **binary protocol**, meaning data is sent as binary (encoded as 1s and 0s). This makes it faster and more efficient for computers to parse and process.
### 4. **Multiplexing**

- **HTTP/1.1**: Allows **only one request per connection**. If you want to request multiple resources simultaneously, multiple connections must be opened, or the browser must wait until the current request is complete.
- **HTTP/2**: Supports **multiplexing**, allowing multiple streams (requests/responses) to be sent simultaneously over a single TCP connection. This reduces the overhead of opening multiple connections and speeds up the loading process.
### 5 **Server push**
- **HTTP/1.1** has no mechanism to send resources proactively
- **HTTP/2**: Supports **server push**, where the server can send additional resources to the client without the client having to ask for them (for example, pushing CSS or JavaScript files when an HTML file is requested). This can reduce round trips and improve page load times.
### 6. **Prioritization**

- **HTTP/1.1**: Does not have a built-in prioritization mechanism, meaning all requests are treated equally.
- **HTTP/2**: Allows **stream prioritization**, enabling the client to prioritize certain streams (e.g., critical CSS or JavaScript files) to be delivered first, enhancing the performance and user experience.
### Summary of Differences:

|Feature|HTTP/1.1|HTTP/2|
|---|---|---|
|**Connection**|One per request (keep-alive possible)|Single connection, multiplexed|
|**Request Multiplexing**|No|Yes|
|**Header Compression**|No|Yes (HPACK)|
|**Data Format**|Text-based|Binary|
|**Server Push**|No|Yes|
|**Encryption**|Optional (HTTP/HTTPS)|HTTPS typically required|
|**Prioritization**|No|Yes|
## Status codes
 **500 Server error**
 - 500 internal server error
 **400 User error**
 - 401 unauthorized
 - 403 bad request 
 - 404 NotFound
 **300 redirect**
 - 302 found
 - 301 moved permanently
 **200 Succeed**
 - 200 succeed
 **100 Information**
## Requests
[`GET`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods/GET) (Request some data without body)

The `GET` method requests a representation of the specified resource. Requests using `GET` should only retrieve data.

[`HEAD`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods/HEAD)  (Request headers)

The `HEAD` method asks for a response identical to a `GET` request, but without the response body.

[`POST`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods/POST) (send some data via body)

The `POST` method submits an entity to the specified resource, often causing a change in state or side effects on the server.

[`PUT`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods/PUT) (Replace entier object)

The `PUT` method replaces all current representations of the target resource with the request payload.

[`DELETE`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods/DELETE) (delete data)

The `DELETE` method deletes the specified resource.

[`CONNECT`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods/CONNECT)

The `CONNECT` method establishes a tunnel to the server identified by the target resource.

[`OPTIONS`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods/OPTIONS)

The `OPTIONS` method describes the communication options for the target resource.

[`TRACE`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods/TRACE)

The `TRACE` method performs a message loop-back test along the path to the target resource.

[`PATCH`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods/PATCH)

The `PATCH` method applies partial modifications to a resource.