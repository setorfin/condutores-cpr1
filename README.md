# Condutores CPR-1 – aplicativo no GitHub

Aplicativo do Setor de Apoio Administrativo – CPR-1. Funciona no Windows e no celular, grava e lê os dados no GitHub, tem consultas, relatório cronológico para impressão, gráficos, planilha Excel e login com criação de usuários.

## Como funciona (visão geral)
Você vai criar **dois repositórios** no GitHub:

| Repositório | Visibilidade | O que guarda |
|---|---|---|
| `condutores-cpr1` | Público | Só o aplicativo (sem nenhum dado). É o endereço que você abre no computador e no celular. |
| `condutores-dados` | **Privado** | Os serviços e os usuários (arquivo `condutores.json`). Só quem tem o token acessa. |

O aplicativo (público) usa um **token** para ler e gravar o arquivo no repositório privado. Por isso os dados ficam iguais em todos os aparelhos.

## Arquivos do pacote
- `index.html`, `manifest.webmanifest`, `sw.js`, `.nojekyll`, `icons/`: o aplicativo.
- `dados-exemplo/condutores.json`: dados iniciais (serviços 564 a 570), opcional.

---

## PARTE 1 – Criar a conta e os dois repositórios
1. Acesse https://github.com e crie uma conta (ou entre na sua). Anote o seu **nome de usuário**: ele aparece no endereço `github.com/NOME`.
2. Clique no **+** (canto superior direito) > **New repository**.
3. Repositório dos dados: em *Repository name* escreva `condutores-dados`, marque **Private**, marque **Add a README file** e clique em **Create repository**.
4. Repita (+ > New repository) para o aplicativo: nome `condutores-cpr1`, marque **Public**, marque **Add a README file** e crie.

## PARTE 2 – Enviar o aplicativo ao repositório público
1. Descompacte o arquivo `condutores-cpr1.zip` no computador.
2. Abra o repositório `condutores-cpr1` no GitHub. Clique em **Add file > Upload files**.
3. Arraste para a página **index.html, manifest.webmanifest, sw.js, .nojekyll** e a pasta **icons** (o arquivo `.nojekyll` pode ficar oculto no Windows: ative *Exibir > Itens ocultos* no Explorador de Arquivos). Não precisa enviar `dados-exemplo`.
4. Role até o fim e clique em **Commit changes**.
5. Se já existir um `index.html` antigo, o upload o substitui. Confira depois que a data dele mudou.

## PARTE 3 – Ligar o GitHub Pages (gerar o endereço do aplicativo)
1. No repositório `condutores-cpr1`, clique em **Settings** (engrenagem, aba superior).
2. No menu da esquerda, clique em **Pages**.
3. Em *Build and deployment > Source*, escolha **Deploy from a branch**.
4. Em *Branch*, escolha **main** e a pasta **/ (root)**, e clique em **Save**.
5. Aguarde 1 a 3 minutos e atualize a página. Aparecerá o endereço: `https://SEU-USUARIO.github.io/condutores-cpr1/`. Guarde-o: é o endereço do aplicativo.

## PARTE 4 – (Opcional) Enviar os dados iniciais
1. Abra o repositório `condutores-dados` > **Add file > Upload files**.
2. Envie o arquivo `dados-exemplo/condutores.json`. Se o arquivo estiver em outra pasta, ele precisa ficar na **raiz** do repositório, com o nome exato `condutores.json`. Faça o **Commit changes**.
3. Se pular esta parte, o aplicativo cria o arquivo sozinho na primeira gravação.

## PARTE 5 – Gerar o token de acesso
1. Clique na sua foto (canto superior direito) > **Settings**.
2. No menu da esquerda, vá até o fim e clique em **Developer settings**.
3. Clique em **Personal access tokens > Fine-grained tokens > Generate new token**.
4. Preencha:
   - **Token name:** `Condutores CPR-1`.
   - **Expiration:** 90 dias (anote a data para renovar).
   - **Resource owner:** a sua conta (ou a organização, se o repositório for dela).
   - **Repository access:** marque **Only select repositories** e escolha **condutores-dados** (somente ele).
   - **Permissions > Repository permissions:** procure **Contents** e mude para **Read and write**. Deixe o resto sem acesso.
5. Clique em **Generate token** e **copie o código agora** (começa com `github_pat_`). O GitHub não mostra de novo; se perder, gere outro.

## PARTE 6 – Conectar o aplicativo e criar o administrador (1º aparelho)
1. Abra o endereço do aplicativo (Parte 3).
2. Na tela de entrada, clique em **Sincronização com GitHub** e preencha:
   - **Usuário ou organização:** o seu nome de usuário do GitHub (o dono do repositório).
   - **Repositório:** `condutores-dados`.
   - **Branch:** `main`. **Arquivo:** `condutores.json`.
   - **Token de acesso:** o código copiado.
3. Clique em **Salvar e sincronizar**. Se der certo, a tela muda para **Primeiro acesso** (ou **Entrar**, se já houver usuários). Se der erro, veja a tabela de problemas abaixo.
4. Em **Primeiro acesso**, informe nome, usuário e senha (mínimo 6 caracteres). Este será o **administrador**.
5. Ao entrar, o arquivo `condutores.json` aparece no repositório de dados. Confira no GitHub.

## PARTE 7 – Criar outros usuários
1. No aplicativo, abra **Usuários** (menu; só o administrador vê).
2. Informe nome, usuário, senha e o perfil (Comum ou Administrador) e clique em **Adicionar usuário**.
3. Para trocar uma senha, digite a nova senha na linha do usuário e clique em **Redefinir**. Para remover, clique em **Excluir** e depois em **Confirmar**.

## PARTE 8 – Usar em outros computadores e celulares
1. Abra o mesmo endereço do aplicativo no outro aparelho.
2. Abra **Sincronização com GitHub**, preencha os mesmos campos e **cole o mesmo token** (ou gere um token por aparelho, o que permite revogar só um deles).
3. Clique em **Salvar e sincronizar**. Em seguida entre com um usuário já criado: os dados aparecem.
4. **Instalar como aplicativo:**
   - Windows (Edge ou Chrome): menu **⋯** > **Aplicativos > Instalar este site como um aplicativo** (no Chrome: ícone de instalação na barra de endereço).
   - Android (Chrome): menu **⋮** > **Adicionar à tela inicial / Instalar aplicativo**.
   - iPhone (Safari): botão compartilhar > **Adicionar à Tela de Início**.

## PARTE 9 – Uso diário
- **Novo serviço:** menu *Novo serviço*, preencha e salve. Aparece “Gravado no GitHub”.
- **Consultas:** filtre por data, unidade, veículo, motorista e situação; toque numa linha para editar.
- **Relatório:** ordem cronológica, botão **Imprimir** (use “Salvar como PDF” na impressora, se quiser PDF).
- **Gráficos:** serviços por veículo e por unidade, respeitando os filtros.
- **Planilha:** botão **Gerar planilha Excel** (exporta o que está filtrado).
- **Sincronizar:** botão no topo da lista, para buscar o que outras pessoas gravaram.

---

## Problemas comuns
| Mensagem | Causa | Solução |
|---|---|---|
| o token é inválido ou expirou | Token digitado errado, incompleto ou vencido | Gere outro (Parte 5) e cole inteiro, sem espaços |
| repositório … não encontrado | Nome do dono/repositório errado, ou token sem acesso a esse repositório | Confira em `github.com/DONO/REPOSITORIO`; no token, *Repository access* deve incluir o repositório |
| o token só tem leitura | Contents está em Read-only | Edite o token: Contents > **Read and write** |
| o repositório é PÚBLICO | O repositório de dados não é privado | Settings do repositório > Danger Zone > Change visibility > Private |
| sem permissão de escrita ou branch inexistente | Token sem escrita, ou branch diferente de `main`, ou repositório sem nenhum arquivo | Crie um README no repositório, confira a branch e as permissões |
| Usuário ou senha incorretos | Usuário/senha errados, ou o aparelho ainda não está conectado ao GitHub | Conecte primeiro (Parte 6/8) e depois entre |
| Os dados não aparecem em outro aparelho | Aparelho não conectado, ou abriu outro endereço (arquivo .html local) | Use sempre o endereço do GitHub Pages e conecte o aparelho |
| Salvo no aparelho, mas não enviado | Sem internet ou erro no GitHub | Veja o motivo na mensagem e use **Sincronizar** depois |
| Página antiga depois de atualizar | Cache do navegador | Feche e abra o aplicativo, ou use Ctrl+F5 |

## Cuidados com a segurança
- O repositório de **dados deve ser sempre privado**; o aplicativo se recusa a conectar em repositório público.
- O token fica guardado no navegador de cada aparelho. Quem tiver o token lê o arquivo de dados. Use token restrito a um repositório, com validade, e revogue (Settings > Developer settings) se perder um aparelho.
- As senhas são gravadas com hash (SHA-256 com sal), mas a conferência é feita no navegador: serve para controlar o uso, não substitui um servidor com segurança forte.
- Não envie dados reais para o repositório público.

## Cópia de segurança e recuperação
- Cada gravação vira um commit. Em `condutores-dados` > arquivo `condutores.json` > **History**, você vê as versões e pode abrir uma anterior e copiar o conteúdo de volta.
- Para fazer backup manual, baixe o `condutores.json` periodicamente (Download raw file).

## Atualizar o aplicativo
Substitua o `index.html` no repositório público (Add file > Upload files > Commit). Os dados não são afetados.
