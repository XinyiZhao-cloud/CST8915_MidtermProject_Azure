RabbitMQ VM (Azure)

VM Public IP: <ip>

RabbitMQ Management UI: http://<ip>:15672

Username: petstore

Password: <pass>

Queue: order_queue

Connection string for services:

amqp://petstore:<pass>@<ip>:5672

Required App Service env vars

RABBITMQ_URL=amqp://...

PORT=3000/3030/4000 (or let Azure set port & bind to process.env.PORT)

Any other service URLs they use (like product-service endpoint, etc.)
