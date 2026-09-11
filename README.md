# Perdido em Palmeira

Um GeoGuessr só da cidade de Palmeira, PR: localização sorteada de verdade dentro do
município, com Street View de verdade (anda, gira, dá zoom) e um mapa pra você marcar
o palpite.

## Como configurar (só isso, e é 100% grátis)

### 1. Criar a API key do Google Maps

1. Acesse [console.cloud.google.com](https://console.cloud.google.com/) e faça login
   com sua conta Google.
2. Crie um projeto novo (qualquer nome, ex: `perdido-em-palmeira`).
3. O Google vai pedir pra vincular uma conta de faturamento (cartão de crédito) —
   isso é exigido mesmo no plano grátis, mas você tem **US$200 de crédito por mês**
   de graça. Um joguinho local não chega nem perto disso.
4. No menu, vá em **APIs e serviços → Biblioteca** e ative apenas:
   - **Maps JavaScript API**
5. Vá em **APIs e serviços → Credenciais → Criar credenciais → Chave de API**.
   Copie a chave gerada.
6. **Restrinja a chave** (importante, pra ninguém mais usar ela e gerar custo):
   - Clique na chave criada → **Restrições de aplicativo** → **Referenciadores HTTP (sites)**.
   - Adicione: `https://SEUUSUARIO.github.io/*` (troque pelo endereço real do seu GitHub Pages).
   - Em **Restrições de API**, marque só **Maps JavaScript API**.
7. (Recomendado) Em **Faturamento → Orçamentos e alertas**, crie um alerta de
   R$5 ou US$1 pra ser avisado por e-mail se algum uso inesperado acontecer.

### 2. Colar a chave no jogo

Abra o arquivo [`config.js`](config.js) neste repositório e troque:

```js
const GOOGLE_MAPS_API_KEY = "COLE_SUA_CHAVE_AQUI";
```

pela sua chave de verdade. Salve, comite e o GitHub Pages atualiza sozinho em
1-2 minutos.

### 3. Jogar

O site já está publicado em GitHub Pages (grátis, sem domínio). Depois de colar a
chave, é só abrir o link e jogar.

## Como funciona

- Todo dia, o jogo sorteia (com uma "semente" baseada na data) 5 pontos aleatórios
  dentro de uma área que cobre a zona urbana de Palmeira, e pergunta ao Google Street
  View qual é o panorama mais próximo de cada ponto — por isso os locais mudam de dia
  para dia e não são uma lista fixa.
- A pontuação usa a distância real (fórmula de haversine) entre seu palpite no mapa
  e o ponto sorteado: até 5.000 pontos por rodada, 25.000 no total.
- O resultado do dia fica salvo no seu navegador (`localStorage`) só pra mostrar
  "você já jogou hoje" — nada é enviado para nenhum servidor.

## Custos

- Hospedagem (GitHub Pages): **grátis para sempre**, sem domínio.
- Google Maps: **grátis** dentro da cota mensal, contanto que o tráfego continue
  pequeno (uso local/cidade). A restrição por referenciador HTTP evita que outra
  pessoa use sua chave em outro site.
