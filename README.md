Sistema de Gestão de Posto de Combustível

Este repositório apresenta o modelo de banco de dados desenvolvido para um sistema de gerenciamento de um posto de combustível. O sistema contempla o controle de vendas, empregados, departamentos, combustíveis, abastecimentos, volumes e informações complementares como endereços, telefones e dependentes.

Estrutura do Banco de Dados

O modelo foi construído em MySQL e é composto pelas seguintes entidades:

EMPREGADO

Armazena os dados dos empregados do posto.

Atributos principais:

cpf_empregado (PK)

nome

sexo (ENUM 'M', 'F')

salario

DEPARTAMENTO_idDEPARTAMENTO (FK – obrigatório)

ENDEREÇO_idENDEREÇO (FK – opcional)

Relacionamentos:

Cada empregado pertence a um departamento.

Pode possuir telefone(s).

Pode ter dependentes.

Pode realizar vendas.

DEPARTAMENTO

Guarda informações sobre os departamentos existentes no posto.

Atributos:

idDEPARTAMENTO (PK)

nome

email

descricao

local

cpf_gerente (FK — opcional)

Relacionamentos:

Um departamento pode ter vários empregados.

ENDEREÇO

Registra os endereços associados aos empregados.

Atributos:

idENDEREÇO (PK)

cidade

bairro

rua

numero

complemento

cep

Relacionamentos:

Um endereço pode estar associado a um empregado.

TELEFONE

Armazena os telefones dos empregados.

Atributos:

idTELEFONE (PK)

numero

EMPREGADO_cpf_empregado (FK)

Relacionamentos:

Cada telefone pertence a um empregado.

DEPENDENTES

Contém os dependentes dos empregados.

Atributos:

CPF (PK)

nome

DataNasc

parentesco

EMPREGADO_cpf_empregado (FK)

Relacionamentos:

Cada dependente está vinculado a um empregado.

VENDAS

Registra as vendas realizadas no posto.

Atributos:

idVENDAS (PK)

data

valorTOTAL

EMPREGADO_cpf_empregado (FK – obrigatório)

BOMBCOMB_idBOMBCOMB (FK)

FORMAS_PAG_idFORMAS_PAG (FK)

ITENS_VENDA_idITENS_VENDA (FK)

Relacionamentos:

Cada venda é realizada por um empregado.

Pode incluir itens de venda.

Está vinculada a uma forma de pagamento.

Pode registrar o abastecimento realizado em uma bomba.

COMBUSTIVEL

Registra os combustíveis disponíveis para venda.

Atributos:

idItem_COMBUSTIVEL (PK)

nome

quantidade

valor

BOMBCOMB_idBOMBCOMB (FK)

Relacionamentos:

Um combustível pode aparecer em vários itens de venda.

Pode estar vinculado a uma bomba.

ITENS_VENDA

Representa os combustíveis que fazem parte de cada venda.

Atributos:

idITENS_VENDA (PK)

combustiveis (FK para COMBUSTIVEL)

Relacionamentos:

Cada item está ligado a uma venda.

Cada item referencia um tipo de combustível.

FORMAS_PAG

Armazena os métodos de pagamento aceitos.

Atributos:

idFORMAS_PAG (PK)

cartao

pix

especie

BOMBCOMB

Registra os abastecimentos realizados nas bombas de combustível.

Atributos:

idBOMBCOMB (PK)

DataHora_Abastecimento

Relacionamentos:

Pode estar associado a combustíveis.

Pode ser usado em uma venda.

Relaciona-se com os volumes registrados.

VOLUME

Controla o volume de combustível associado às bombas.

Atributos:

idVOLUME (PK)

BOMBCOMB_idBOMBCOMB (FK)
