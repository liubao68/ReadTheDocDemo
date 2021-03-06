## 表1-1术语表

| 缩略语 | 英文词汇 | 中文词汇 | 解释 |
| :--- | :--- | :--- | :--- |
| CSE | Cloud Service Engine | 微服务框架 | 微服务引擎，作为一个公有云服务，在开发层面提供一组工具和开发框架，方便进行本地的微服务开发，同时在云上提供一组支撑微服务运行和运维的基础服务，方便微服务在云上生产环境的部署和运维。 |
| MicroServices | MicroServices | 微服务 | 微服务是一种轻量级SOA架构，通常用来描述广泛用于云应用、互联网应用的一种松耦合分布式架构。 |
| Provider | Provider | 服务提供者 | 在微服务调用关系中处于被调用一方的服务。 |
| Consumer | Consumer | 服务消费者 | 在微服务调用关系中处于调用发起方的服务。 |
| Application | Application | 应用 | 应用代表一个软件应用的逻辑实体，表示一个有业务功能呈现给用户的计算机软件应用。一个以微服务化架构构建的应用通常由多个微服务组成。 |
| Instance | Instance | 微服务实例 | 一个微服务的最小运行和部署单元，通常对应一个应用进程。 |
| IAM | Identity and Access Management | 身份及权限管理 | 负责PaaS系统中管理层级、用户、角色、授权关系，用户的组织归性等信息的维护。并实施授权和授权检查。 |
| AK/SK | AK/SK | AK/SK密钥 | Access key/Secret key是一组密钥对，用于API的身份认证和访问控制。 |
| Service | Service | 服务 | 服务是对按需取用的功能对象的一种描述。在应用模型中，服务一般面向应用，应用使用服务需要先订购服务，再绑定服务并使用，某些商业场景下可能还需要按使用量付费。 |
| AB test | AB test | 灰度发布 | CSE支持两种灰度发布策略。按照流量百分比的引流——可以设定引流规则，设置不同占比的流量到特定的服务版本。按照特定请求特征进行的引流——根据请求头的特征设置引流规则，符合某些规则的流量进入特定的服务版本。以此方式保证服务的平滑演进。 |
| Distributed Transaction | Distributed Transaction | 分布式事务 | 分布式事务是指事务的参与者、资源服务器以及事务管理器分别位于分布式系统的不同节点之上的事务。CSE支持两种分布式事务方案：1 基于TCC协议的最终一致性方案 2 基于两阶段提交的强一致性方案。 |
| Load Balance | Load Balance | 负载均衡 | 当应用访问一个具有多个实例的微服务时，会涉及到路由负载均衡。CSE提供基于Ribbon的负载均衡方案，可以通过配置文件配置负载均衡策略，支持随机，轮询、会话保持和基于响应时间的权值等多种负载均衡路由策略。 |
| Rate limit | Rate limit | 限流 | 当资源成为瓶颈时，服务框架需要对消费者的访问请求做限流，启动流控保护机制。在服务消费者端和提供者端均可进行流量控制。在服务消费端，可以限制发往某个微服务提供者的请求频率；在服务提供端，可以限制每个微服务消费端发过来的请求频率，也可以根据服务提供端资源消耗情况确定总的请求频率限制，防止服务因资源耗尽而崩溃。 |
| Service Degrade | Service Degrade | 降级 | 服务降级主要包括屏蔽降级和容错降级两种策略：屏蔽降级是指当外界的触发条件达到某个临界值时，由运维人员/开发人员决策，对某类或者某个服务进行强制降级。容错降级是指当非核心服务不可用时，可以对故障服务做业务逻辑放通，以保障核心服务的运行。 |
| Fault tolarance | Fault tolarance | 容错 | 容错是消费者访问服务时出现异常的场景下的一种处理策略，出现异常后由服务框架自动选择新的服务路由进行调用。 |
| Circuit Breaker | Circuit Breaker | 熔断 | 微服务之间通常存在依赖关系，服务调用链路可能包含多个微服务，如果链路中一个或多个服务访问延迟过高，会导致入口服务的请求不断堆积，持续消耗更多的线程、io资源，最终由于资源累积使系统出现瓶颈，造成更多服务不可用，产生雪崩效应。熔断机制就是针对上述场景设计的，当某个目标服务响应缓慢或者有大量超时情况发生时，熔断该服务的调用，对于后续调用请求，不再继续调用目标服务，直接返回，快速释放资源，等到该目标服务情况好转再恢复调用。 |
| Isolation | Isolation | 隔离 | 服务隔离是一种异常检测机制，常用的检测方法是请求超时、流量过大等。一般的设置参数包括超时时间、最大并发请求数等，当超过超时时间或最大并发请求数时，记录一次异常，并用于在熔断机制中计算错误率和错误请求数。 |
| Service Mesh | Service Mesh | 服务网格 | 一种基础设施层服务。在微服务化的过程中，开发者需要解决应用运行在分布式网络中所引入的问题，例如容错，限流，负载均衡，注册发现，可监控等，Service Mesh作为L4/L7协议代理，为应用解决了微服务化后带来的问题。 |
| legacy | legacy | 遗留系统 | 遗留系统是一个还在运行和使用，但已步入软件生命周期衰老期的软件系统。 |



