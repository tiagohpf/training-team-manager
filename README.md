# Spiridon · Backoffice Desportivo

Uma ferramenta simples para **preparar planos de treino semanais** e exportá-los em **PDF** ou **imagem**, pronta a enviar aos atletas.

É um único ficheiro (`Spiridon___Backoffice_Desportivo.html`) que abre no navegador. **Não precisas de instalar nada, nem de criar conta, nem de ligação à internet.**

---

## O que podes fazer

- **Criar planos semanais** por grupo ou por atleta, com Aquecimento, Parte Principal e Retorno à Calma em cada dia.
- **Formatar o texto** com negrito, itálico, sublinhado e listas. Podes colar texto do Word ou do Google Docs e a formatação mantém-se.
- **Indicar ritmos** (por exemplo `4:40 - 4:50`) em cada fase do treino.
- **Escolher cores** para o cabeçalho e para os subtítulos. Cada grupo e cada atleta pode ter a sua cor por defeito.
- **Organizar grupos e atletas** (Sub-14, Sub-16, Fundistas, etc.).
- **Exportar o plano** em PDF ou em imagem (PNG).
- **Guardar cópias de segurança** e passar os dados de um computador para outro.

---

## Índice

1. [Primeiros passos (resumo)](#primeiros-passos-resumo)
2. [Como sacar com Git](#como-sacar-com-git)
3. [Como correr](#como-correr)
4. [Como usar](#como-usar)
5. [Guardar cópias e importar](#guardar-cópias-e-importar)
6. [Problemas frequentes](#problemas-frequentes)
7. [Alternativa: sacar como ZIP](#alternativa-sacar-como-zip)

---

## Primeiros passos (resumo)

1. Saca o projeto (com Git ou em ZIP, ver abaixo).
2. Abre o ficheiro `Spiridon___Backoffice_Desportivo.html` com um duplo clique.
3. Cria os teus grupos e atletas, depois o teu primeiro plano.
4. **De vez em quando, descarrega uma cópia de segurança** em *Dados e cópias*.

---

## Como sacar com Git

O Git permite sacar o projeto e **receber as atualizações** com um único comando. Só tens de o instalar uma vez.

### 1. Instalar o Git

**Windows**
1. Vai a <https://git-scm.com/download/win>. O download começa sozinho.
2. Abre o ficheiro descarregado e vai carregando em **Next** até ao fim (as opções por defeito servem).
3. No fim, procura **Git Bash** no menu Iniciar. É o terminal que vais usar.

**Mac**
1. Abre a aplicação **Terminal** (procura por "Terminal" no Spotlight).
2. Escreve o comando abaixo e carrega em Enter:
   ```bash
   git --version
   ```
3. Se o Mac perguntar se queres instalar as ferramentas de programador, aceita e espera que termine.

**Linux (Ubuntu / Debian)**
```bash
sudo apt install git
```

Para confirmar que ficou instalado, escreve no terminal:
```bash
git --version
```
Deve aparecer algo como `git version 2.xx.x`.

### 2. Sacar o projeto

1. Abre o terminal (Git Bash no Windows, Terminal no Mac).
2. Vai para a pasta onde queres guardar o projeto. Por exemplo, os Documentos:
   ```bash
   cd ~/Documents
   ```
3. Saca o projeto:
   ```bash
   git clone https://github.com/<UTILIZADOR>/<REPOSITORIO>.git
   ```
   > Troca `<UTILIZADOR>` e `<REPOSITORIO>` pelos valores do endereço deste repositório. Podes copiar o endereço completo no botão verde **Code** desta página.
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

## Como correr

1. Abre a pasta do projeto.
2. Faz **duplo clique** em `Spiridon___Backoffice_Desportivo.html`. Abre no navegador.
   - Se abrir noutro programa, clica com o botão direito no ficheiro, escolhe **Abrir com** e depois **Google Chrome** (ou Edge).

**Navegadores recomendados:** Google Chrome ou Microsoft Edge. A exportação em imagem pode não funcionar no Safari.

**Os teus dados ficam guardados no navegador e no computador onde estás a trabalhar.** Se abrires noutro computador ou noutro navegador, vais ver o backoffice vazio. Para passar os dados de um sítio para o outro, usa as cópias de segurança (ver abaixo).

---

## Como usar

### 1. Atletas e grupos
- Em **Atletas e grupos**, adiciona os grupos e os atletas.
- Podes escolher uma **cor por defeito** para cada grupo e para cada atleta. Um atleta sem cor própria usa a cor do grupo.
- Podes mudar o grupo de um atleta a qualquer momento na lista.

### 2. Criar um plano
- Em **Planos de treino**, carrega em **+ Novo plano**.
- Escolhe o **Grupo de Treino** e, se for para um atleta em particular, o **Atleta**. Com os dois em "Todos", o plano é para toda a gente.
- Indica a **segunda-feira** da semana.
- Escolhe as cores do cabeçalho e dos subtítulos, se quiseres mudar as sugeridas.
- Preenche os dias. Cada fase tem uma caixa de texto com formatação e um campo opcional para o **ritmo**.
- Carrega em **Guardar plano**.

### 3. Exportar
- **Ver / Exportar PDF** abre o plano pronto a imprimir ou a guardar como PDF.
- **Exportar imagem** descarrega o plano em PNG, bom para enviar por WhatsApp.
- Os planos já guardados também têm os botões **PDF** e **Imagem** na lista.

---

## Guardar cópias e importar

Os dados (planos, atletas, grupos e cores) ficam guardados **dentro do navegador**. Por isso, é importante fazer cópias de segurança:

- se limpares os dados de navegação, podes **perder tudo**;
- se mudares de computador ou de navegador, **os dados não vão contigo**.

### Guardar uma cópia
1. Abre **Dados e cópias** (menu à esquerda).
2. Carrega em **Descarregar cópia JSON**.
3. É descarregado um ficheiro com o nome `spiridon-backup-AAAA-MM-DD.json`. Guarda-o num sítio seguro (pasta no computador, Google Drive, e-mail para ti próprio...).

> Faz uma cópia sempre que fizeres alterações importantes, ou pelo menos uma vez por semana.

### Importar uma cópia
1. Abre **Dados e cópias**.
2. Carrega em **Importar cópia** e escolhe o ficheiro `.json` guardado.
3. Confirma a mensagem que aparece.

**Atenção:** importar **substitui todos os dados atuais** pelos da cópia.

### Passar os dados para outro computador
1. No computador antigo, descarrega a cópia JSON.
2. Envia o ficheiro para o computador novo (e-mail, pen, Drive).
3. No computador novo, abre o backoffice e importa a cópia.

### Exportar atletas por grupo
Em **Dados e cópias** há também o botão **Descarregar CSV**, que cria uma folha com cada atleta e o respetivo grupo. Abre diretamente no Excel.

### Privacidade
Os dados ficam só no teu computador e nunca são enviados para a internet. **Não publiques as cópias JSON ou CSV neste repositório**, porque contêm nomes de atletas.

---

## Problemas frequentes

**O PDF não abre quando carrego no botão.**
O navegador pode estar a bloquear janelas pop-up. Permite os pop-ups para este ficheiro e tenta de novo.

**A imagem não é descarregada.**
Usa o Chrome ou o Edge. No Safari, a exportação em imagem pode falhar. Como alternativa, usa o PDF.

**Abri o backoffice e os meus planos desapareceram.**
Muito provavelmente estás a usar outro navegador ou outro computador, ou limpaste os dados de navegação. Importa a tua última cópia de segurança em **Dados e cópias**.

**Atualizei o projeto e os meus dados sumiram.**
Os dados ficam ligados ao navegador e à localização do ficheiro. Se moveste o ficheiro ou o abriste de outra pasta, importa a tua cópia de segurança.

---

## Alternativa: sacar como ZIP

Se não quiseres usar o Git, é possível sacar tudo de uma só vez:

1. Na página principal deste repositório, carrega no botão verde **Code**.
2. Escolhe **Download ZIP**.
3. Abre a pasta de Transferências, clica com o botão direito no ficheiro ZIP e escolhe **Extrair tudo** (Windows) ou faz duplo clique (Mac).
4. Abre a pasta extraída e faz duplo clique em `Spiridon___Backoffice_Desportivo.html`.

Para receber uma versão nova, repete estes passos. **Antes de mudares de pasta, descarrega uma cópia de segurança** e importa-a depois na nova versão.
