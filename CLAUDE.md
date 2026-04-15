# CLAUDE.md — CLUBINHOFABERCASTELL

Site gerado pelo **SF (Site Factory)** em 15/04/2026.

## Contexto do Site

**Nome:** CLUBINHOFABERCASTELL
**Nicho:** Educação
**Keywords:** Faca parte da nossa familia um lugar para ser criativo A CRIATIVIDADE
**Paleta de cores:** ocean | **Fonte:** lora

Faça parte da nossa família 😉 um lugar para ser criativo A CRIATIVIDADE AJUDA O APRENDIZADO E NA EVOLUÇÃO DE NOSSAS CRIANÇAS  Cursos para professores de todas as matérias escolares. Aperfeiçoamento das habilidades de passar o conhecimento com técnicas inovadoras de ensino.  Técnicas diferenciadas que ajudam o aluno a melhorar o seu aprendizado, através de atividades que estimulam o seu  raciocínio lógico e estimulam o pensamento crítico.  Profissionais qualificados que ajudaram os alunos a escolherem a melhor opção profissional. A escolha profissional deve ser baseada nas habilidades que o aluno quer desenvolver e nas suas expectativas de futuro.  Nós trabalhamos sempre com o apoio aos nossas crianças e adolescentes. Tirar dúvidas faz parte do aprendizado, portanto sempre estará aberto um espaço para trocar ideias e tirar dúvidas.



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
  content/blog/    # Posts em Markdown
  pages/           # Rotas Astro (index, sobre, contato, blog, privacidade, termos)
  layouts/         # BaseLayout com fonte e cores dinâmicas
  styles/          # global.css com variáveis CSS de cor
public/
  images/          # hero.jpg, about.jpg, blog/*.jpg — inseridos automaticamente via Pexels
```

## O que editar

### Textos e conteúdo
- **`src/data/home.json`** — hero (título, subtítulo, botão), features (título, items), about section (título, desc, stats), posts
- **`src/data/sobre.json`** — conteúdo completo da página Sobre (hero, texto, missão)
- **`src/data/contato.json`** — título, subtítulo, email, tempo de resposta
- **`src/data/siteConfig.json`** — nome, slug, email, redes sociais, menu

### Imagens
Imagens já estão em `public/images/` (via Pexels). Para substituir, mantenha os mesmos nomes de arquivo:
- `hero.jpg` — imagem de fundo do Hero
- `about.jpg` — imagem da seção About (home)
- `sobre.jpg` — imagem de fundo da página Sobre
- `blog/{slug}.jpg` — imagens dos posts

### Posts do blog
Arquivos em `src/content/blog/`. Ajuste o tom de voz, adicione dados específicos do nicho e personalize conforme a identidade do site.

### Cores
Variáveis em `src/styles/global.css`: `--color-primary`, `--color-accent`, `--color-dark`.

## Deploy

```bash
bun install
bun run build
# Faça upload da pasta dist/ para Netlify, Vercel ou hosting estático
```
