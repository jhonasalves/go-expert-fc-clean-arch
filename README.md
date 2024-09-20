# Desafio Clean Arch

Este desafio tem como objetivo criar o use case de listagem de pedidos (orders) utilizando Clean Arch.

## Requisitos do Desafio

- Criar as migrações necessárias para o banco de dados.
- Criar um arquivo `api.http` com as requisições para criar e listar os pedidos.
- Implementar a listagem utilizando:
  - Endpoint REST (GET /order)
  - Serviço ListOrders com gRPC
  - Query ListOrders com GraphQL

## Tecnologias Utilizadas

- Go
- Docker
- MySQL
- gRPC
- GraphQL

## Como Executar

### Pré-requisitos
Certifique-se de ter o Go instalado na sua máquina. Você pode instalá-lo através do site oficial: [Golang](https://golang.org/).

### Passos para Execução

1. **Clone o repositório**:
   ```bash
   git clone https://github.com/jhonasalves/go-expert-fc-clean-arch.git
   cd go-expert-fc-clean-arch
   ```

2. **Suba os containers do Docker**:
    ```bash
    docker-compose up -d
    ```

3. **Execute as migrações para criar a estrutura do banco**:
    ```bash
    make migrate
    ```

4. **Inicie a aplicação**:
    ```bash
    cd cmd/ordersystem
    go run main.go wire_gen.go
    ```

## Testando a Aplicação

### Aplicação REST

Utilize o arquivo `api.http` para realizar as chamadas POST e GET.

### Aplicação gRPC

Para interagir com o serviço gRPC, utilize o Evans:
```bash
evans --proto internal/infra/grpc/protofiles/order.proto --host localhost --port 50051
=> call ListOrders
```

### Aplicação gRPC
Para realizar a consulta GraphQL, você pode utilizar uma ferramenta como o Postman ou um cliente GraphQL:
```bash
query listOrders {
  listOrders {
    id
    price
    tax
    finalPrice
  }
}
```

## Notas
- Certifique-se de que o Docker esteja instalado e em execução antes de iniciar os containers.
- Verifique se as portas mencionadas estão disponíveis e não estão sendo utilizadas por outros serviços.
