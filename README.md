# Plato Vital — Funil LATAM (cães)

Funil em espanhol, em um único arquivo (`index.html`), sem build. É só subir em qualquer hospedagem estática (Vercel, Netlify, Cloudflare Pages, GitHub Pages).

**Fluxo:** Entrada → Quiz (10 perguntas) → Processamento → Resultado personalizado → Dossier → Animação → Página de vendas → Checkout (Bronce US$ 9,90 / Oro US$ 14,90)

## Antes de publicar

No topo do `<script>` em `index.html`, edite o `CONFIG`:

| Campo | O que colocar |
|---|---|
| `checkout.bronce` / `checkout.oro` | Links de checkout (Hotmart ou outra plataforma). As UTMs da URL são repassadas automaticamente. |
| `pixelId` | ID do Pixel da Meta. Se ficar vazio, nenhum evento é disparado. |
| `garantiaDias` | Prazo de garantia que a plataforma realmente oferece. |

## Eventos do Pixel

| Evento | Quando dispara |
|---|---|
| `PageView` | Ao carregar a página |
| `ViewContent` (`quiz_start`) | Clique em "Analizar" |
| `QuizComplete` (custom, com `nivel` e `raza`) | Fim do quiz |
| `ViewContent` (`sales_page`) | Exibição do resultado e da página de vendas |
| `InitiateCheckout` (`value`, `currency`) | Clique em um dos planos |

## Lógica do resultado

As perguntas de sintomas somam um peso de 0 a 3. O total define o nível: **≥7 Alto · 3–6 Moderado · <3 Baixo**.

As respostas graves (sangue nas fezes, gengiva sangrando, vômito frequente, feridas, prostração) acionam um aviso para levar o cão ao veterinário antes de mudar a dieta.

## Pendências

- Depoimentos reais (não há seção de depoimentos — não inventar).
- Confirmar se as receitas são balanceadas e revisadas por veterinário. Se forem, isso vira o argumento de autoridade mais forte da página.
- Mockups/imagens do produto (hoje são emojis e CSS).
