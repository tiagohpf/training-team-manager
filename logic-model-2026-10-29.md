# Spiridon-Backoffice --- Modelo Lógico de Dados

**Versão:** 1.0\
**Estado:** Modelo conceptual e lógico acordado; ainda não aplicado ao
código.\
**Data:** 29/10/2026

## 1. Objetivo

Este documento regista o modelo de dados acordado para o
Spiridon-Backoffice: diagrama de classes, entidades, campos, relações,
cardinalidades e regras de integridade.

O documento descreve o modelo proposto. Não implica alterações à
aplicação nem à estrutura atual dos dados.

## 2. Diagrama de classes

``` mermaid
classDiagram
direction LR

class Grupo {
  +id
  +nome
  +cor
  +ativo
}

class Escalao {
  +id
  +nome
}

class Atleta {
  +id
  +nome
  +grupo_id
  +escalao_id
  +ativo
}

class PlanoTreino {
  +id
  +nome
  +tipo
  +grupo_id
  +atleta_id
  +data_criacao
  +conteudo_adicional
}

class FasePlano {
  +id
  +plano_id
  +nome
  +ordem
  +conteudo_livre
}

class Exercicio {
  +id
  +nome
  +alcunha
  +descricao
  +video_url
  +grupo_exercicio
}

class ExercicioPlano {
  +id
  +fase_id
  +exercicio_id
  +ordem
  +texto_personalizado
}

class Competicao {
  +id
  +nome
  +data
  +local
  +ambito
  +tipo
  +observacoes
}

class CompeticaoEscalao {
  +competicao_id
  +escalao_id
}

class AtribuicaoCompeticao {
  +id
  +competicao_id
  +escalao_id
  +grupo_id
  +atleta_id
}

Grupo "1" --> "0..*" Atleta : integra
Escalao "1" --> "0..*" Atleta : enquadra

Grupo "1" --> "0..*" PlanoTreino : planos de grupo
Atleta "1" --> "0..*" PlanoTreino : planos individuais

PlanoTreino "1" --> "1..*" FasePlano : contém
FasePlano "1" --> "0..*" ExercicioPlano : inclui
Exercicio "0..1" --> "0..*" ExercicioPlano : reutilizado em

Competicao "1" --> "0..*" CompeticaoEscalao : escalões elegíveis
Escalao "1" --> "0..*" CompeticaoEscalao : elegível em

Competicao "1" --> "0..*" AtribuicaoCompeticao : tem atribuições
Grupo "0..1" --> "0..*" AtribuicaoCompeticao : destinatário
Escalao "0..1" --> "0..*" AtribuicaoCompeticao : destinatário
Atleta "0..1" --> "0..*" AtribuicaoCompeticao : destinatário
```

**Nota:** o diagrama mostra as relações gerais. As regras abaixo
restringem as combinações permitidas, sobretudo em `PlanoTreino` e
`AtribuicaoCompeticao`.

## 3. Entidades e descrição dos campos

### 3.1. `Grupo`

Representa um grupo de treino. Um grupo pode incluir atletas de
diferentes escalões.

  ------------------------------------------------------------------------
  Campo            Tipo sugerido              Obrigatório Descrição
  ---------------- ---------------- --------------------- ----------------
  `id`             Identificador                      Sim Chave primária e
                                                          identificador
                                                          estável do
                                                          grupo.

  `nome`           Texto                              Sim Nome do grupo de
                                                          treino.

  `cor`            Texto/código de                    Não Cor associada ao
                   cor                                    grupo na
                                                          aplicação.

  `ativo`          Booleano                           Sim Indica se o
                                                          grupo está
                                                          ativo.
  ------------------------------------------------------------------------

### 3.2. `Escalao`

Representa o escalão competitivo de um atleta.

  ------------------------------------------------------------------------
  Campo            Tipo sugerido              Obrigatório Descrição
  ---------------- ---------------- --------------------- ----------------
  `id`             Identificador                      Sim Chave primária
                                                          do escalão.

  `nome`           Texto                              Sim Nome do escalão,
                                                          por exemplo
                                                          Sub-14, Sub-16,
                                                          Sub-18 ou
                                                          Veteranos.
  ------------------------------------------------------------------------

**Regra acordada:** os escalões estão sempre ativos; a entidade não tem
campo `ativo`.

### 3.3. `Atleta`

Representa um atleta. Cada atleta pertence a um único grupo e a um único
escalão no modelo atual.

  ------------------------------------------------------------------------
  Campo            Tipo sugerido              Obrigatório Descrição
  ---------------- ---------------- --------------------- ----------------
  `id`             Identificador                      Sim Chave primária e
                                                          identificador
                                                          estável do
                                                          atleta.

  `nome`           Texto                              Sim Nome do atleta.

  `grupo_id`       Identificador                      Sim Chave
                                                          estrangeira para
                                                          `Grupo`.

  `escalao_id`     Identificador                      Sim Chave
                                                          estrangeira para
                                                          `Escalao`.

  `ativo`          Booleano                           Sim Indica se o
                                                          atleta está
                                                          ativo.
  ------------------------------------------------------------------------

O histórico de escalões ou grupos por época não está incluído nesta
versão do modelo.

### 3.4. `PlanoTreino`

Representa um plano destinado a um grupo ou a um atleta individual. Os
planos individuais são independentes dos planos de grupo.

  ------------------------------------------------------------------------------
  Campo                  Tipo sugerido              Obrigatório Descrição
  ---------------------- ---------------- --------------------- ----------------
  `id`                   Identificador                      Sim Chave primária
                                                                do plano.

  `nome`                 Texto                              Sim Nome ou título
                                                                do plano.

  `tipo`                 Enumeração                         Sim `GRUPO` ou
                                                                `INDIVIDUAL`.

  `grupo_id`             Identificador              Condicional Chave
                         anulável                               estrangeira para
                                                                `Grupo`,
                                                                preenchida nos
                                                                planos de grupo.

  `atleta_id`            Identificador              Condicional Chave
                         anulável                               estrangeira para
                                                                `Atleta`,
                                                                preenchida nos
                                                                planos
                                                                individuais.

  `data_criacao`         Data/hora                          Sim Data de criação
                                                                do plano.

  `conteudo_adicional`   Conforme                           Não Metadados
                         necessário                             adicionais do
                                                                plano, se
                                                                necessários.
  ------------------------------------------------------------------------------

**Regras:** - Se `tipo = GRUPO`, `grupo_id` é obrigatório e `atleta_id`
tem de estar vazio. - Se `tipo = INDIVIDUAL`, `atleta_id` é obrigatório
e `grupo_id` tem de estar vazio. - Um plano individual não herda
alterações de um plano de grupo. - Um grupo ou atleta pode ter vários
planos ao longo do tempo.

### 3.5. `FasePlano`

Representa uma fase dentro de um plano, como Aquecimento, Parte
Principal ou Retorno à Calma.

  --------------------------------------------------------------------------
  Campo              Tipo sugerido              Obrigatório Descrição
  ------------------ ---------------- --------------------- ----------------
  `id`               Identificador                      Sim Chave primária
                                                            da fase.

  `plano_id`         Identificador                      Sim Chave
                                                            estrangeira para
                                                            `PlanoTreino`.

  `nome`             Texto                              Sim Nome da fase.

  `ordem`            Número inteiro                     Sim Posição da fase
                                                            no plano.

  `conteudo_livre`   Texto                              Não Notas ou
                                                            instruções
                                                            livres que não
                                                            sejam exercícios
                                                            estruturados.
  --------------------------------------------------------------------------

Um plano contém uma ou mais fases, pela ordem definida pelo treinador.

### 3.6. `Exercicio`

Representa o registo original de um exercício na biblioteca do Dossiê de
Exercícios.

  ---------------------------------------------------------------------------
  Campo               Tipo sugerido              Obrigatório Descrição
  ------------------- ---------------- --------------------- ----------------
  `id`                Identificador                      Sim Chave primária
                                                             do exercício.

  `nome`              Texto                              Sim Nome do
                                                             exercício.

  `alcunha`           Texto                              Não Nome alternativo
                                                             ou alcunha.

  `descricao`         Texto                              Não Descrição do
                                                             exercício.

  `video_url`         URL/texto                          Não Ligação para
                                                             vídeo
                                                             demonstrativo.

  `grupo_exercicio`   Texto ou                           Não Categoria do
                      identificador                          exercício, por
                                                             exemplo Core ou
                                                             Barreiras.
  ---------------------------------------------------------------------------

Um exercício pode ser reutilizado em várias fases e planos.

### 3.7. `ExercicioPlano`

Entidade de associação que regista a utilização de um exercício numa
fase de um plano. Permite definir a ordem e guardar texto específico
para aquele plano.

  -------------------------------------------------------------------------------
  Campo                   Tipo sugerido              Obrigatório Descrição
  ----------------------- ---------------- --------------------- ----------------
  `id`                    Identificador                      Sim Chave primária
                                                                 do registo de
                                                                 exercício no
                                                                 plano.

  `fase_id`               Identificador                      Sim Chave
                                                                 estrangeira para
                                                                 `FasePlano`.

  `exercicio_id`          Identificador                      Não Chave
                          anulável                               estrangeira para
                                                                 `Exercicio`;
                                                                 vazio para texto
                                                                 livre.

  `ordem`                 Número inteiro                     Sim Posição do
                                                                 exercício ou
                                                                 texto dentro da
                                                                 fase.

  `texto_personalizado`   Texto                              Não Texto usado no
                                                                 plano, incluindo
                                                                 instruções ou
                                                                 adaptações
                                                                 específicas.
  -------------------------------------------------------------------------------

**Regra de independência:** ao inserir um exercício do Dossiê num plano,
o plano mantém a sua própria versão do texto utilizado. Alterações
posteriores ao exercício original não modificam silenciosamente os
planos existentes.

`exercicio_id` é anulável para permitir texto livre que não corresponda
a um exercício da biblioteca.

### 3.8. `Competicao`

Representa o evento desportivo, registado uma única vez.

  ------------------------------------------------------------------------
  Campo            Tipo sugerido              Obrigatório Descrição
  ---------------- ---------------- --------------------- ----------------
  `id`             Identificador                      Sim Chave primária
                                                          da competição.

  `nome`           Texto                              Sim Nome da
                                                          competição.

  `data`           Data ou                            Sim Data da
                   data/hora                              competição.

  `local`          Texto                              Não Local onde
                                                          decorre a prova.

  `ambito`         Texto ou                           Não Âmbito, por
                   enumeração                             exemplo
                                                          Regional, Zona
                                                          Norte ou
                                                          Nacional.

  `tipo`           Texto ou                           Não Tipo, por
                   enumeração                             exemplo Estrada,
                                                          Corta-Mato ou
                                                          Pista Curta.

  `observacoes`    Texto                              Não Informação
                                                          complementar.
  ------------------------------------------------------------------------

### 3.9. `CompeticaoEscalao`

Entidade de associação que define os escalões elegíveis para uma
competição. É independente das atribuições internas feitas pelo clube.

  -------------------------------------------------------------------------
  Campo             Tipo sugerido              Obrigatório Descrição
  ----------------- ---------------- --------------------- ----------------
  `competicao_id`   Identificador                      Sim Chave
                                                           estrangeira para
                                                           `Competicao`.

  `escalao_id`      Identificador                      Sim Chave
                                                           estrangeira para
                                                           `Escalao`.
  -------------------------------------------------------------------------

A chave primária composta (`competicao_id`, `escalao_id`) impede que o
mesmo escalão seja registado mais do que uma vez para a mesma
competição.

### 3.10. `AtribuicaoCompeticao`

Define a quem se destina uma competição dentro do clube: um escalão
completo, um grupo ou um atleta individual.

  -------------------------------------------------------------------------
  Campo             Tipo sugerido              Obrigatório Descrição
  ----------------- ---------------- --------------------- ----------------
  `id`              Identificador                      Sim Chave primária
                                                           da atribuição.

  `competicao_id`   Identificador                      Sim Chave
                                                           estrangeira para
                                                           `Competicao`.

  `escalao_id`      Identificador              Condicional Chave
                    anulável                               estrangeira para
                                                           `Escalao`, se a
                                                           atribuição for
                                                           por escalão.

  `grupo_id`        Identificador              Condicional Chave
                    anulável                               estrangeira para
                                                           `Grupo`, se a
                                                           atribuição for
                                                           por grupo.

  `atleta_id`       Identificador              Condicional Chave
                    anulável                               estrangeira para
                                                           `Atleta`, se a
                                                           atribuição for
                                                           individual.
  -------------------------------------------------------------------------

**Regra obrigatória:** exatamente um dos campos `escalao_id`, `grupo_id`
ou `atleta_id` deve estar preenchido por atribuição.

A mesma competição pode ter várias atribuições, incluindo modalidades
diferentes. A lista final de atletas deve eliminar duplicados quando um
atleta estiver abrangido por mais do que uma atribuição.

## 4. Relações e cardinalidades

  ------------------------------------------------------------------------
  Relação                  Cardinalidade           Significado
  ------------------------ ----------------------- -----------------------
  `Grupo` → `Atleta`       1:N                     Um grupo pode ter
                                                   vários atletas; cada
                                                   atleta pertence a um
                                                   grupo.

  `Escalao` → `Atleta`     1:N                     Um escalão pode ter
                                                   vários atletas; cada
                                                   atleta tem um escalão.

  `Grupo` → `PlanoTreino`  1:N                     Um grupo pode ter
                                                   vários planos de grupo.

  `Atleta` → `PlanoTreino` 1:N                     Um atleta pode ter
                                                   vários planos
                                                   individuais.

  `PlanoTreino` →          1:N                     Um plano tem uma ou
  `FasePlano`                                      mais fases.

  `FasePlano` →            1:N                     Uma fase pode conter
  `ExercicioPlano`                                 vários exercícios ou
                                                   entradas de texto
                                                   livre.

  `Exercicio` →            1:N                     Um exercício do Dossiê
  `ExercicioPlano`                                 pode ser reutilizado em
                                                   vários planos.

  `Competicao` ↔ `Escalao` N:M                     Uma competição pode
                                                   aceitar vários escalões
                                                   e um escalão pode
                                                   participar em várias
                                                   competições.

  `Competicao` →           1:N                     Uma competição pode ter
  `AtribuicaoCompeticao`                           várias atribuições
                                                   dentro do clube.

  `AtribuicaoCompeticao` → Um de três              Cada atribuição é
  destinatário                                     dirigida a um escalão,
                                                   grupo ou atleta.
  ------------------------------------------------------------------------

## 5. Regras de integridade transversais

1.  **Integridade referencial:** não podem existir referências a grupos,
    atletas, escalões, planos ou competições inexistentes.
2.  **Desativação em vez de eliminação:** grupos e atletas podem ser
    desativados sem apagar automaticamente o histórico.
3.  **Escalões sempre ativos:** a entidade `Escalao` não tem campo de
    estado ativo.
4.  **Destinatário único do plano:** cada plano pertence a um grupo ou a
    um atleta, nunca a ambos.
5.  **Planos individuais independentes:** não existe dependência de um
    plano de grupo.
6.  **Exercícios reutilizáveis:** o Dossiê é a biblioteca original; o
    plano guarda o texto usado e as adaptações específicas.
7.  **Sem duplicações de elegibilidade:** o par competição/escalão é
    único em `CompeticaoEscalao`.
8.  **Um destinatário por atribuição:** cada `AtribuicaoCompeticao`
    aponta para um escalão, um grupo ou um atleta, exatamente.
9.  **Destinatários deduplicados:** a lista de convocados apresenta cada
    atleta apenas uma vez por competição.

## 6. Decisões adiadas

Os seguintes temas ficam fora do modelo atual, podendo ser acrescentados
quando houver necessidade:

-   **Épocas desportivas:** histórico de grupos e escalões de cada
    atleta por época.
-   **Histórico de competições:** registo de alterações de datas, locais
    ou outros dados.
-   **Detalhe estruturado dos exercícios:** séries, repetições, duração,
    distância e recuperação como campos próprios, em vez de apenas
    texto.
-   **Cobertura de planos por escalão:** decidir se basta o escalão
    estar abrangido pelos planos dos grupos que incluem os seus atletas
    ou se será exigido um plano diretamente associado ao escalão.

## 7. Princípio de implementação

Este documento é a referência do modelo lógico acordado. A implementação
deverá preservar as regras e relações descritas, sem exigir alterações
imediatas à página atual.

Antes de implementar numa base de dados ou modificar a estrutura de
armazenamento local, será necessário comparar este modelo com os dados e
formatos existentes, de modo a planear uma migração segura.
