# 🌿 NutrIA — Assistente de Saúde e Nutrição com Inteligência Artificial

O **NutrIA** é uma plataforma web gratuita desenvolvida com o objetivo de facilitar o acesso a informações sobre saúde e nutrição, combinando calculadoras nutricionais automatizadas com um chat inteligente alimentado pela API Claude, da Anthropic.

O projeto foi desenvolvido para oferecer uma orientação inicial acessível, humanizada e de fácil utilização, especialmente para pessoas que enfrentam dificuldades de acesso a profissionais e serviços de saúde.

> ⚠️ **Aviso importante:** O NutrIA é uma ferramenta informativa e educacional. Suas respostas não substituem consultas, diagnósticos ou acompanhamentos realizados por profissionais de saúde.

---

## 📌 1. Problema, contexto e objetivo

### Problema identificado

O acesso a informações confiáveis sobre nutrição e alimentação saudável ainda representa um desafio para grande parte da população brasileira.

Dúvidas comuns, como quantidade de calorias diárias, índice de massa corporal (IMC), consumo de água e distúrbios alimentares, muitas vezes ficam sem respostas adequadas devido à falta de acesso a profissionais de saúde ou à desinformação encontrada na internet.

### Público-alvo

O público principal do NutrIA são pessoas das classes D e E, que enfrentam barreiras financeiras e geográficas para acessar serviços de saúde.

O projeto também atende:

- Pessoas de baixa renda que moram longe de postos de saúde, clínicas ou farmácias.
- Moradores de comunidades rurais e periféricas.
- Pessoas que convivem com ou suspeitam ter distúrbios alimentares.
- Pessoas que procuram orientações iniciais gratuitas sobre saúde e nutrição.

### Objetivo

Desenvolver uma plataforma web gratuita, acessível e fácil de utilizar, que combine calculadoras nutricionais automatizadas com um assistente virtual inteligente, fornecendo informações de maneira humanizada e incentivando sempre o acompanhamento profissional.

---

## 🛠️ 2. Tecnologias utilizadas

| Tecnologia | Aplicação no projeto |
|---|---|
| HTML5 | Estruturação das páginas e conteúdos |
| CSS3 | Estilização, cores, layouts e responsividade |
| JavaScript | Interatividade, cálculos e funcionamento do chat |
| Bootstrap 5.3.3 | Componentes e responsividade |
| Google Fonts | Tipografia Nunito e Playfair Display |
| Claude API | Processamento das mensagens e respostas da IA |
| Cloudflare Workers | Back-end serverless e comunicação segura com a API |

---

## 💻 3. Funcionalidades do site

### 3.1. Landing Page

A página inicial apresenta o NutrIA, suas funcionalidades e os principais recursos disponíveis.

Possui:
- Menu de navegação fixo.
- Apresentação do projeto.
- Botões de acesso rápido às funcionalidades.
- Avisos sobre as limitações da inteligência artificial.
- Layout responsivo para diferentes dispositivos.

### 3.2. Chat com Inteligência Artificial

O chat é a principal funcionalidade do projeto. Ele utiliza a API Claude para responder dúvidas relacionadas à saúde e nutrição.

Principais recursos:

- Conversação em linguagem natural.
- Histórico de mensagens durante a sessão.
- Indicador de digitação.
- Sugestões de perguntas frequentes.
- Botão para iniciar uma nova conversa.
- Filtro de mensagens fora do escopo.
- Formatação básica das respostas em Markdown.
- Tratamento de erros de comunicação com a API.

### 3.3. Calculadoras nutricionais

O site disponibiliza três calculadoras para fornecer estimativas relacionadas à saúde.

**Calculadora de IMC**

Calcula o Índice de Massa Corporal utilizando peso e altura.

Fórmula:

`IMC = peso / altura²`

Apresenta o resultado e sua classificação em uma escala visual.

**Calculadora de Água Diária**

Estima a quantidade diária de água com base no peso informado.

Fórmula utilizada:

`Quantidade de água = peso × 35 ml`

**Calculadora de Calorias Diárias**

Estima a taxa metabólica basal e o gasto energético diário, considerando:

- Peso.
- Altura.
- Idade.
- Sexo.
- Nível de atividade física.

Utiliza a fórmula de Harris-Benedict revisada e multiplicadores de atividade física.

### 3.4. Seções informativas

O NutrIA também apresenta conteúdos educativos sobre:

- Saúde e nutrição.
- Condições e doenças.
- Viroses.
- Distúrbios alimentares.
- Orientações e recursos de ajuda.

### 3.5. Recursos de emergência

O projeto apresenta informações de apoio e canais de ajuda, incluindo o CVV (188), além de reforçar a importância de procurar acompanhamento profissional.

---

## ⚙️ 4. Arquitetura e funcionamento da inteligência artificial

O funcionamento do chat foi organizado em três camadas:

| Camada | Componente | Responsabilidade |
|---|---|---|
| Usuário | Navegador (HTML, CSS e JS) | Interface, calculadoras e envio de mensagens |
| Back-end | Cloudflare Worker | Validação das requisições e proteção da chave de API |
| Inteligência Artificial | Claude API | Processamento das mensagens e geração das respostas |

### Fluxo de funcionamento

1. O usuário escreve uma pergunta no chat.
2. O JavaScript verifica se a mensagem está dentro do escopo de saúde e nutrição.
3. Caso seja permitida, o histórico da conversa é enviado ao Cloudflare Worker.
4. O Worker adiciona a chave de API armazenada de forma segura.
5. A requisição é encaminhada à API Claude.
6. A inteligência artificial processa o contexto e gera uma resposta.
7. O Worker devolve a resposta ao site.
8. O JavaScript formata e apresenta a mensagem na interface do chat.

### Segurança

O Cloudflare Worker foi utilizado para evitar que a chave de API da Anthropic ficasse exposta diretamente no código HTML ou JavaScript.

A chave é armazenada como variável de ambiente secreta no painel da Cloudflare.

---

## 🧠 5. Engenharia de Prompt

A engenharia de prompt foi fundamental para definir o comportamento da NutrIA.

Foi desenvolvido um **System Prompt** responsável por estabelecer:

- Identidade: a IA se apresenta como NutrIA.
- Especialidade: saúde, nutrição, alimentação e hidratação.
- Linguagem: acolhedora, empática e acessível.
- Limitações: não realizar diagnósticos, prescrições ou planos alimentares detalhados.
- Segurança: orientar a procura por profissionais de saúde.
- Formatação: utilizar negrito para destacar informações importantes e parágrafos curtos.

### Filtro de escopo

Além das instruções enviadas à IA, foi desenvolvido um filtro em JavaScript para controlar os assuntos das mensagens.

O filtro utiliza:

- Mais de 150 palavras permitidas relacionadas à saúde e nutrição.
- Palavras bloqueadas relacionadas a tecnologia, esportes, política, entretenimento e finanças.
- Normalização de acentos para melhorar a comparação dos textos.
- Prioridade das palavras permitidas quando aparecem junto a termos bloqueados.

### Histórico de conversa

As mensagens são armazenadas em um array JavaScript chamado `conversationHistory`, permitindo que a IA considere as mensagens anteriores e mantenha o contexto da conversa.

### Modelo utilizado

- Modelo: `claude-sonnet-4-20250514`.
- Limite configurado: 1000 tokens por resposta.
- Plataforma de back-end: Cloudflare Workers.
- API: Anthropic Claude API.

---

## 📝 6. Prompt completo utilizado para criação do site

Abaixo está o prompt utilizado como referência para orientar a criação da estrutura, identidade visual, funcionalidades e comportamento do NutrIA.

### PROMPT COMPLETO

```text
Crie um site completo em HTML, CSS e JavaScript em um único arquivo chamado nutria.html, com o seguinte conceito:

Tema: Saúde e nutrição
Nome do site: NutrIA
Cor principal: Verde
Especialidade do chat: Nutrição, alimentação, saúde e bem-estar.

ESTRUTURA E SEÇÕES OBRIGATÓRIAS

1. NAVBAR (fixo no topo)

- Fundo com gradiente da cor principal.
- Logo à esquerda com fonte serif (Playfair Display) e destaque em cor clara.
- Links de navegação à direita: Chat com IA, Calculadoras, Informações, Condições, Saiba Mais e Preciso de Ajuda.
- Responsivo com botão hambúrguer no mobile (Bootstrap 5).
- Scroll suave para âncoras.

2. HERO SECTION

- Gradiente diagonal da cor principal (escuro → médio → claro).
- Título grande com fonte serif, com trecho destacado em cor pastel clara.
- Subtítulo descritivo com opacity: 0.9.
- Badges/pílulas horizontais com ícones emoji listando as funcionalidades.
- Botão CTA "Falar com a IA ↓" com borda semitransparente, scroll para o chat.
- Círculo decorativo semitransparente no canto direito.

3. AVISO / ALERTA

- Card com fundo gradiente avermelhado (#fff0f0 → #ffe8e8).
- Borda esquerda vermelha (#d63031) com 5px.
- Título em vermelho com ícone ⚠️.
- Texto alertando sobre limitações do site e necessidade de profissional.
- Largura máxima de 860px centralizado.

4. NAVEGAÇÃO POR SEÇÃO (pills)

- Linha de botões/links estilizados como cápsulas (border-radius: 50px).
- Fundo branco, borda na cor principal, texto na cor principal.
- Hover/active: fundo na cor principal, texto branco.
- Flex wrap para adaptar ao mobile.

5. CHAT COM IA (seção principal)

Wrapper com sombra forte, border-radius 1.6rem,
altura fixa 600px, display: flex; flex-direction: column.

Header do chat:

- Avatar emoji à esquerda.
- Nome e descrição do assistente.
- Badge "Online" verde pulsante.
- Badge "Powered by Claude" com ícone SVG.
- Botão "🔄 Nova conversa" que limpa o histórico.

Área de mensagens (overflow-y: auto, flex: 1):

- Mensagens do usuário: alinhadas à direita,
  fundo verde, texto branco, border-radius assimétrico.
- Mensagens do bot: alinhadas à esquerda,
  fundo cinza claro, border-radius assimétrico.
- Avatar emoji em cada mensagem do bot.
- Animação typing indicator (3 bolinhas pulando).
- Mensagem de boas-vindas ao carregar.
- Aviso de internet lenta após 3 segundos de espera.

Sugestões rápidas (ocultas após primeiro envio):

- Botões cápsula com sugestões de perguntas frequentes.
- Fundo verde-pálido, hover muda para verde.

Input de texto:

- Textarea com auto-resize (máx. 120px).
- Borda arredondada verde, foco com sombra verde.
- Botão enviar circular com gradiente da cor principal.
- Enter envia (Shift+Enter quebra linha).

Disclaimer: texto pequeno sobre limitações da IA.

Lógica da IA:

- Histórico de conversa mantido em array
  (conversationHistory).
- Filtro de escopo por palavras-chave
  (lista de palavras permitidas e bloqueadas).
- Mensagens bloqueadas recebem aviso de fora do escopo.
- Chamada à API Claude via endpoint próprio
  (Cloudflare Worker ou similar).
- Tratamento de erros: 429 (rate limit), 401 (auth), genérico.
- Função addMessage(role, text) com suporte
  a Markdown básico (negrito, listas).
- Scroll automático para última mensagem.

6. CALCULADORAS (3 cards lado a lado)

Grid Bootstrap 3 colunas (col-lg-4), com gap.

Estrutura de cada card:

- Fundo branco, border-radius, sombra suave.
- Hover: sobe 4px, sombra mais intensa.
- Ícone em wrapper quadrado com border-radius 14px
  e cor de fundo temática.
- Título bold em cor principal.
- Descrição cinza.
- Formulário com inputs estilizados
  (borda verde arredondada, foco com sombra).
- Botão de calcular full-width com gradiente.
- Resultado animado (fadeIn, borda esquerda,
  valor grande em bold).
- Classificações com badges coloridos por faixa.

Calculadora 1 – IMC:

- Inputs: Altura (cm) e Peso (kg).
- Fórmula: peso / (altura_m²).
- Barra de gradiente visual com agulha indicadora
  (posição calculada em %).
- Classificações: Abaixo do peso / Normal /
  Sobrepeso / Obesidade (com cores distintas).
- Dica personalizada por classificação.

Calculadora 2 – Água Diária:

- Input: Peso (kg).
- Fórmula: peso × 35ml (ajustado para atividade física).
- Resultado em litros com dica de saúde.

Calculadora 3 – Calorias Diárias (TMB/TDEE):

- Inputs: Peso, Altura, Idade, Sexo (select),
  Nível de atividade (select).
- Fórmula de Harris-Benedict revisada.
- Multiplicadores por nível de atividade
  (sedentário, leve, moderado, intenso,
  muito intenso).
- Resultado em kcal/dia com classificação
  e meta sugerida.

7. SEÇÃO INFORMATIVA (fundo verde escuro)

- Background gradiente na cor principal.
- Título serif branco.
- Grid de cards com background:
  rgba(255,255,255,0.10),
  borda translúcida, backdrop-filter blur.
- Números grandes destacados em cor pastel.
- Parágrafos com opacidade 0.9.

8. SEÇÃO DE CONDIÇÕES / DOENÇAS (cards informativos)

- Grid de 2-3 colunas com cards brancos.
- Borda superior de 4px na cor principal.
- Tag categorizada (ex: distúrbio alimentar, virose).
- Título bold, parágrafo descritivo.
- Box de emergência/ajuda separado com
  fundo avermelhado.

Número do CVV (188) ou linha de crise.
Texto encorajador.

9. LINKS E RECURSOS DE AJUDA

- Box com fundo gradiente verde escuro.
- Layout flex: texto à esquerda,
  número de telefone à direita.
- Número em destaque grande, clicável (tel: link).
- Subtítulo em cor pastel.

10. FOOTER

- Fundo na cor principal mais escura.
- Logo repetida.
- Texto de disclaimer com fundo semitransparente.
- Links legais (Política de Privacidade,
  Termos de Uso, Contato).
- Copyright.

11. BOTÃO SCROLL TO TOP

- Fixo no canto inferior direito.
- Circular, cor principal, aparece após 300px de scroll.
- Smooth scroll para o topo.

PALETA DE CORES

:root {
  --color-deep: #0d5c2e;
  --color-mid: #1a7a4a;
  --color-light: #34a865;
  --color-pale: #d5f5e3;
  --white: #ffffff;
  --gray-soft: #f4faf7;
  --text-dark: #0a1f15;
  --text-mid: #3a5745;
  --danger: #d63031;
  --success: #00b894;
  --radius: 1.2rem;
  --shadow: 0 8px 32px rgba(13,92,46,0.10);
}

TIPOGRAFIA

Nunito (sans-serif): corpo do texto,
pesos 400, 600, 700, 800, 900.

Playfair Display (serif): títulos, logo,
números destacados — peso 700.

Importar via Google Fonts.

DEPENDÊNCIAS EXTERNAS

- Bootstrap 5.3.3 (via CDN).
- Google Fonts (Nunito + Playfair Display).
- Sem outras dependências — tudo vanilla JS.

COMPORTAMENTO DO CHAT (lógica JS detalhada)

// 1. Histórico de conversa
let conversationHistory = [];

// 2. Filtro de escopo
const PALAVRAS_PERMITIDAS = [
  'nutrição', 'alimentação', 'saúde',
  'hidratação', 'calorias', 'IMC',
  'vitaminas', 'proteínas', 'viroses',
  'distúrbios alimentares'
];

const PALAVRAS_FORA = [
  'futebol', 'política', 'entretenimento',
  'finanças', 'programação'
];

function isForaDoEscopo(texto) {
  // Normaliza acentos.
  // Verifica palavras permitidas primeiro.
  // Depois verifica palavras fora do escopo.
  // Mensagens curtas sem contexto são bloqueadas.
}

// 3. Função de envio
async function sendMessage() {
  // Validar input.
  // Verificar escopo localmente.
  // Adicionar na UI e no histórico.
  // Mostrar typing indicator.
  // Timeout de 3s → aviso de internet lenta.
  // Chamar API.
  // Tratar erros por status code.
  // Adicionar resposta no histórico e UI.
}

// 4. Renderização de markdown básico
function renderMarkdown(text) {
  // **negrito**, *itálico*, \n → <br>,
  // - item → <li>.
}

// 5. Nova conversa
function novaConversa() {
  // Limpar histórico.
  // Limpar UI mantendo mensagem de boas-vindas.
  // Mostrar sugestões novamente.
}

RESPONSIVIDADE

- Hero: padding reduzido no mobile.
- Cards: stack vertical abaixo de lg.
- Chat: height: calc(100dvh - 180px) no mobile,
  mínimo 400px, máximo 600px.
- Bubbles de mensagem: max-width 90% no mobile.
- Navbar: colapsa com hambúrguer.

NOTAS FINAIS

- Todo o CSS em <style> no <head>.
- Todo JS em <script> antes de </body>.
- IDs de âncoras para scroll:
  #home, #chat-nutria, #imc, #agua,
  #calorias, #viroses, #disturbios, #ajuda.
- Animações: fadeIn para resultados,
  bounce para typing indicator.
- Botões de sugestão chamam sendSuggestion(this),
  que lê o textContent do botão.
- Enter no input envia, Shift+Enter quebra linha
  (handleChatKey).
- Textarea com autoResize() vinculada ao evento input.
- Enter nos inputs das calculadoras também
  dispara o cálculo.
```

---

## ⚠️ 7. Limitações da solução

Apesar de funcional, o NutrIA apresenta algumas limitações técnicas e de conteúdo.

### Limitações técnicas

- **Filtro de escopo impreciso:** pode bloquear perguntas válidas ou permitir mensagens irrelevantes.
- **Sem persistência de dados:** o histórico é perdido ao fechar o navegador.
- **Limite de contexto:** conversas muito longas podem ultrapassar os limites de tokens.
- **Dependência de terceiros:** o chat depende da disponibilidade da API Anthropic e do Cloudflare Worker.
- **Sem cache:** cada mensagem gera uma nova chamada à API.

### Limitações de conteúdo

- A inteligência artificial pode apresentar informações incorretas ou desatualizadas.
- As respostas não consideram necessariamente o histórico médico, alergias ou condições preexistentes.
- A IA pode não identificar automaticamente todas as situações de urgência.
- As calculadoras apresentam estimativas baseadas em fórmulas e médias populacionais, não substituindo uma avaliação individual.

---

## 🚀 8. Melhorias futuras

Entre as melhorias que podem ser implementadas em versões futuras estão:

- **Autenticação de usuários:** permitir login e salvar históricos de conversas e cálculos.
- **Detecção automática de crises:** identificar mensagens de sofrimento emocional e indicar canais de ajuda.
- **Melhoria do filtro de palavras:** substituir listas estáticas por classificação de intenção utilizando IA.
- **Integração com banco de dados:** utilizar Cloudflare D1 para armazenar conversas e informações.
- **Validação de informações:** implementar RAG (Retrieval-Augmented Generation) com fontes nutricionais confiáveis.
- **Acessibilidade:** melhorar o suporte a leitores de tela e navegação por teclado.
- **Versão mobile:** transformar o projeto em Progressive Web App (PWA).

---

## 📚 9. Considerações finais

O projeto NutrIA demonstra como a Engenharia de Prompt pode ser aplicada no desenvolvimento de ferramentas úteis e responsáveis utilizando inteligência artificial.

A combinação de um System Prompt bem estruturado, filtro de escopo local, histórico de conversas e uma camada de back-end serverless possibilitou a criação de uma solução funcional, acessível e com potencial de impacto positivo.

Durante o desenvolvimento, foi possível compreender a importância de definir corretamente o papel, os limites, o tom e o comportamento esperado de uma inteligência artificial.

Apesar das limitações existentes, o NutrIA cumpre seu objetivo como protótipo de aplicação com IA voltada à saúde e nutrição, incentivando o acesso à informação e a busca por acompanhamento profissional.

---

**Projeto:** NutrIA — Assistente de Saúde e Nutrição com Inteligência Artificial  
**Ano:** 2026

