# 🚃 VLT NEWS – Sobral

Painel de informações em tempo real sobre o VLT de Sobral/CE, com rastreador de viagens, status das linhas, horários oficiais, links úteis e mural de avisos.

> **Site público:** `index.html`  
> **Painel administrativo:** `admin.html` (protegido por senha)

---

## ✨ Funcionalidades

### 🌐 Site público (`index.html`)
- **Rastreador interativo** das linhas Sul e Norte
  - Exibe posição atual do VLT entre estações
  - Estados: *Em viagem*, *Parado no terminal* (com contagem regressiva), *Aguardando operação*
  - Indicador visual de status da linha (cor conforme situação real)
- **Horários completos** de ida e volta (grade oficial Metrofor)
- **Status geral** do VLT clicando no cabeçalho (com senha de admin)
- **Links externos** (Instagram, Comunidade, Canal – editáveis pelo admin)
- **Mural de avisos** (mensagens somem em 24h; usuários e admin podem postar)

### 🔐 Painel Admin (`admin.html`)
- Senha de acesso: `batata` (padrão; alterar no código)
- **Status por linha**: defina independentemente a situação da Linha Sul e Norte
- **Gerenciar links**: altere nome e URL dos links exibidos no site
- **Editar horários**: adicione/remova viagens, edite estações e horários, restaure padrão
- **Moderar mural**: postar como admin (destacado) e excluir qualquer aviso
- **Visão geral**: total de avisos ativos e status atual

---

## 🗄️ Banco de dados (Supabase)

O projeto utiliza o Supabase como backend. As credenciais já estão no código-fonte (projeto público).  
Caso queira usar sua própria instância, altere as constantes `SUPABASE_URL` e `SUPABASE_KEY` nos dois arquivos.

### Estrutura das tabelas necessárias:

| Tabela      | Colunas principais                 | Descrição                         |
|-------------|------------------------------------|-----------------------------------|
| `status`    | `line` (text), `color` (text), `updated_at` | Status de cada linha (sul/norte)  |
| `links`     | `id` (int8, auto), `name` (text), `url` (text) | Links do site                     |
| `comments`  | `id` (uuid), `text`, `is_admin` (bool), `created_at` | Mural de avisos                  |
| `schedules` | `id` (int8), `data` (jsonb), `updated_at` | Horários customizados             |

> **Importante:** O código já faz a manutenção automática (exclui comentários expirados, cria/atualiza registros). Basta criar as tabelas com as colunas indicadas e habilitar a API pública.

---

## 🚀 Como rodar

1. Faça o upload dos arquivos `index.html` e `admin.html` para um servidor estático (ex: Netlify, Vercel, GitHub Pages) ou abra localmente.
2. Certifique-se de que as tabelas no Supabase estão configuradas.
3. Acesse o site público e o painel (`/admin.html`).

---

## 🔧 Personalização

- **Senha do admin**: altere a constante `ADMIN_PASSWORD` em ambos os arquivos.
- **Horários padrão**: edite o objeto `DEFAULT_SCHEDULES` no admin e no index.
- **Tempo de vida dos avisos**: altere `COMMENT_LIFETIME_HOURS` (atual: 24h).
- **Links padrão**: o admin carrega os dados do banco; se não houver, o site exibe um placeholder.

---

## 📸 Preview

*(adicione imagens ou gifs do rastreador e do admin aqui, se desejar)*

---

Desenvolvido por **VR Web Solutions**.
