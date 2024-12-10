#Sistema de Gestão de Geração de Energia - Banco de Dados

Objetivo do Banco de Dados
O banco de dados foi desenvolvido para gerenciar e armazenar informações relacionadas ao Sistema de Gestão de Geração de Energia. Ele contém informações sobre usinas de geração de energia, medidores de consumo, leituras de energia e manutenções realizadas nas usinas.

O objetivo principal é fornecer uma estrutura de dados eficiente para o controle e a visualização de consumos de energia, além de registrar manutenções e a capacidade de geração das usinas.

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Estrutura do Banco de Dados

Tabelas
O banco de dados é composto por quatro tabelas principais:

USINAS
Armazena informações sobre as usinas de geração de energia:

USINA_ID (PK): Identificador único da usina.
NOME: Nome da usina.
TIPO: Tipo de usina (ex: Solar, Eólica, Hidrelétrica).
CAPACIDADE_GERACAO: Capacidade de geração de energia (em MW).
LOCALIZACAO: Localização da usina.


MEDIDORES
Armazena informações sobre os medidores de consumo de energia:

MEDIDOR_ID (PK): Identificador único do medidor.
NUMERO_SERIE: Número de série do medidor.
USINA_ID (FK): Relacionamento com a tabela USINAS, indicando a qual usina o medidor está associado.
TIPO: Tipo do medidor (ex: Monofásico, Trifásico).


LEITURAS_ENERGIA
Armazena as leituras de consumo de energia feitas pelos medidores:

LEITURA_ID (PK): Identificador único da leitura.
MEDIDOR_ID (FK): Relacionamento com a tabela MEDIDORES, indicando a qual medidor a leitura pertence.
DATA_LEITURA: Data e hora da leitura.
CONSUMO: Quantidade de energia consumida (em kWh).


MANUTENCOES
Armazena informações sobre as manutenções realizadas nas usinas:

MANUTENCAO_ID (PK): Identificador único da manutenção.
USINA_ID (FK): Relacionamento com a tabela USINAS, indicando a qual usina a manutenção foi feita.
DATA_MANUTENCAO: Data da manutenção.
DESCRICAO: Descrição da manutenção.
CUSTO: Custo da manutenção (em R$).

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Relacionamentos entre as Tabelas

USINAS ↔ MEDIDORES: Cada usina pode ter vários medidores associados. O relacionamento é de 1 para N (uma usina pode ter múltiplos medidores).
MEDIDORES ↔ LEITURAS_ENERGIA: Cada medidor pode ter várias leituras de energia associadas. O relacionamento é de 1 para N (um medidor pode ter várias leituras).
USINAS ↔ MANUTENCOES: Cada usina pode ter várias manutenções registradas. O relacionamento é de 1 para N (uma usina pode ter várias manutenções).

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Como Executar os Scripts no Oracle

Utilizando o SQL*Plus
1 - Abra o SQL*Plus e conecte-se ao seu banco de dados Oracle com o seguinte comando:
  sqlplus username/password@hostname:port/SID

2 -Execute os scripts para criar as tabelas e popular os dados:
  Criação das tabelas: Execute o script de criação das tabelas (create_tables.sql).
  Inserção de dados: Execute o script de inserção de dados (insert_data.sql).
  No SQL*Plus, você pode executar o script utilizando o comando:
    @DDL/estrutura.sql
    @DML/dados.sql
    
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Utilizando o SQL Developer

1 - Abra o SQL Developer e conecte-se ao banco de dados Oracle.
2 - Abra uma nova janela de SQL Worksheet.
3 - Para executar os scripts de criação das tabelas e inserção de dados:
  Copie e cole o conteúdo do script de criação das tabelas no SQL Worksheet e clique em Run (ícone de "play").
  Copie e cole o script de inserção de dados e clique em Run novamente.
  
Comandos de Commit
Após a execução dos scripts de inserção, você deve confirmar as transações com o comando:
  COMMIT;
  
Isso irá persistir as alterações no banco de dados.
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Conclusão

Este banco de dados oferece uma estrutura robusta para o gerenciamento de dados relacionados à geração de energia e manutenção das usinas. Ele pode ser expandido conforme necessário, adicionando mais tabelas ou funcionalidades.

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
