# Projeto Nivelamento Sobre JPA
Este projeto é um exemplo de como utilizar o framework JPA para persistência de dados em banco de dados relacional. A classe Pessoa é uma entidade mapeada com a anotação @Entity, que será mapeada para uma tabela no banco de dados. O objetivo do projeto é demonstrar como criar, alterar e excluir registros utilizando o JPA.

## Tecnologias utilizadas
- Java 11
- Maven
- JPA 2.1
- Hibernate 5.6.1.Final
- MySQL Connector/J 8.0.27

## Como utilizar
1. Clone o repositório para a sua máquina local;
2. Importe o projeto na sua IDE;
3. Configure as informações de conexão com o banco de dados no arquivo persistence.xml;
4. Execute a classe Programa para persistir dados na tabela pessoa.

## Dependências
As seguintes dependências são necessárias para a execução do projeto:
```xml
<dependencies>
    <dependency>
        <groupId>org.hibernate</groupId>
        <artifactId>hibernate-core</artifactId>
        <version>5.6.1.Final</version>
    </dependency>
    <dependency>
        <groupId>org.hibernate</groupId>
        <artifactId>hibernate-entitymanager</artifactId>
        <version>5.6.1.Final</version>
    </dependency>
    <dependency>
        <groupId>mysql</groupId>
        <artifactId>mysql-connector-java</artifactId>
        <version>8.0.27</version>
    </dependency>
</dependencies>

```
## Persistindo dados
Para persistir dados na tabela pessoa, basta descomentar as linhas correspondentes no método main da classe Programa. As linhas comentadas realizam a busca e a exclusão de um registro na tabela.
```java
public class Programa {

    public static void main(String[] args) {

        // Criação de novos registros
        Pessoa p1 = new Pessoa(null, "Carlos da Silva", "carlos@gmai.com");
        Pessoa p2 = new Pessoa(null, "Joaquim Torres", "joaquim@gmai.com");
        Pessoa p3 = new Pessoa(null, "Ana Maria", "ana@gmai.com");

        EntityManagerFactory emf = Persistence.createEntityManagerFactory("exemplo-jpa");
        EntityManager em = emf.createEntityManager();

        // Inserção de novos registros
        em.getTransaction().begin();
        em.persist(p1);
        em.persist(p2);
        em.persist(p3);
        em.getTransaction().commit();

        // Busca e exclusão de um registro
        // Pessoa p = em.find(Pessoa.class, 2);
        // em.getTransaction().begin();    
        // em.remove(p);
        // em.getTransaction().commit();

        System.out.println("Pronto!");
        em.close();
        emf.close();
    }
}

```
