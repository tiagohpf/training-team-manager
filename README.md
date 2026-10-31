# Training Team · Backoffice Desportivo
Uma ferramenta simples para os treinadores, sendo possível **convocar atletas para as competições** e **preparar planos de treino semanais**, exportando em **PDF** ou **imagem**, pronta para partilhar.

É um único ficheiro (`index.html`) que abre no navegador. **Não precisas de instalar nada, nem de criar conta.**

## Funcionalidades
- **Criar planos semanais** por grupo ou por atleta.
- **Calendário competitivo independente**, com âmbito, tipo, escalões permitidos, convocações por grupo e/ou por atleta, filtros em cascata por escalão, grupo e atleta, intervalo de datas e exportação organizada por mês para impressão/PDF.
- **Registar competições** com nome, data, local e observações, definindo separadamente os escalões elegíveis e os grupos/atletas convocados.
- **Registar treinos ou competições** em cada dia da semana e indicar livremente o tipo de treino.
- **Formatar o texto** com negrito, itálico, sublinhado, listas com marcadores e listas numeradas.
- **Usar a verificação ortográfica** do navegador no editor de texto.
- **Colar texto** do Word ou do Google Docs, mantendo a formatação compatível.
- **Indicar ritmos** (por exemplo `4:40 - 4:50`) nas fases do treino.
- **Escolher cores** para o cabeçalho e para os subtítulos dos planos. Cada grupo e cada atleta pode ter a sua cor por defeito.
- **Exportar calendários com cores personalizadas**, respeitando a cor definida para o grupo ou atleta; quando não existe uma cor própria, é usada a cor por defeito da aplicação.
- **Organizar grupos e atletas**, com género (Masculino, Feminino ou A definir) e filtros por escalão, grupo de treino e género na listagem de atletas.
- **Exportar o plano** em PDF ou em imagem (PNG).
- **Exportar e importar dados** para guardar o progresso.
---

## Índice

1. [Primeiros passos](#primeiros-passos)
2. [Como instalar e correr](#como-instalar-e-correr)
3. [Alternativa: download em ZIP](#alternativa-download-em-zip)
4. [Como sacar com Git](#como-sacar-com-git)
5. [Como usar](#como-usar)
6. [Calendário competitivo](#calendário-competitivo)
7. [Cópias de segurança e exportação de dados](#cópias-de-segurança-e-exportação-de-dados)
8. [Problemas frequentes](#problemas-frequentes)
9. [Sugestões e ideias](#sugestões-e-ideias)

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
3. Se abrir noutro programa, clica com o botão direito no ficheiro, escolhe **Abrir com** e seleciona **Google Chrome** ou **Microsoft Edge**.

**Navegadores recomendados:** Google Chrome ou Microsoft Edge. A exportação em imagem pode não funcionar no Safari.

**Os teus dados ficam guardados no navegador e no computador onde estás a trabalhar.** Se abrires a aplicação noutro computador ou navegador, os dados não aparecem automaticamente. Para os transferir, usa as opções de exportação e importação de dados.

---

## Alternativa: download em ZIP

Se não quiseres usar o Git, podes descarregar o projeto todo de uma só vez:

1. Na página principal deste repositório, carrega no botão verde **Code**.
2. Escolhe **Download ZIP**.
3. Abre a pasta de Transferências e extrai o ficheiro ZIP:
   - **Windows:** clica com o botão direito e escolhe **Extrair tudo**.
   - **Mac:** faz duplo clique no ZIP.
4. Abre a pasta extraída e faz duplo clique em `index.html`.

Para receber uma versão nova, repete estes passos. **Antes de mudares para uma nova pasta, exporta os teus dados** e importa-os depois na nova versão.

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

---

## Como usar

### 1. Atletas e Grupos

- Em **Atletas e grupos**, adiciona os grupos e os atletas. Podes registar vários atletas de uma só vez, partilhando o mesmo grupo e escalão; o género é definido individualmente na ficha de cada atleta ou no registo inicial.
- Podes escolher uma **cor por defeito** para cada grupo e para cada atleta. Um atleta sem cor própria usa a cor do grupo.
- A informação dos atletas é apresentada no formato **Escalão · Grupo de treino · Género**. Os registos anteriores à introdução do género ficam como **A definir** até serem atualizados.
- Na listagem, podes filtrar por escalão, grupo de treino e género. Por defeito, são apresentados todos os atletas numa área com altura limitada e deslocamento interno.

### 2. Criar um Plano

- Em **Planos de treino**, carrega em **+ Novo plano**.
- Define o destinatário do plano: **um grupo de treino ou um atleta individual**. Um plano é associado a um destes destinatários, não aos dois em simultâneo.
- Indica a **segunda-feira** da semana.
- Escolhe as cores do cabeçalho e dos subtítulos, se quiseres mudar as sugeridas.
- Para um treino, preenche as fases disponíveis e, se necessário, indica o ritmo. No campo **Tipo de treino**, escreve livremente a designação que pretendes, por exemplo, «Treino de Força».
- Para uma prova ou competição, marca o dia como **prova** e escreve o nome da competição.
- Carrega em **Guardar plano**.

### 3. Formatar o Texto

No editor podes usar negrito, itálico, sublinhado, listas com marcadores e listas numeradas. A verificação ortográfica depende do navegador e dos idiomas/dicionários disponíveis. Se não aparecerem sugestões, confirma as definições de idioma e de verificação ortográfica do navegador.

### 4. Exportar um Plano

- **Ver / Exportar PDF** abre o plano pronto a imprimir ou a guardar como PDF.
- **Exportar imagem** descarrega o plano em PNG, ideal para partilhar.
- Os planos já guardados também têm os botões **PDF** e **Imagem** na lista.

---

## Calendário Competitivo

A área *Calendário competitivo* é independente dos planos de treino e permite organizar provas ao longo de vários anos. A elegibilidade por escalão e a convocatória são conceitos separados: os escalões indicam quem pode participar; os grupos e atletas selecionados indicam quem o clube pretende convocar.

1. Clica em **Nova competição** e indica o nome e a data.
2. Escolhe o **âmbito**: Regional, Zona Norte, Zona Norte + Regional, Popular, Meeting, Nacional ou Internacional.
3. Escolhe o **tipo**: Ar Livre, Pista Curta, Corta-Mato, Estrada, Pavilhão ou Rua.
4. Indica o local e, se necessário, observações.
5. Define a **data de início** e a **data de fim**. Por defeito, ambas são iguais; se a competição durar vários dias, altera a data de fim. A data de fim não pode ser anterior à data de início.
6. Em **Escalões permitidos**, seleciona os escalões competitivos elegíveis para a prova. Esta definição indica quem pode participar, não quem foi convocado.
7. Define a convocatória selecionando um ou mais grupos completos e/ou atletas individuais. Podes, por exemplo, convocar todo um grupo e escolher apenas alguns atletas de outro grupo. A seleção individual pode abranger atletas de grupos e escalões diferentes.
8. Define as datas **De** e **Até** para consultar qualquer intervalo, incluindo épocas que atravessem vários anos. Os atalhos **Época** e **Ano civil** preenchem intervalos comuns.
9. Filtra por grupo ou atleta para consultar um calendário específico. Estes filtros aplicam-se à consulta do calendário competitivo; a secção **Próximas Competições** do Painel Geral apresenta as competições dos próximos 30 dias sem filtrar por escalão, grupo ou atleta convocado.
10. Clica em **Exportar calendário / PDF** para abrir uma versão organizada por mês, com as colunas Data, Competição, Âmbito, Local, Tipo e Escalões permitidos. A exportação respeita a cor definida para o grupo ou atleta; na ausência de cor personalizada, utiliza a cor predefinida da aplicação. Na janela aberta, escolhe imprimir ou guardar como PDF.

As competições ficam guardadas no navegador e são incluídas nas cópias de segurança. Os registos antigos continuam a funcionar; os campos novos assumem valores por defeito quando não estavam definidos.

---

## Cópias de segurança e exportação de dados

Os planos, atletas, grupos, competições e cores ficam guardados **no navegador**. Por isso, é importante exportar os dados regularmente:

- se limpares os dados de navegação, podes **perder os registos**;
- se mudares de computador ou navegador, **os dados não são transferidos automaticamente**.

### Exportar dados

1. Abre **Importar e Exportar Dados** no menu.
2. Na secção **Cópia de Segurança**, carrega em **Exportar Dados**.
3. Guarda o ficheiro JSON num local seguro, como uma pasta no computador ou um serviço de armazenamento pessoal.

Faz uma cópia sempre que fizeres alterações importantes, ou pelo menos uma vez por semana.

### Importar dados

1. Abre **Importar e Exportar Dados**.
2. Na secção **Cópia de Segurança**, carrega em **Importar Dados** e escolhe o ficheiro JSON.
3. Confirma a mensagem apresentada.

**Atenção:** a importação substitui todos os dados atuais pelos dados do ficheiro escolhido.

### Transferir os dados para outro computador

1. No computador antigo, exporta os dados.
2. Transfere o ficheiro para o computador novo (por e-mail, pen ou armazenamento pessoal).
3. No computador novo, abre o backoffice e importa o ficheiro.

### Exportar atletas e grupos

Em **Importar e Exportar Dados**, a opção **Exportar Atletas e Grupos** descarrega um ficheiro CSV com os atletas e os respetivos grupos. O ficheiro pode ser aberto no Excel.

### Privacidade

Os dados ficam guardados localmente no navegador e não são enviados automaticamente para a internet. **Não publiques ficheiros JSON ou CSV neste repositório**, porque podem conter nomes de atletas.

---

## Problemas frequentes

**O PDF não abre quando carrego no botão.**  
O navegador pode estar a bloquear janelas pop-up. Permite os pop-ups para este ficheiro e tenta novamente.

**A imagem não é descarregada.**  
Usa o Chrome ou o Edge. No Safari, a exportação em imagem pode falhar. Como alternativa, usa o PDF.

**Abri o backoffice e os meus planos desapareceram.**  
Podes estar a usar outro navegador ou computador, ou ter limpado os dados de navegação. Importa a tua última cópia de segurança.

**Atualizei o projeto e os meus dados desapareceram.**  
Os dados ficam associados ao navegador. Se abriste a aplicação noutro navegador ou computador, importa a cópia de segurança. Se moveste o ficheiro para outra pasta e os dados deixaram de aparecer, importa também a cópia de segurança.

---

## Sugestões e ideias

Usas esta ferramenta e tens uma ideia para a melhorar? Adoramos ouvir!

- **Tens uma sugestão?** Partilha-a em [Discussions › Ideas](https://github.com/<UTILIZADOR>/<REPOSITORIO>/discussions/new?category=ideas).
- **Encontraste um erro?** Abre um [Issue](https://github.com/<UTILIZADOR>/<REPOSITORIO>/issues/new) e explica o que aconteceu e em que navegador.

Quanto mais detalhe, melhor. Por exemplo: “Gostava de poder duplicar um plano da semana anterior”.
