## What is Monolithic and Microservices Application

The purpose of this blog is to introduce you to the concept of microservices. What is a microservice, why do you need them, and why are they so significant? There will be a series of blogs in the near future about Kubernetes, the first of which is this one. 

# The Legacy Monolithic

![12.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662018384007/YDxLnlfYr.png align="left")

A **monolithic** has a rather expensive taste in hardware. Being a large, single piece of software that continuously grows, it has to run on a single system that has to satisfy its compute, memory, storage, and networking requirements. The hardware of such capacity is not only complex and extremely pricey but at times challenging to procure.

Since the entire monolith application runs as a single process, the scaling of individual features of the monolith is almost impossible. It internally supports a hardcoded number of connections and operations. However, scaling the entire application can be achieved by manually deploying a new instance of the monolith on another server, typically behind a load-balancing appliance - another pricey solution.

During upgrades, patches, or migrations of the monolith application downtime is inevitable and maintenance windows have to be planned well in advance as disruptions in service are expected to impact clients. While there are third-party solutions to minimize downtime to customers by setting up monolith applications in a highly available active/passive configuration, they introduce new challenges for system engineers to keep all systems at the same patch level and may introduce new possible licensing costs.

# The Modern Microservices

![12.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662018425907/iCa9wj96u.png align="left")

**Microservices** can be deployed individually on separate servers provisioned with fewer resources - only what is required by each service and the host system itself, helping to lower compute resource expenses.

Microservices-based architecture is aligned with Event-driven Architecture and Service-Oriented Architecture (SOA) principles, where complex applications are composed of small independent processes which communicate with each other through APIs over a network. APIs allow access by other internal services of the same application or external, third-party services and applications.

Each microservice is developed and written in a modern programming language, selected to be the best suitable for the type of service and its business function.

Although the distributed nature of microservices adds complexity to the architecture, one of the greatest benefits of microservices is scalability. With the overall application becoming modular, each microservice can be scaled individually, either manually or automated through demand-based autoscaling.

Seamless upgrades and patching processes are other benefits of microservices architecture. There is virtually no downtime and no service disruption to clients because upgrades are rolled out seamlessly - one service at a time, rather than having to re-compile, re-build and re-start an entire monolithic application. As a result, businesses are able to develop and roll out new features and updates a lot faster, in an agile approach, having separate teams focusing on separate features, thus being more productive and cost-effective.

# Refactoring

Newer, more modern enterprises possess the knowledge and technology to build cloud-native applications that power their business.

Unfortunately, that is not the case for established enterprises running on legacy monolithic applications. Some have tried to run monoliths as microservices, and as one would expect, it did not work very well. The lessons learned were that a monolithic size multi-process application cannot run as a microservice and that other options had to be explored. The next natural step in the path of the monolith to microservices transition was refactoring

The refactoring phase slowly transforms the monolith into a cloud-native application that takes full advantage of cloud features, by coding in new programming languages and applying modern architectural patterns. Through refactoring, a legacy monolith application receives a second chance at life - to live on as a modular system adapted to fully integrate with today's fast-paced cloud automation tools and services.

# Challenges

![11.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662018506650/I1ehMAmr-.png align="left")

The refactoring path from a monolith to microservices is not smooth and without challenges. Not all monoliths are perfect candidates for refactoring, and some may not even "survive" such a modernization phase. When deciding whether a monolith is a possible candidate for refactoring, there are many possible issues to consider.

Once the monolith survived the refactoring phase, the next challenge is to design mechanisms or find suitable tools to keep alive all the decoupled modules to ensure application resiliency as a whole.

Ultimately application containers came along, providing encapsulated lightweight runtime environments for application modules. Containers promised consistent software environments for developers, and testers, all the way from Development to Production. Wide support of containers ensured application portability from physical bare-metal to Virtual Machines, but this time with multiple applications deployed on the very same server, each running in their own execution environments isolated from one another, thus avoiding conflicts, errors, and failures. Other features of containerized application environments are higher server utilization, individual module scalability, flexibility, interoperability, and easy integration with automation tools.

# success stories

Although a challenging process, moving from monoliths to microservices is a rewarding journey especially once a business starts to see growth and success delivered by a refactored application system. Below we are listing only a handful of the success stories of companies that rose to the challenge to modernize their monolith business applications. A detailed list of success stories is available at the Kubernetes website: [Kubernetes User Case Studies](https://kubernetes.io/case-studies/).
- [AppDirect](https://kubernetes.io/case-studies/appdirect/) - an end-to-end commerce platform provider, started from a complex monolith application and through refactoring was able to retain limited functionality monoliths receiving very few commits, but all new features implemented as containerized microservices.
- [box](https://kubernetes.io/case-studies/box/) - a cloud storage solutions provider, started from a complex monolith architecture and through refactoring was able to decompose it into microservices.
- [Crowdfire](https://kubernetes.io/case-studies/crowdfire/) - a content management solutions provider, successfully broke down their initial monolith into microservices.
- [GolfNow](https://kubernetes.io/case-studies/golfnow/) - a technology and services provider, decided to break their monoliths apart into containerized microservices.
- [Pinterest](https://kubernetes.io/case-studies/pinterest/) - a social media services provider, started the refactoring process by first migrating their monolith API.**Annotate**

# Concusion
Microservices architecture is a distributed design approach intended to overcome the limitations of traditional monolithic architectures. Microservices help to scale applications and organizations while improving cycle times. However, they also come with a couple of challenges that might add additional architectural complexity and operational burden.

