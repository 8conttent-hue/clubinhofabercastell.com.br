# CLAUDE.md — CLUBINHOFABERCASTELL

Site gerado pelo **SF (Site Factory)** em 15/04/2026. Migrado para o modelo Cloudflare + Supabase em 25/09/2026.

## Contexto do Site

**Nome:** CLUBINHOFABERCASTELL
**Nicho:** Educação
**Keywords:** Faca parte da nossa familia um lugar para ser criativo A CRIATIVIDADE
**Paleta de cores:** ocean | **Fonte:** lora

Faça parte da nossa família, um lugar para ser criativo. A criatividade ajuda o aprendizado e na evolução de nossas crianças. Cursos para professores de todas as matérias escolares. Aperfeiçoamento das habilidades de passar o conhecimento com técnicas inovadoras de ensino. Técnicas diferenciadas que ajudam o aluno a melhorar o seu aprendizado, através de atividades que estimulam o seu raciocínio lógico e estimulam o pensamento crítico. Profissionais qualificados que ajudaram os alunos a escolherem a melhor opção profissional. Nós trabalhamos sempre com o apoio às nossas crianças e adolescentes. Tirar dúvidas faz parte do aprendizado, portanto sempre estará aberto um espaço para trocar ideias e tirar dúvidas.

## Componentes visuais usados

| Seção | Variante |
|-------|----------|
| Header | Header-B |
| Hero | Hero-I |
| Features | Features-A |
| About Section | About-C |
| Posts | Posts-E |
| Footer | Footer-F |
| Página Sobre | Sobre-C |
| Página Contato | Contato-A |

## Estrutura do projeto

```
src/
  sections/        # Layout escolhido pelo SF — Header, Hero, Features, About, Posts, Footer, Sobre, Contato
  data/            # JSONs com todo o conteúdo editável
  lib/             # supabase.ts (cliente) e posts.ts (getPosts/getPostBySlug)
  components/      # Seo.astro (meta tags + JSON-LD)
  pages/           # Rotas Astro (index, sobre, contato, blog, privacidade, termos, [...slug])
  layouts/         # BaseLayout com fonte e cores dinâmicas
  styles/          # global.css com variáveis CSS de cor
public/
  images/          # hero.jpg, about.jpg, sobre.jpg
```

## O que editar

### Textos e conteúdo
- **`src/data/home.json`** — hero (título, subtítulo, botão), features (título, items), about section (título, desc, stats), posts
- **`src/data/sobre.json`** — conteúdo completo da página Sobre (hero, texto, missão)
- **`src/data/contato.json`** — título, subtítulo, email, tempo de resposta
- **`src/data/siteConfig.json`** — nome, slug, email, redes sociais, menu (título/descrição/OG/JSON-LD derivam daqui)

### Imagens
Imagens já estão em `public/images/` (via Pexels). Para substituir, mantenha os mesmos nomes de arquivo:
- `hero.jpg` — imagem de fundo do Hero (e og:image padrão)
- `about.jpg` — imagem da seção About (home)
- `sobre.jpg` — imagem de fundo da página Sobre

### Posts do blog
Os posts NÃO ficam mais em markdown local. São carregados do Supabase (tabela `network_posts`, filtrados por `domain = clubinhofabercastell.com.br`).
- `src/lib/posts.ts` — `getPosts()` e `getPostBySlug()`; `formatContentToHtml()` converte markdown → HTML.
- Sem painel admin. Novos posts/posts editados entram pela plataforma 8links e publicam automaticamente (via Git/CF).

### Cores
Variáveis em `src/styles/global.css`: `--color-primary`, `--color-accent`, `--color-dark`.

## SEO

- `src/components/Seo.astro` injetado pelo `BaseLayout`: title, description, canonical, OG, Twitter, `name="robots"`, JSON-LD (WebSite nas páginas estáticas, BlogPosting nos artigos).
- `src/pages/robots.txt.ts` e `src/pages/sitemap.xml.ts` gerados dinamicamente (sitemap inclui posts com lastmod).

## Deploy

```bash
bun install
bun run build
# Publicar no Cloudflare: a pasta dist/ é servida como Worker (adaptador @astrojs/cloudflare)
# Envs opcionais no CF: SUPABASE_URL e SUPABASE_ANON_KEY (fallbacks embutidos no código)
```