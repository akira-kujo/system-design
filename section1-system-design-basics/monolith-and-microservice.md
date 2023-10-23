## What is a monolith?

* Single-tiered software application where UI and data access code is combined into a **single program** from a **single platform**
  * E.g. Single Java.jar file handling business logic for your entire programme

### Monolith Advantages
* Simple
* Single code base
* Resource efficient

### Monolith Disadvantages
* Hard to enforce as application grows (due to single code base)
* Scaling is a challenge
* Slow to react to customer demand 
* Long release cycles (adding more functionality means checking if other code-bases are impacted)

<img src="/system-design-images/apis-in-monolith.jpg"/>

* API calls are sent into the Monolith via the API GW / LB

### Scenario 1: Issue of Scaling

<img src="/system-design-images/scale-monolith.jpg"/>

* Increase of API calls will stress the EC2 Instance (increase CPU utilisation)
* Solution is to scale the entire monolith (increase the instance account)
  * Increasing ec2s will distribute API calls, reducing CPU utilisation
  * You will still be paying the **full cost** for **both** EC2s

### Scenario 2: APIs in a Microservice

<img src="/system-design-images/scale-microservice.jpg"/>

* The API calls function for different VMs (smaller instances = ↓ cost)
  * *Get* API calls ↑, only the VMs configured for that API call ↑
* Polyglot: Microservices can be written in different programming languages

### What is a microservice architecture?
* Each microservice is independant of eachother
  * Can scale independantly of eachother
  * Can deploy independantly of eachother
  * Can test microservice independantly of eachother
* Main characteristic is
  * Independant scaling
  * Indepdandnt functioning 