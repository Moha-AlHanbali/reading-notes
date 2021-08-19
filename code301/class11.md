[Home](README.md)

<br>

# Authentication


<br>

## Readings from [What is OAuth? How the open authorization framework works](https://www.csoonline.com/article/3216404/what-is-oauth-how-the-open-authorization-framework-works.html)

<br>

### OAuth definition

<br>

> OAuth is an open-standard authorization protocol or framework that describes how unrelated servers and services can safely allow authenticated access to their assets without actually sharing the initial, related, single logon credential.

> In authentication parlance, this is known as secure, third-party, user-agent, delegated authorization.

<br>

### OAuth examples

<br>

> When you go to log onto a website and it offers one or more opportunities to log on using another website’s/service’s logon. You then click on the button linked to the other website, the other website authenticates you, and the website you were originally connecting to logs you on itself afterward using permission gained from the second website.

<br>

### OAuth explained

<br>

>  OAuth scenarios almost always represent two unrelated sites or services trying to accomplish something on behalf of users or their software. All three have to work together involving multiple approvals for the completed transaction to get authorized.

<br>

### OAuth vs. OpenID

<br>

- At a base level, the distinction between the two is simple to grasp. 

- OpenID is about authentication: as a commenter on StackOverflow pithily put it: "OpenID is for humans logging into machines, OAuth is for machines logging into machines on behalf of humans."

<br>

### OAuth vs. SAML

<br>

- The Security Assertion Markup Language, or SAML, is another technology in the same breath as OAuth.

-  SAML describes a framework that allows one computer to perform both authentication and authorization on behalf of one or more other computers, unlike OAuth, which requires an additional layer like OpenID Connect to perform authentication. 

<br>

### Is OAuth safe

<br>

> TLS can provide all those protections, but it’s up to the implementers, on all sides, to require it to be used. Coders and users should look to ensure that OAuth is running inside of TLS protection.

> Because of the lack of inherent security binding, it’s possible for a rogue website to phish a user’s legitimate credentials during the part of the process where the user is being required to authenticate themselves to the authorization provider.

<br>

## ## Readings from [Authentication and Authorization Flows](https://auth0.com/docs/flows)

<br>

### Introduction

<br>

> Auth0 uses the OpenID Connect (OIDC) Protocol and OAuth 2.0 Authorization Framework to authenticate users and get their authorization to access protected resources. 

>  With Auth0, you can easily support different flows in your own applications and APIs without worrying about OIDC/OAuth 2.0 specifications or other technical aspects of authentication and authorization.

<br>

### Authorization Code Flow

<br>

> Because regular web apps are server-side apps where the source code is not publicly exposed, they can use the Authorization Code Flow, which exchanges an Authorization Code for a token.

<br>

### Authorization Code Flow with Proof Key for Code Exchange (PKCE)

<br>

> During authentication, mobile and native applications can use the Authorization Code Flow, but they require additional security. 

> Additionally, single-page apps have special challenges. To mitigate these, OAuth 2.0 provides a version of the Authorization Code Flow which makes use of a Proof Key for Code Exchange (PKCE).

<br>

### Implicit Flow with Form Post

<br>

> As an alternative to the Authorization Code Flow, OAuth 2.0 provides the Implicit Flow, which is intended for Public Clients, or applications which are unable to securely store Client Secrets.

> While this is no longer considered a best practice for requesting Access Tokens, when used with Form Post response mode, it does offer a streamlined workflow if the application needs only an ID token to perform user authentication.

<br>

### Hybrid Flow

<br>

> Applications that are able to securely store Client Secrets may benefit from the use of the Hybrid Flow, which combines features of the Authorization Code Flow and Implicit Flow with Form Post to allow your application to have immediate access to an ID token while still providing for secure and safe retrieval of access and refresh tokens.

> This can be useful in situations where your application needs to immediately access information about the user, but must perform some processing before gaining access to protected resources for an extended period of time.

<br>

### Client Credentials Flow

<br>

> With machine-to-machine (M2M) applications, such as CLIs, daemons, or services running on your back-end, the system authenticates and authorizes the app rather than a user.

> For this scenario, typical authentication schemes like username + password or social logins don't make sense. Instead, M2M apps use the Client Credentials Flow (defined in OAuth 2.0 RFC 6749, section 4.4).

<br>

### Device Authorization Flow

<br>

> With input-constrained devices that connect to the internet, rather than authenticate the user directly, the device asks the user to go to a link on their computer or smartphone and authorize the device.

> This avoids a poor user experience for devices that do not have an easy way to enter text. To do this, device apps use the Device Authorization Flow (drafted in OAuth 2.0). For use with mobile/native applications.

<br>

### Resource Owner Password Flow

<br>

> Though we do not recommend it, highly-trusted applications can use the Resource Owner Password Flow, which requests that users provide credentials (username and password), typically using an interactive form. 

> The Resource Owner Password Flow should only be used when redirect-based flows (like the Authorization Code Flow) cannot be used.

<br>

## Conclusion

<br>

- What is OAuth?
    - OAuth is an open-standard authorization protocol or framework that describes how unrelated servers and services can safely allow authenticated access to their assets without actually sharing the initial, related, single logon credential.


- Give an example of what using OAuth would look like.
    - > When you go to log onto a website and it offers one or more opportunities to log on using another website’s/service’s logon. You then click on the button linked to the other website, the other website authenticates you, and the website you were originally connecting to logs you on itself afterward using permission gained from the second website.


- How does OAuth work? What are the steps that it takes to authenticate the user?

    > Let’s assume a user has already signed into one website or service (OAuth only works using HTTPS). The user then initiates a feature/transaction that needs to access another unrelated site or service. 

    - The first website connects to the second website on behalf of the user, using OAuth, providing the user’s verified identity.

    - The second site generates a one-time token and a one-time secret unique to the transaction and parties involved.

    - The first site gives this token and secret to the initiating user’s client software.

    - The client’s software presents the request token and secret to their authorization provider (which may or may not be the second site).

    - If not already authenticated to the authorization provider, the client may be asked to authenticate. After authentication, the client is asked to approve the authorization transaction to the second website.

    - The user approves (or their software silently approves) a particular transaction type at the first website.

    - The user is given an approved access token (notice it’s no longer a request token).

    - The user gives the approved access token to the first website.

    - The first website gives the access token to the second website as proof of authentication on behalf of the user.

    - The second website lets the first website access their site on behalf of the user.

    - The user sees a successfully completed transaction occurring.

    - OAuth is not the first authentication/authorization system to work this way on behalf of the end-user. In fact, many authentication systems, notably Kerberos, work similarly. What is special about OAuth is its ability to work across the web and its wide adoption.


- What is OpenID?
    - OpenID is about authentication: as a commenter on StackOverflow pithily put it: "OpenID is for humans logging into machines, OAuth is for machines logging into machines on behalf of humans."


<br>

- What is the difference between authorization and authentication?
    - Authentication:
        - Determines whether users are who they claim to be	
        - Challenges the user to validate credentials (for example, through passwords, answers to security questions, or facial recognition)	
        - Usually done before authorization	
        - Generally, transmits info through an ID Token	
        - Generally governed by the OpenID Connect (OIDC) protocol	
    - Authorization
        - Determines what users can and cannot access
        - Verifies whether access is allowed through policies and rules
        - Usually done after successful authentication
        - Generally, transmits info through an Access Token
        - Generally governed by the OAuth 2.0 framework
        

- What is Authorization Code Flow?
    - Because regular web apps are server-side apps where the source code is not publicly exposed, they can use the Authorization Code Flow, which exchanges an Authorization Code for a token.


- What is Authorization Code Flow with Proof Key for Code Exchange (PKCE)?
    - During authentication, mobile and native applications can use the Authorization Code Flow, but they require additional security. Additionally, single-page apps have special challenges.


- What is Implicit Flow with Form Post?
    - While this is no longer considered a best practice for requesting Access Tokens, when used with Form Post response mode, it does offer a streamlined workflow if the application needs only an ID token to perform user authentication.


- What is Client Credentials Flow?
    - Applications that are able to securely store Client Secrets may benefit from the use of the Hybrid Flow, which combines features of the Authorization Code Flow and Implicit Flow with Form Post to allow your application to have immediate access to an ID token while still providing for secure and safe retrieval of access and refresh tokens


- What is Device Authorization Flow?
    - With input-constrained devices that connect to the internet, rather than authenticate the user directly, the device asks the user to go to a link on their computer or smartphone and authorize the device. This avoids a poor user experience for devices that do not have an easy way to enter text.


- What is Resource Owner Password Flow?
    - Resource Owner Password Flow, which requests that users provide credentials (username and password), typically using an interactive form. The Resource Owner Password Flow should only be used when redirect-based flows (like the Authorization Code Flow) cannot be used.

