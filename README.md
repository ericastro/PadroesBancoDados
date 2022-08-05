### Padrões Banco Dados
Padronizações de nomenclatura de Tabelas e Parâmetros

---

# Convenção de Escrita
* O Banco de Dados como o nome das tabelas e nome de campos devera seguir a convenção snake_case
* Poderá SER utilizado a escrita em UPPERCASE ou LOWERCASE , porém uma vez adotada, deverá ser utilizada sem variação.
* [Snake case](https://en.wikipedia.org/wiki/Snake_case).
* [Screaming snake case](https://www.alura.com.br/artigos/convencoes-nomenclatura-camel-pascal-kebab-snake-case?gclid=Cj0KCQjwuaiXBhCCARIsAKZLt3mpms-3WDGb4LEQXyS-QTErOkyEzIvv67ZgBmoKlfocmNnj66W5ze0aAo-JEALw_wcB)

# Nome de Tabelas
* Deverá estar no singular, e precedido da sigla TB.
* Ex.: TB_CLIENTE

# Campos ID
* Deverá ser utilizado o prefixo ID como Primary Key da Tabela, e os IDs referentes a Foregns Keys deverão utilizar o prefixo ID seguido do nome da Tabela a ser vinculada, ex.: ID_ENDERECO

# CONSTRANT ( RESTRIÇÕES )
* Primary, Foreign Keys deverão ser declaradas separadamentes no final do comando da criação da tabela com a utilização de nomes para suas devidas especifições
* As Primary Keys deverão utilizar a sigla PK seguidas do nome da tabela.
* As Foreign Keys deverão utilizar a sigla FK seguida do nome da tabela que esta sendo criada e do campo ao qual esta sendo relacionado como chave estrangeira.
* As Unique Keys deverão utilizar a sigla UQ seguidas do nome da tabela que esta sendo criada.

```
CREATE TB_CLIENTE ( 
                      ID            INT           NOT NULL  IDENTITY(1,1),
                      NOME          VARCHAR(100)  NOT NULL,
                      EMAIL         VARCHAR(100)  NOT NULL,
                      ID_ENDERECO   INT           NOT NULL,
                      
                      CONSTRAINT    PK_TB_CLIENTE                PRIMARY KEY(ID),
                      CONSTRAINT    FK_TB_CLIENTE_ID_ENDERECO    FOREIGN KEY(ID_ENDERECO)  REFERENCES TB_ENDERECO(ID)
                      CONSTRAINT    UQ_TB_CANAL_CODIGO           UNIQUE(CODIGO),
                  );
                  
CREATE TB_ENDERECO ( 
                      ID            INT           NOT NULL      IDENTITY(1,1),
                      LOGRADOURO    VARCHAR(100)  NOT NULL,
                      NUMERO        SMALLINT      NOT NULL,
                      
                      CONSTRAINT    PK_TB_ENDERECO               PRIMARY KEY(ID)
                  );                  
                  
```

# Campos TIMESTAMP
* deverão ser todos do tipo DATETIME e gerenciados pela aplicação para evitar problemas com a diferença horários entre serviços distribuidos.

* Exemplo :

```
    DATA_CRIACAO                DATETIME            NOT NULL,
    DATA_ATUALIZACAO            DATETIME                NULL,
```    

