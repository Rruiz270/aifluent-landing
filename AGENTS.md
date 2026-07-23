# AIfluent Landing

Landing page institucional da AIfluent — plataforma de ensino de inglês e espanhol personalizado com inteligência artificial. Site estático de página única (`pt-BR`).

## Stack

- **Linguagem:** HTML5 + CSS + JavaScript (vanilla), tudo inline em `index.html`.
- **Framework/CSS:** Tailwind CSS via CDN (`cdn.tailwindcss.com`, config inline no `<head>`), biblioteca de animações AOS (`aos@2.3.4`), fonte Inter via Google Fonts.
- **Banco:** nenhum.
- **Deploy:** hospedagem estática (serve o `index.html` diretamente). Não há `vercel.json`/`netlify.toml` no repo.
- **Package manager:** nenhum — não há `package.json` nem lockfile.

## Comandos

Não há scripts de build/test/lint. É um único arquivo estático.

- **Visualizar localmente:** abra `index.html` no navegador, ou sirva a pasta (`npx serve .` ou `python3 -m http.server`).
- **Build:** não há etapa de build.

## Estrutura

- `index.html` — a página inteira: markup, config do Tailwind, estilos e scripts, todos inline.

## Convenções de código

- Tudo vive em `index.html`; mantenha markup, estilos e scripts organizados nas seções já existentes.
- Cores da marca definidas no `tailwind.config` inline (paleta `turquoise`, `brand.green/purple/turquoise`). Reutilize esses tokens em vez de hardcodar hex novos.
- Conteúdo em português do Brasil.

## Variáveis de ambiente

Nenhuma. O site não consome APIs autenticadas nem segredos.

## CI/CD & Deploy

- Não há workflows em `.github/workflows/`.
- Deploy tipicamente estático (Vercel/Netlify/qualquer host de estáticos) apontando para a raiz e servindo `index.html`.
- **Recomendação mínima (opcional):** um workflow em PR que valide o HTML (ex.: `html-validate` ou um linter simples) já basta para um site de uma página.

## Boas práticas de PR

- Branch naming: `feat/…`, `fix/…`, `chore/…`.
- Commits em [Conventional Commits](https://www.conventionalcommits.org/) (`feat:`, `fix:`, `chore:`, `docs:`).
- PRs pequenos e focados. Checklist:
  - página abre sem erros no console;
  - nenhum segredo/chave commitado;
  - screenshots de antes/depois para mudanças visuais (desktop e mobile).
- Ao menos 1 review; merge por squash; `main` sempre publicável.

## Testes

Não há testes automatizados (site estático). Verificação manual: abrir a página, checar responsividade (mobile/desktop), links e animações AOS.

## Segurança & dados

- Nunca commitar `.env` ou segredos (o site não deve precisar de nenhum).
- Sem coleta de dados pessoais no repo atual; se adicionar formulários que capturem dados, respeitar a LGPD (consentimento, finalidade, destino dos dados).
- Dependências vêm de CDNs externos (Tailwind, AOS, Google Fonts) — fixe versões e revise ao atualizar.

## Gotchas

- **Tailwind é carregado via CDN**, não há build. Não existe `tailwind.config.js` em arquivo; a config está inline no `<head>` do `index.html`. Editar um arquivo de config inexistente não terá efeito.
- Dependência de CDNs externos: sem internet, os estilos (Tailwind) e animações (AOS) não carregam.
- Tudo num só arquivo grande — cuidado com edições que quebrem tags não fechadas.
