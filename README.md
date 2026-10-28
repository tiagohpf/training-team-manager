# Training Team · Backoffice Desportivo

Uma ferramenta simples para **preparar planos de treino semanais** e exportá-los em **PDF** ou **imagem**, pronta para partilhar.

É um único ficheiro (`index.html`) que abre no navegador. **Não precisas de instalar nada, nem de criar conta, nem de ligação à internet.**

---

## Funcionalidades

- **Criar planos semanais** por grupo ou por atleta.
- **Registar treinos ou competições** em cada dia da semana.
- **Formatar o texto** com negrito, itálico, sublinhado, listas com marcadores e listas numeradas.
- **Indicar ritmos** (por exemplo `4:40 - 4:50`) nas fases do treino.
- **Escolher cores** para o cabeçalho e para os subtítulos dos planos de treino. Cada grupo e cada atleta pode ter a sua cor por defeito.
- **Organizar grupos e atletas**.
- **Guardar exercícios** no Dossiê de Exercícios, organizados por grupos (Barreiras, Core, PFG, Técnica de Corrida, etc), e inseri-los nos planos com um clique.
- **Exportar o plano** em PDF ou em imagem (PNG).
- **Exportar e importar dados** para guardar o progresso.

---

## Índice

1. [Primeiros passos](#primeiros-passos)
2. [Como instalar e correr](#como-instalar-e-correr)
3. [Como sacar com Git](#como-sacar-com-git)
4. [Alternativa: download em ZIP](#alternativa-download-em-zip)
5. [Como usar](#como-usar)
6. [Cópias de segurança, importação e exportação de dados](#cópias-de-segurança-importação-e-exportação-de-dados)
7. [Problemas frequentes](#problemas-frequentes)
8. [Sugestões e ideias](#sugestões-e-ideias)

---

## Primeiros passos

1. Obtém os ficheiros do projeto, através do ZIP ou do Git (ver abaixo).
2. Abre o ficheiro `index.html` com um duplo clique.
3. Cria os teus grupos e atletas e prepara o teu primeiro plano.
4. **Faz cópias de segurança regularmente** em *Importar e Exportar Dados*.

---

## Como instalar e correr

A aplicação não precisa de instalação: basta abrir o ficheiro HTML num navegador.

1. Abre a pasta do projeto.
2. Faz **duplo clique** em `index.html`.


**Navegadores recomendados:** Google Chrome ou Microsoft Edge. A exportação em imagem pode não funcionar no Safari.

**Os teus dados ficam guardados no navegador e no computador onde estás a trabalhar.** Se abrires a aplicação noutro computador ou navegador, os dados não aparecem automaticamente. Para os transferir, usa as opções de exportação e importação de dados.

---

## Como sacar com Git

O Git permite descarregar o projeto e **receber atualizações** com um único comando. Só tens de o instalar uma vez.

### 1. Instalar o Git

**Windows**
1. Vai a <https://git-scm.com/download/win>. O download começa automaticamente.
2. Abre o ficheiro descarregado e carrega em **Next** até ao fim. As opções por defeito servem.
3. No menu Iniciar, procura **Git Bash**. É o terminal que vais usar.

**Mac**
1. Abre a aplicação **Terminal** (procura por “Terminal” no Spotlight).
2. Escreve o comando abaixo e carrega em Enter:
   ```bash
   git --version
   ```
3. Se o Mac perguntar se queres instalar as ferramentas de programador, aceita e espera que termine.

**Linux (Ubuntu / Debian)**
```bash
sudo apt install git
```

Para confirmar que ficou instalado, escreve:
```bash
git --version
```

Deve aparecer algo como `git version 2.xx.x`.

### 2. Descarregar o projeto

1. Abre o terminal (Git Bash no Windows ou Terminal no Mac).
2. Vai para a pasta onde queres guardar o projeto. Por exemplo, Documentos:
   ```bash
   cd ~/Documents
   ```
3. Descarrega o projeto:
   ```bash
   git clone https://github.com/<UTILIZADOR>/<REPOSITORIO>.git
   ```
   Troca `<UTILIZADOR>` e `<REPOSITORIO>` pelos valores do endereço deste repositório. Podes copiar o endereço completo no botão verde **Code** desta página.
4. Entra na pasta criada:
   ```bash
   cd <REPOSITORIO>
   ```

### 3. Receber atualizações

Quando houver uma versão nova, abre o terminal dentro da pasta do projeto e escreve:

```bash
git pull
```

Os teus planos e atletas **não são afetados**, porque ficam guardados no navegador e não na pasta do projeto.


## Alternativa: download em ZIP

Se não quiseres usar o Git, podes descarregar o projeto todo de uma só vez:

1. Na página principal deste repositório, carrega no botão verde **Code**.
2. Escolhe **Download ZIP**.
3. Abre a pasta de Transferências e extrai o ficheiro ZIP:
   - **Windows:** clica com o botão direito e escolhe **Extrair tudo**.
   - **Mac:** faz duplo clique no ZIP.
4. Abre a pasta extraída e faz duplo clique em `index.html`.

Para receber uma versão nova, repete estes passos. **Antes de mudares para uma nova pasta, exporta os teus dados** e importa-os depois na nova versão.

## Como usar

### 1. Atletas e Grupos

- Em **Atletas e Grupos**, adiciona os grupos e os atletas.
- Podes escolher uma **cor por defeito** para cada grupo e para cada atleta. Um atleta sem cor própria usa a cor do grupo.
- Podes mudar o grupo de um atleta a qualquer momento na lista.

### 2. Dossiê de Exercícios

Para os exercícios que se repetem (técnica, ginásio, reforço muscular, preparação física geral), usa o dossiê:

- Em **Dossiê de Exercícios**, cria **Grupos de Exercícios** (por exemplo, *Barreiras* ou *Core*) e vai acrescentando exercícios a cada um.
- Cada exercício tem **nome**, **alcunha**, **descrição**, **link** (por exemplo, um vídeo) e **grupo**. Só o nome é obrigatório.
- Podes editar ou remover um exercício a qualquer momento. Os planos já criados **não são alterados**.

### 3. Criar um plano

- Em **Planos de treino**, carrega em **+ Novo plano**.
- Escolhe o **Grupo de Treino** e, se for para um atleta em particular, o **Atleta**. Com ambos em “Todos”, o plano é para toda a gente.
- Indica a **segunda-feira** da semana.
- Escolhe as cores do cabeçalho e dos subtítulos, se quiseres mudar as sugeridas.
- Para um treino, preenche as fases disponíveis e, se necessário, indica o ritmo.
- Para usar um exercício da biblioteca, carrega em **+ Exercício** no editor da fase, escolhe um ou vários e carrega em **Inserir**. O exercício entra como texto normal, no sítio do cursor, e podes continuar a escrever e a formatar à vontade. O formato é `Nome: descrição [Vídeo]`, onde “Vídeo” é uma ligação clicável. Se não houver descrição fica `Nome: [Vídeo]`, se não houver vídeo fica `Nome: descrição` e, se não houver nenhum dos dois, fica só `Nome`. Podes desligar a descrição ou o vídeo na janela de inserção.
- Para uma prova ou competição, marca o dia como **prova** e escreve o nome da competição.
- Carrega em **Guardar plano**.

### 4. Formatar o texto

No editor podes usar negrito, itálico, sublinhado, listas com marcadores e listas numeradas, ao teu gosto.

### 5. Exportar um plano

- **Ver / Exportar PDF** abre o plano pronto a imprimir ou a guardar como PDF.
- **Exportar imagem** descarrega o plano em PNG, ideal para partilhar.
- Os planos já guardados também têm os botões **PDF** e **Imagem** na lista.

---

## Cópias de segurança, importação e exportação de dados

Os planos, atletas, grupos, exercícios e cores ficam guardados **no navegador**. Por isso, é importante exportar os dados regularmente:

- se limpares os dados de navegação, podes **perder os dados**;
- se mudares de computador ou navegador, **os dados não são transferidos automaticamente**.

### Exportar Dados

1. Abre **Importar e Exportar Dados** no menu.
2. Na secção **Cópia de Segurança**, carrega em **Exportar Dados**.
3. Guarda o ficheiro JSON num local seguro, como uma pasta no computador ou um serviço de armazenamento pessoal.

Faz uma cópia sempre que fizeres alterações importantes, ou pelo menos uma vez por semana.

### Importar Dados

1. Abre **Importar e Exportar Dados**.
2. Na secção **Cópia de Segurança**, carrega em **Importar Dados** e escolhe o ficheiro JSON.
3. Confirma a mensagem apresentada.

**Atenção:** a importação substitui todos os dados atuais pelos dados do ficheiro escolhido.

### Transferir os dados para outro computador

1. No computador antigo, exporta os dados.
2. Transfere o ficheiro para o computador novo (por e-mail, pen ou armazenamento pessoal).
3. No computador novo, abre o backoffice e importa o ficheiro.

### Exportar Atletas e Grupos

Em **Importar e Exportar Dados**, a opção **Exportar Atletas e Grupos** descarrega um ficheiro CSV com os atletas e os respetivos grupos. O ficheiro pode ser aberto no Excel.

### Privacidade

Os dados ficam guardados localmente no navegador e não são enviados automaticamente para a internet. **Não publiques ficheiros JSON ou CSV neste repositório**, porque podem conter nomes de atletas.

---

## Sugestões e Ideias

Usas esta ferramenta e tens uma ideia para a melhorar? Adoramos ouvir!

- **Tens uma sugestão?** Partilha-a em [Discussions › Ideas](https://github.com/<UTILIZADOR>/<REPOSITORIO>/discussions/new?category=ideas).
- **Encontraste um erro?** Abre um [Issue](https://github.com/<UTILIZADOR>/<REPOSITORIO>/issues/new) e explica o que aconteceu e em que navegador.

Quanto mais detalhe, melhor. Por exemplo: “Gostava de poder duplicar um plano da semana anterior”.
