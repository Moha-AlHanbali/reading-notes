[Home](README.md)

<br>

# CRUD


<br>

## Readings from [Which HTTP Status Code to Use for Every CRUD App](https://www.moesif.com/blog/technical/api-design/Which-HTTP-Status-Code-To-Use-For-Every-CRUD-App/)

<br>

### HTTP Status Codes

<br>

> A status code is a number higher than 100 and smaller than 600 that is part of a HTTP response.

> The first digit defines the class of the status. A status code comes with a reason phrase. 

> The code is for programmatic recognition the phrase is for humans to understand what happened.

<br>

#### Status Classes

<br>

- 100 - 199
  - These are informational status codes; they usually tell the client that the header part of the request has been received and the server will try to comply with a transmission demand of the client.
  - Like using a different protocol or telling the client that its request will fail before they start sending the body.

  <br>

- 200 - 299
  - These are the success codes.
  - They tell the client that its request was accepted.
  - In case of asynchronous processing of a request (202), this doesn’t mean the request was successfully processed only that it met all validation requirements at the time of sending.

<br>

- 300 - 399
  - These are redirection codes.
  - They tell the client that the resource they are requesting isn’t available at the expected location anymore. 
  -This can have multiple reasons, be temporary or permanent, but the client has to issue a request to the new location.

<br>

- 400 - 499
  - These are the client error codes.
  - They are all about invalid requests a client sent to a server.
  - There are several causes to this, timeouts, wrong URI, missing authentication, etc.
  - A client is sending incorrect input and should confirm the input parameters are correct before retrying the request.

<br>

- 500 - 599
  - These are the server error codes.
  - Often they indicate problems with overwhelmed servers or unreachable servers behind proxies, but sometimes they can be directly related to client requests that trigger error exceptions on the server.
  - These errors can be temporary or permanent. Usually it’s best for the client to retry the same request.

<br>

- Custom Classes
  - Custom classes, that is, classes above 599 aren’t permitted but used by some services anyway.
  - For API designers, they are relevant as bad examples. API client creators, however, have to deal with them.

<br>

### CRUD (Create, Read, Update, Delete)

<br>

> The CRUD model defines the most basic API actions for persistent storage. 
> `Create`, `read`, `update`, and `delete`. They make up the lions-share of API endpoints.

<br>

#### CREATE

<br>

> The create action is usually implemented via HTTPs POST method. In RESTful APIs, these endpoints are used to create new resources or access tokens.

- 200 OK
  - It’s the basic status code to tell the client everything went good.

- 201 Created
  - The most fitting for Create operations. This code should signal backend-side resource creation and come along with a Location header that defines the most specific URL for that newly created resource. 

- 202 Accepted 
  - Often used for asynchronous processing. This code tells the client that the request was valid, but its processing will finish sometime in the future.

- 303 See Other
  - Like the 202 code but using a Location header field in response to informing the client about the location of the created resource or an endpoint that lets the client check for the status of the creation process. 

<br>

#### READ

<br>

> The read action gets implemented via HTTPs GET method and used to fetch resource representations. 

> Asynchronous responses aren’t much of a thing here, because the reason for asynchronous processing is often that the resource doesn’t exist yet and has to be created, so it’s a create action anyway.

- 200 OK
  - Most of the read actions will be answered with a 200 OK status.

- 206 Partial Content
  - This code is useful for lists of content that are too big to be delivered in one response.

- 300 Multiple Choices 
  - This redirect is used if there are multiple representations for one resource and the client (or its user) has to choose one of them.

- 308 Permanent Redirect
  - This tells the client to use another URL to access the resource and not use the current URL anymore. 

- 304 Not Modified
  - Is used like 200 but without a body, so the client will be redirected to its locally cached representation from a previous read.

- 307 Temporary Redirect 
  - When the URL to a resource could change in the future, and the client should always ask the current URL before accessing the real one.

<br>

#### UPDATE

<br>

> An update can be implemented with an HTTP PUT or PATCH method. The difference lies in the amount of data the client has to send to the backend.

> PUT requires the client to send an entire representation of a resource to update it. (Replace the old one with the new one)

> PATCH requires the client only send parts of the representation of the resource to update it. (Add, update or delete these parts in the old version)

- 200 OK 
  - This is the most appropriate code for most use-cases.

- 204 No Content 
  - A proper code for updates that don’t return data to the client, for example when just saving a currently edited document.

- 202 Accepted 
  - If the update is done asynchronous, this code can be used. It should include an URL to access the updated resource or an URL to check if the update has been succeeded. 
  - It can also include an estimation of how long the update will take.

<br>

#### DELETE

<br>

- 200 OK 
  - Some people think a delete function of any kind should return the deleted element, so a representation of the deleted element can be included in the response body.

- 204 No Content 
  - The most fitting status code for this case. It’s better to reduce traffic and simply tell the client the deletion is complete and return no response body (as the resource has been deleted).

- 202 Accepted 
  - If the deletion is asynchronous and takes some time, which is the case in distributed systems, it can be appropriate to return this code with some information or URL to tell the client when it will be deleted.

<br>

#### API Changes

<br>

- 307 Temporary Redirect 
  - This is the right code if the resource could be available on a different URL in the future, but we want the current endpoint to control where the client is redirected to. 
  - This status code will let the client come back to the current URL for every request.

<br>

- 308 Permanent Redirect 
  - This is the right code if the resource will now be available at a new URL and the client should directly access it via the new URL in the future. 
  - The current endpoint can’t control the clients’ behavior after the request and a subsequent redirect if the resource URL changes again have to be issued from the new URL.

<br>

##### Multiple Endpoints for One Resource

<br>

> If we opt-in to use nested or sub-resources in our API it can help to only deliver representations from root (non-nested) resources to keep the implementation DRY. Redirect status codes help with this.

- 308 Permanent Redirect 

<br>

#### Errors

<br>

> Many API frameworks use 500 and 404 status codes by default when something went wrong, but depending on the situation, often there are more descriptive ones.

> 500 means Internal Server Error, which can be anything from a missing header field the backend accessed without checking its existence to an unreachable third party service the backend wanted to call.

> So it can be that the client did something wrong and we would expect a 400-499 status code.

> 404 means Not Found. This can be because of a wrong URL used by the client to some endpoint not being set up right on the backend.

<br>

#### Wrong URL

<br>

- 404 Not Found 
  - This is the most natural of responses and should be used in the case that the client URL was wrong.

- 405 Method Not Allowed 
  - In many frameworks we define the URL alongside the HTTP method, so removing one of these definitions could leave all but one methods to one URL intact. The response has to include an Allow header field that lists what is allowed to do.

- 501 Not Implemented 
  - Like 405, but the method is missing for all resources on the backend.

- 406 Not Acceptable 
  - The URL exists, but the backend can’t send a representation the client will accept. So for that specific client, the URL behaves like a 404, but they now know that they need to update the client.

- 410 Gone 
  - This is like 404 but we know that the resource existed in the past, but it got deleted or somehow moved, and we don’t know where.

- 414 Request-URI Too Long 
  - This is sometimes the case when the endpoint is right, and the resource exists, but the query makes the URL too long to be interpreted.

- 308 Permanent Redirect 
  - This would be the right code if we know that a resource has moved to a different URL and we can tell the client about it.

- 307 Temporary Redirect 
  - Same as 308, but we don’t know if the resource will be back on the original URL or another different URL in the future.

<br>

#### No Permissions

<br>

- 401 Unauthorized 
  - The client hasn’t authorized itself to the backend yet and the server may give it access after that has happened.

- 403 Forbidden 
  - The client has authorized or doesn’t need to authorize itself, but still has no permissions to access the resource.

- 404 Not Found 
  - If 401 or 403 is the case, but the backend doesn’t want to tell the client that the resource exists for security reasons.

<br>

## Conclusion

<br>

- In your own words, describe what each group of status code represents:
  - 100’s = These are informational status codes.
  - 200’s = These are the success codes.
  - 300’s = These are redirection codes.
  - 400’s = These are the client error codes.
  - 500’s = These are the server error codes.

- What is a status code 202?
  -  Accepted.

- What is a status code 308?
  - Permanent Redirect

- What code would you use if an update didn’t return data to a client?
  - 204 No Content

- What code would you use if a resource used to exist but no longer does?
  - 410 Gone

- What is the ‘Forbidden’ status code?
  - 403

<br>

- Why do we need to pull our MongoDB database string out of our server and put it into our .env?


- What is middleware?
  - Functions that have access to the request object ( req ), the response object ( res ), and the next function in the application's request-response cycle.

- What does app.use(express.json()) do?
  - Allowes the server to accept JSON as a body inside elements.

- What does the /:id mean in a route?
  - The route will be the passed id argument in the middleware function.

- What is the difference beween PUT and PATCH?
  - PUT requires the client to send an entire representation of a resource to update it. (Replace the old one with the new one)
  - Patch requires the client only send parts of the representation of the resource to update it. (Add, update or delete these parts in the old version)

- How do you make a defalut value in a schema?
  - Create an object-like data model within it with key name and value data type.

- What does a 500 error status code mean?
  - Internal Server Error

- What is the difference between a status 200 and a status 201?
  - 200: OK, it’s the basic status code to tell the client everything went good.
  - 201: Created, the most fitting for Create operations. This code should signal backend-side resource creation and come along with a Location header that defines the most specific URL for that newly created resource.
