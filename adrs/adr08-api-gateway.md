# API Gateway Pattern

## Status
Accepted

## Context
In a [microservices architecture](adr01-microservice-architecture.md), the client apps usually need to consume functionality from more than one microservice. If that consumption is performed directly, the client needs to handle multiple calls to microservice endpoints. This couples the clients to internal endpoints and makes it harder to evolve the micro-services without causing high impact.

Therefore, having API Gateway as a middle man can be convenient for microservice-based applications.

## Decision 
Spotlight platform will use API Gateway as a facade between the clients and the microservices.

## Rationale

Without an API gateway, we can run into the following issues:

- **Coupling:** Without the API Gateway pattern, the client apps are coupled to the internal microservices. The client apps need to know how the multiple areas of the application are decomposed in microservices. When evolving and refactoring the internal microservices, those actions impact maintenance because they cause breaking changes to the client apps due to the direct reference to the internal microservices from the client apps. Client apps need to be updated frequently, making the solution harder to evolve.

- **Too many round trips:** A single page/screen in the client app might require several calls to multiple services. That approach can result in multiple network round trips between the client and the server, adding significant latency. Aggregation handled in an intermediate level could improve the performance and user experience for the client app.

- **Security Issues:** Without a gateway, all the microservices must be exposed to the "external world", making the attack surface larger than if you hide internal microservices that aren't directly used by the client apps. The smaller the attack surface is, the more secure your application can be.

- **Cross-cutting concerns:** Each publicly published microservice must handle concerns such as authorization, SSL, caching and throttling. In many situations, those concerns could be handled in a single tier so the internal microservices are simplified.

With an API Gateway, we get the following features out-of-the-box:

<a name="authorization"></a>**Authorization**:
Authorize access to your APIs at a single place. [oAuth](https://www.oauth.com/oauth2-servers/access-tokens/)/[JWT](https://jwt.io/) tokens can be validated at the gateway level without going to each individual service. Micro-services can simply assume that they get authorized requests.

<a name="caching"></a>**Caching**:
Response caching can be configured at the gateway level, making the platform performant and reducing load on back-end services.

<a name="throttling"></a>**Throttling**:
Throttle traffic to protect back-end services from excess/spiky load and stay unaffected.

<a name="load-balancing"></a>**Load Balancing**:
API Gateway can manage and balance out network traffic just as a Load Balancer, just in a different way. Instead of distributing requests evenly to a set of backend resources (e.g. a cluster of servers), an API Gateway can be configured to direct requests to specific resources based on the endpoints being requested.

## Alternatives Considered

### Direct client-to-microservice communication

This introduces coupling between the clients and for reasons best explained [above](#rationale), this was not a suitable approach for micro-services based architecture.

### Load Balancer as an alternative to API Gateway
A load balancer does not provide features like central authentication & authorization, throttling client-requests and general security measures. It is better suited for distributing load amongst similar applications, which is not the only thing we are looking for here.

## Consequences
- API gateway is yet another moving part that must be developed, deployed and managed. However, this impact can be minimized by leveraging a [managed offering (Amazon)](https://aws.amazon.com/api-gateway/) for the same.
- Response time gets increased due to the additional network hop through the API gateway - however, for most applications the cost of an extra roundtrip is insignificant.

## References
- [API Gateway Pattern](https://microservices.io/patterns/apigateway.html)