# Desafio Dio - Docker: Utilização Prática no Cenário de Microsserviços



**Projeto Abrangente de Microsserviços Usando Docker**



Docker é uma plataforma de contêiner que permite aos desenvolvedores empacotar e executar aplicações em ambientes isolados e portáteis. Este projeto fornece uma estrutura abrangente para construir e implantar uma arquitetura de microsserviços usando Docker.



### **Requisitos**

- Docker
- Docker Compose
- Linguagem de programação (por exemplo, Java, Python)



### **Estrutura do Projeto**

O projeto será estruturado em vários microsserviços, incluindo:



- **Serviço de API Gateway:** Roteia solicitações para os microsserviços apropriados.
- **Serviço de Usuário:** Gerencia usuários e autenticação.
- **Serviço de Produto:** Gerencia produtos e catálogos.
- **Serviço de Pedido:** Gerencia pedidos e pagamentos.



### **Implementação**

### **Serviço de API Gateway**

dockerfile



```dockerfile
FROM nginx
COPY nginx.conf /etc/nginx/nginx.conf
```



### **Serviço de Usuário**

java



```java
@SpringBootApplication
public class UserServiceApplication {

    public static void main(String[] args) {
        SpringApplication.run(UserServiceApplication.class, args);
    }
}
```



**Serviço de Produto**

python



```python
from flask import Flask

app = Flask(__name__)

@app.route("/products")
def get_products():
    return {"products": ["Produto 1", "Produto 2"]}

if __name__ == "__main__":
    app.run(host="0.0.0.0", port=5000)
```



### **Serviço de Pedido**

java



```java
@Entity
@Table(name = "orders")
public class Order {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private Long userId;
    private Long productId;
    private int quantity;

    // ... outros campos
}
```



### **Docker Compose**

yaml



```yaml
version: "3.7"

services:
  api-gateway:
    image: nginx:latest
    ports:
      - "80:80"
    volumes:
      - ./nginx.conf:/etc/nginx/nginx.conf
  user-service:
    image: user-service:latest
    ports:
      - "8080:8080"
  product-service:
    image: product-service:latest
    ports:
      - "5000:5000"
  order-service:
    image: order-service:latest
    ports:
      - "8090:8090"
```



### **Conclusão**

Este projeto fornece uma base abrangente para construir e implantar uma arquitetura de microsserviços usando Docker. Ele aborda aspectos essenciais como roteamento de API, gerenciamento de usuários, gerenciamento de produtos e processamento de pedidos. Ao implementar essas estratégias, os desenvolvedores podem criar microsserviços robustos e escaláveis que atendam aos requisitos específicos de suas aplicações.
