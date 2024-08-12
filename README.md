# DEVSuperior-BEE-URI-2611-join-simples
# <a href="https://imgbb.com/"><img src="https://i.ibb.co/51bfmLv/image-2024-07-01-T11-45-10-371-Z.png" alt="image-2024-07-01-T11-45-10-371-Z" border="0" width="300"></a> Java Spring Professional - BEE/URI 2611

#### Desenvolvido na linguagem Java por:
- [Marcos Shirafuchi](https://github.com/marcosfshirafuchi)
## Formação Desenvolvedor Moderno Módulo: Back end
<b>Capítulo: JPA, consultas SQL e JPQL</b><br><br>
<b>Aula: URI 2611 - Elaborando a consulta</b>

## Exercício: BEE/URI 2611

Exercício de SQL da plataforma do BEE: 2611 <br><br>
[https://judge.beecrowd.com/pt/problems/view/2611](https://judge.beecrowd.com/pt/problems/view/2611)<br>

<p align ="center"><b>Filmes de Ação</b></p>
Uma Vídeo locadora contratou seus serviços para catalogar os filmes dela. Eles precisam que você selecione o código e o nome dos filmes cuja descrição do gênero seja 'Action'.<br><br>


## Esquema

###  customer    


<table>
  <thead>
    <tr align="center">
      <th>customers</th>
       <th>customers</th>
    </tr>
    <tr align="left">
      <th>Coluna</th>
      <th>Tipo</th>
    </tr>
  </thead>
  <tbody align="left">
    <tr>
      <td>id (PK)
      </td>
      <td>numeric</td>
    </tr>
    <tr>
      <td>name</td>
      <td>varchar</td>
    </tr>
    <tr>
      <td>street</td>
      <td>	varchar</td>   
    </tr>
    <tr>
      <td>city</td>
      <td>	varchar</td>   
    </tr>
    <tr>
      <td>state</td>
      <td>char</td>   
    </tr>
    <tr>
      <td>credit_limit</td>
      <td>number</td>   
    </tr>
  </tbody>
  <tfoot></tfoot>
</table>


## Tabelas

### customers
| id |             name           |            street         |      city      | 	state | credit_limit  |
| -- | -------------------------- | ------------------------- | -------------- | ------ | ------------- |
| 1  |    Pedro Augusto da Rocha  | Rua Pedro Carlos Hoffman  | Porto Alegre   |   RS   |     700,00    |
| 2  |      Antonio Carlos Mamel  | 	   Av. Pinheiros        | Belo Horizonte |   MG   |    3500,50    |
| 3  |        Luiza Augusta Mhor  |     Rua Salto Grande      | Niteroi        |   RJ   |    4000,00    |
| 4  |          Jane Ester        |     Av 7 de setembro      | Erechim        |   RS   |     800,00    |
| 5  | Marcos Antônio dos Santos  |     Av Farrapos           | Porto Alegre   |   RS   |    4250,25    |


##  Exemplo de Saída  

| name                      |
| ------------------------- |
| Pedro Augusto da Rocha    |
| Jane Ester                | 
| Marcos Antônio dos Santos | 

## Principais Tecnologias

- <img width="50px" src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/java/java-original-wordmark.svg" title = "Java" /> Java 21 : Utilizaremos a versão LTS mais recente do Java para tirar vantagem das últimas inovações que essa linguagem robusta e amplamente utilizada oferece;
- <img width="50px" src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/spring/spring-original-wordmark.svg" title = "Spring boot"/> Spring Boot 3 : Trabalharemos com a mais nova versão do Spring Boot, que maximiza a produtividade do desenvolvedor por meio de sua poderosa premissa de autoconfiguração;
- <img width="50px" src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/spring/spring-original-wordmark.svg" title = "Spring Data JPA"/>  Spring Data JPA: Exploraremos como essa ferramenta pode simplificar nossa camada de acesso aos dados, facilitando a integração com bancos de dados SQL;
- <img width="50px" src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/postgresql/postgresql-original-wordmark.svg" title = "PostgreSQL"/> PostgreSQL: Banco de dados SQL .

### Código SQL do URI/BEE 2602

```
--- URI Online Judge SQL
--- Copyright URI Online Judge
--- www.urionlinejudge.com.br
--- Problem 2602

CREATE TABLE customers (
  id NUMERIC PRIMARY KEY,
  name CHARACTER VARYING (255),
  street CHARACTER VARYING (255),
  city CHARACTER VARYING (255),
  state CHAR (2),
  credit_limit NUMERIC
);

INSERT INTO customers (id, name, street, city, state, credit_limit)
VALUES 
  (1,	'Pedro Augusto da Rocha',	'Rua Pedro Carlos Hoffman',	'Porto Alegre',	'RS',	700.00),
  (2,	'Antonio Carlos Mamel',	'Av. Pinheiros', 'Belo Horizonte',	'MG',	3500.50),
  (3,	'Luiza Augusta Mhor',	'Rua Salto Grande',	'Niteroi',	'RJ',	4000.00),	
  (4,	'Jane Ester',	'Av 7 de setembro',	'Erechim',	'RS',	800.00),
  (5, 'Marcos Antônio dos Santos',	'Av Farrapos',	'Porto Alegre',	'RS',	4250.25);

  
  /*  Execute this query to drop the tables */
  -- DROP TABLE customers; --
```

## Resolução do exercício em SQL no URI/BEE 2602

```
SELECT name FROM customers WHERE state = 'RS';
```

## Código do SQL no Java

```
@Query(nativeQuery = true,value = "SELECT name FROM customers WHERE UPPER(state) = UPPER(:state)")
    List<CustomerMinProjection> search1(String state);
```

## Código do JPQL no Java

```
@Query("SELECT new com.devsuperior.uri2602.dto.CustomerMinDTO(obj.name)  FROM Customer obj WHERE UPPER(obj.state) = UPPER(:state)")
    List<CustomerMinDTO> search2(String state);
```
