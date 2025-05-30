# Sistema de Gerenciamento de Pedidos com Spring Boot

## Visão Geral
Este projeto consiste em uma aplicação web desenvolvida com o framework Spring Boot, focada na criação de um sistema de gerenciamento de pedidos simples, mas abrangente. Utilizando tecnologias como Spring Data JPA para persistência de dados e o banco de dados em memória H2 para facilitar o desenvolvimento e testes, a aplicação demonstra conceitos fundamentais de desenvolvimento web back-end.

## Objetivo
Fornecer uma base sólida para entender como construir aplicações web robustas e escaláveis com o ecossistema Spring. O projeto modela entidades comuns em um sistema de e-commerce, como:

- Usuários
- Produtos
- Categorias
- Pedidos
- Itens de Pedido

## Estrutura e Arquitetura
A aplicação segue uma arquitetura em camadas bem definida:

### Camadas Principais

1. **Camada de Recursos (Resources/Controllers)**
   - Expõe os endpoints da API REST
   - Utiliza anotações como `@RestController` e `@RequestMapping`
   - Classes: `UserResource`, `ProductResource`, `OrderResource`, etc.

2. **Camada de Serviços (Services)**
   - Contém a lógica de negócio da aplicação
   - Marcadas com a anotação `@Service`
   - Classes: `UserService`, `ProductService`, `OrderService`, etc.

3. **Camada de Repositório (Repositories)**
   - Interface de acesso aos dados
   - Estende `JpaRepository`
   - Interfaces: `UserRepository`, `ProductRepository`, `OrderRepository`, etc.

4. **Camada de Entidades (Entities)**
   - Representa o modelo de domínio
   - Utiliza anotações JPA como `@Entity`, `@Table`, `@Id`, etc.
   - Classes: `User`, `Product`, `Order`, `Category`, etc.

### Outros Componentes

- **Configuração (config)**: Classes de configuração como `TestConfig`
- **Tratamento de Exceções**: Classes como `ResourceExceptionHandler` com `@ControllerAdvice`

## Funcionalidades Principais
CRUD básico para as entidades:

- **Usuários**: Cadastrar, listar, buscar por ID, atualizar e deletar
- **Produtos**: Listar e buscar por ID
- **Categorias**: Listar e buscar por ID
- **Pedidos**: Listar e buscar por ID

### Relacionamentos entre Entidades

- Um usuário pode ter múltiplos pedidos (One-to-Many: User → Order)
- Um pedido pertence a um único usuário (Many-to-One: Order → User)
- Um pedido possui um único pagamento (One-to-One: Order ↔ Payment)
- Um pedido contém múltiplos itens de pedido (One-to-Many: Order → OrderItem)
- Um produto pode estar em múltiplos itens de pedido (One-to-Many: Product → OrderItem)
- Produtos e categorias têm relação Many-to-Many (Product ↔ Category)

## Fluxo de Execução

1. **Inicialização**: Spring Boot configura o contexto da aplicação
2. **Perfil 'test'**: Se ativo, popula o banco H2 com dados iniciais
3. **Requisição HTTP**: Cliente envia requisição para um endpoint
4. **Controller**: DispatcherServlet direciona para o Resource apropriado
5. **Service**: Executa lógica de negócio
6. **Repository**: Acessa os dados no banco
7. **JPA/Hibernate**: Traduz para comandos SQL
8. **Retorno**: Dados retornam pela cadeia inversa
9. **Resposta HTTP**: Resource serializa o resultado (geralmente JSON)
10. **Tratamento de Erros**: Exceções são capturadas por `ResourceExceptionHandler`

## Tecnologias Utilizadas

- **Java 17**: Linguagem de programação base
- **Spring Boot**: Framework principal
- **Spring Web (MVC)**: Para APIs RESTful
- **Spring Data JPA**: Para persistência de dados
- **Hibernate**: Implementação da JPA
- **H2 Database**: Banco de dados em memória
- **Maven**: Gerenciamento de dependências e build

## Como Executar

1. Clone o repositório
2. Configure o ambiente com Java 17 e Maven
3. Execute a classe principal `CourseApplication`
4. Acesse os endpoints conforme documentação
