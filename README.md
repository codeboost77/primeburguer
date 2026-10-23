# The Prime Burger — Landing Page

One-page premium em HTML/CSS/JS puro, nível MotionSites: hero em vídeo com glow, scroll storytelling do burger explodido (seção pinada ~300vh), marquee em X, manifesto que acende no scroll, bento de combos com spotlight, galeria da marca arrastável, ícones que se desenham e footer com wordmark monumental que preenche de amarelo. Tudo self-hosted (fontes, GSAP, Lenis, imagens) e dentro da identidade: só Montserrat + Oswald, preto #080808 e amarelo #FFD629.

## Estrutura

```
prime-burger/
├── index.html            ← página completa (dados do cardápio num bloco JSON no topo do <body>)
├── 404.html · robots.txt · sitemap.xml
├── hero-background.mp4   ← vídeo do hero (já incluído)
├── hero-poster.jpg       ← primeiro frame do vídeo
└── assets/
    ├── hamburguer-explodido.webp      (hero da anatomia, fatiado via clip-path)
    ├── thumb-*.webp                   (recortes do vídeo: cardápio, combos, feed)
    ├── menu/*.webp                    (uma ilustração por item do cardápio, gerada por script)
    ├── js/  (gsap, ScrollTrigger, lenis)
    └── fonts/ (Green Matcha · Super Chips · Montserrat 300/500/600 · Oswald 700 de fallback)
```

## Editar conteúdo

- **Cardápio e preços**: bloco `<script type="application/json" id="menu-data">` no início do `<body>` do index.html. É um JSON simples por categoria.
- **Fotos do cardápio**: cada item tem o campo `foto` no JSON, apontando para `assets/menu/`. Troque o caminho pela foto real quando tiver.
- **Buscar `TODO cliente`** e completar: link exato da loja no Anota AI (constante `PEDIDO` no script e botões), dias de funcionamento, @ do Instagram, CNPJ e descrições dos lanches. Endereço, telefone, preços e avaliações já são os reais (Google/Anota AI, out/2026).
- **Avaliações**: a seção usa avaliações reais do perfil no Google (nota 4,5 · 1.724 avaliações). Atualize quando quiser destacar outras.
- robots.txt / sitemap.xml: trocar `SEUDOMINIO.com.br`.

## Deploy

Site estático: suba a pasta inteira na Vercel, Netlify, Cloudflare Pages ou hospedagem comum. Headers de segurança recomendados (Vercel, `vercel.json`):

```json
{"headers":[{"source":"/(.*)","headers":[
 {"key":"Strict-Transport-Security","value":"max-age=31536000; includeSubDomains; preload"},
 {"key":"X-Content-Type-Options","value":"nosniff"},
 {"key":"X-Frame-Options","value":"DENY"},
 {"key":"Referrer-Policy","value":"strict-origin-when-cross-origin"},
 {"key":"Permissions-Policy","value":"camera=(), microphone=(), geolocation=()"}
]}]}
```

## Comportamentos

- Navbar pill some ao rolar para baixo e volta ao subir; menu mobile fullscreen com stagger.
- Cursor custom vira "VER" sobre cards e "PEDIR" sobre CTAs (desktop).
- Anatomia do Prime: a seção pinada roda em todas as larguras; em telas estreitas os callouts viram legendas centralizadas que se revezam no rodapé do palco.
- Todos os botões de pedido (nav, hero, cardápio "+", destaques, CTA final, rodapé) apontam para o Anota AI; o telefone (38) 3216-0009 aparece na Unidade e no rodapé.
- Motion sempre ativo por decisão do cliente: o site ignora `prefers-reduced-motion` (o bloco está comentado no CSS/JS caso queira reativar).
- Trocar o vídeo: substitua `hero-background.mp4` (H.264, 1080p, 8–12s, <6MB) e gere um novo `hero-poster.jpg` do primeiro frame.

## Fontes

- Headlines: **Green Matcha** (base) + **Super Chips** (palavra de destaque); corpo, nav e preços em **Montserrat**.
- Atenção à licença: a Green Matcha (MJType) é gratuita só para uso pessoal; para o site comercial da hamburgueria é preciso adquirir a licença comercial em mjtype.com (os termos estão em assets/fonts/green-matcha-LICENCA.txt). Verifique também a licença da Super Chips junto à fonte de onde foi baixada.
