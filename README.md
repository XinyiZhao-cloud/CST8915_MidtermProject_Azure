# Links to repos
- Order Analytics Service: https://github.com/XinyiZhao-cloud/order-analytics-service
- Order Service: https://github.com/XinyiZhao-cloud/order-service
- Store Front: https://github.com/XinyiZhao-cloud/store-front
- Product Service: https://github.com/XinyiZhao-cloud/product-service-python

---

# Demo Video
🎥 https: https://youtu.be/AU_iUTIWqoo

---

# Azure Deployment – RabbitMQ Infrastructure
- RabbitMQ was deployed on an Azure Virtual Machine running Ubuntu and managed using Docker with the official rabbitmq:3-management image. The container exposes port 5672 for AMQP messaging and 15672 for the management interface.    

- Inbound rules were configured in the VM’s Network Security Group to allow traffic on ports 5672 and 15672, enabling secure communication between Azure App Services and RabbitMQ.   

- A queue named order_queue was created with durable set to false, matching the assignment requirements. The order-service publishes messages to this queue, and the order-analytics-service consumes them.  

- Both services were configured using environment variables (RABBITMQ_URL and QUEUE_NAME) in Azure App Service, following 12-Factor App principles and treating RabbitMQ as a backing service.
<img width="457" height="318" alt="Screenshot 2026-02-23 at 1 41 47 PM" src="https://github.com/user-attachments/assets/d95ce93f-074d-4083-811a-5df1fb1e13e1" />

## Why choose Docker?
Docker was chosen to provide a clean, isolated, and reproducible deployment environment, making it easier to manage dependencies, restart services, and reset the system for testing and demos.

---

## End-to-end testing confirmed that:
- Orders placed through the Static Web App are published to RabbitMQ. 
- The analytics service consumes messages in real time.
- Analytics endpoints(/health, /orders, /analytics/summary, /analytics/products, /analytics/top-products) update correctly.  
<img width="1468" height="859" alt="Screenshot 2026-02-23 at 3 09 51 PM" src="https://github.com/user-attachments/assets/f7574c91-0593-44ed-80ab-a894adf7bc67" />
<img width="1470" height="858" alt="Screenshot 2026-02-23 at 3 09 34 PM" src="https://github.com/user-attachments/assets/9b804224-2341-4ea0-ae2d-536178e8320e" />
<img width="1469" height="853" alt="Screenshot 2026-02-23 at 3 08 52 PM" src="https://github.com/user-attachments/assets/47da52d9-9f81-4b6c-a659-42e66fe1ce1a" />
<img width="1470" height="857" alt="Screenshot 2026-02-23 at 3 09 09 PM" src="https://github.com/user-attachments/assets/7c5e11f2-7930-4324-b72e-3f79016c7497" />

<img width="1466" height="852" alt="Screenshot 2026-02-23 at 3 08 29 PM" src="https://github.com/user-attachments/assets/46ad5d31-be3a-4c26-a8b4-32a641d7b537" />

