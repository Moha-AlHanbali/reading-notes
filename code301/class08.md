[Home](README.md)

<br>

# APIs

<br>

## Conclusion of Readings from [RESTful web API design](https://docs.microsoft.com/en-us/azure/architecture/best-practices/api-design)

<br>

- What does REST stand for?
    - Representational State Transfer

- REST APIs are designed around  ____.
    - resources (any kind of object, data, or servics)
    
- What is an identifer of a resource? Give an example.
    - `URI` that uniquely identifies that resource.

- What are the most common HTTP verbs?
    - `GET`, `POST`, `PUT`, `PATCH`, and `DELETE`.


- What should the URIs be based on?
    - nouns (the resource).

- Give an example of a good URI.
    - `/orders`

- What does it mean to have a ‘chatty’ web API? Is this a good or a bad thing?
    - Web APIs that expose a large number of small resources. 

- What status code does a successful GET request return?
    - A successful GET method typically returns HTTP status code 200 (OK).
    
- What status code does an unsuccessful GET request return?
    -  If the resource cannot be found, the method should return 404 (Not Found).

- What status code does a successful POST request return?
    - If a POST method creates a new resource, it returns HTTP status code 201 (Created). 

- What status code does a successful DELETE request return?
    - If the delete operation is successful, the web server should respond with HTTP status code 204 (No Content).
