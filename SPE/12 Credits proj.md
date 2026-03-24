**Title:**  
Performance Evaluation of Distributed System Architectures under Varying Load Conditions

---

### Description

- This project evaluates how different system architectures behave under increasing load conditions.
    
- The same application will be implemented in multiple designs:
    
    - Monolithic system
        
    - Synchronous microservices system
        
    - Asynchronous queue-based system
        
- The application logic remains constant while only the architecture changes to ensure fair comparison.
    

---

### System Implementation

- Services will be developed in Go.
    
- Communication between services will use HTTP.
    
- Asynchronous processing will be implemented using RabbitMQ and worker services.
    
- Data will be stored in PostgreSQL, with optional Redis caching.
    
- Nginx will be used as API Gateway and Kubernetes Ingress for load balancing.
    
- All components will be containerized using Docker and managed using Docker Compose for local setup.
    
- Deployment and scaling will be handled using Kubernetes.
    

---

### Load Testing

- Load will be generated using k6.
    
- Traffic levels will be gradually increased (e.g., 100, 1,000, 10,000+ requests per second).
    

---

### Monitoring and Logging

- Prometheus will collect system metrics.
    
- Grafana will be used to visualize performance data.
    
- ELK stack will be used for centralized logging.
    

---

### Metrics Evaluated

- Latency
    
- Throughput
    
- Error rate
    
- CPU and memory usage
    
- Queue length and processing delay
    

---

### Objective

- To compare different architectural designs and analyze how asynchronous processing, caching, and scaling improve system performance and resilience under high load.
    

---

### Outcome

- A comparative analysis of system architectures based on performance metrics.
    
- Insights into how design choices impact scalability and reliability in distributed systems.
    

---