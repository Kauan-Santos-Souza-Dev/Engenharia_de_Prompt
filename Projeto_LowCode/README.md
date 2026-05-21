# Projeto Módulo 3 – Low Code/No Code/Vibecode

## 📌 Desafio Escolhido

Desenvolvimento de um agregador automático de vagas de emprego remoto. O desafio consistiu em construir um sistema capaz de consumir uma API pública de vagas, filtrar os resultados por critérios de localização, eliminar notificações duplicadas e entregar as oportunidades novas automaticamente ao usuário — tanto via mensagem no Telegram quanto por um painel web acessível pelo navegador.

O problema real resolvido: acompanhar manualmente múltiplas plataformas de emprego todos os dias é ineficiente e sujeito a perda de oportunidades por falta de tempo ou atenção.

---

## 🖥️ Protótipo

### Como o protótipo funciona

Todo dia às 08:00 (horário de Brasília) o sistema executa automaticamente o seguinte ciclo:

1. Busca até 150 vagas remotas na API pública da Remotive nas categorias software-dev, design e devops-sysadmin
2. Para cada vaga, verifica se o campo de localização aceita candidatos brasileiros
3. Consulta o banco de dados para verificar se a vaga já foi notificada anteriormente
4. Se a vaga é nova, salva no banco e envia uma notificação formatada no Telegram
5. Todas as vagas salvas ficam disponíveis no painel web para consulta

### Notificação no Telegram

Cada vaga gera uma mensagem no formato:
```
🚀 Nova vaga!

💼 Título da vaga
🏢 Nome da empresa
🔗 Link para candidatura
📅 Data de publicação
⏰ Tipo de contrato
```

### Painel Web

Interface com listagem de vagas em cards, barra de busca, filtros por tipo de contrato e região, e botão "Apply" redirecionando para a candidatura externa.

> Coloque os arquivos de imagem ou PDF na pasta `/docs`.

---

## ⚙️ Plataforma Utilizada

### Plataformas

| Plataforma | Função no projeto |
|------------|-------------------|
| **Make** | Automação do fluxo completo |
| **Airtable** | Banco de dados de vagas |
| **Telegram Bot API** | Canal de notificação |
| **Softr** | Front-end — painel web |

### Justificativa da Escolha

**Make** foi escolhido como motor de automação por ser a plataforma low-code com maior controle sobre fluxos de dados complexos dentre as avaliadas. Diferente do Zapier e do IFTTT, o Make permite iterar sobre arrays, aplicar filtros condicionais com múltiplas regras, encadear módulos com lógica de deduplicação e configurar schedulers com timezone explícito — funcionalidades essenciais para o funcionamento do Scraper.

**Airtable** foi escolhido como banco de dados por oferecer integração nativa com o Make e com o Softr, eliminando a necessidade de configurar uma camada intermediária. Sua interface visual também facilita inspecionar os dados salvos e identificar problemas durante o desenvolvimento.

**Softr** foi escolhido como plataforma de front-end por ser a única ferramenta da lista que conecta diretamente ao Airtable como fonte de dados e gera interfaces responsivas com componentes prontos para listagem, busca e filtragem. Ferramentas como Wix e Webflow são mais adequadas para sites institucionais estáticos e não oferecem essa integração dinâmica com banco de dados externo.

**Telegram Bot API** foi mantido como canal de notificação por ser gratuito, sem limite de mensagens, e por ser o canal mais direto para entregar alertas em tempo real sem exigir que o usuário acesse o painel ativamente.

---

## ✅ Vantagens Identificadas

1. **Velocidade de prototipagem** — o ciclo completo (buscar API → filtrar → notificar → armazenar → exibir no painel) foi construído e validado em menos de um dia, sem escrever uma linha de código.

2. **Visualização do fluxo** — cada etapa do sistema se torna um bloco visual no Make, o que facilita entender e comunicar a lógica do produto antes de qualquer implementação técnica. Funciona como pseudocódigo executável.

3. **Integração nativa entre ferramentas** — Make, Airtable, Telegram e Softr se conectam diretamente sem precisar configurar servidores, autenticação complexa ou infraestrutura própria.

---

## ⚠️ Limitações Encontradas

1. **Lógica customizada restrita** — deduplicação com o campo primário do Airtable apresentou comportamento inconsistente nas fórmulas de busca. Funcionalidades simples em código — como verificar se um ID já existe em uma lista — exigiram múltiplas tentativas e gambiarras no Make.

2. **Debugging opaco** — quando algo falhou foi difícil identificar exatamente onde e por quê. A plataforma não oferece visibilidade real do que acontece por baixo de cada módulo, tornando a resolução de problemas mais lenta do que em código tradicional.

3. **Escalabilidade limitada pelo plano gratuito** — o plano gratuito do Make tem limite de operações mensais. Adicionar mais fontes de vagas, mais usuários ou execuções mais frequentes rapidamente ultrapassa esse limite, gerando custo ou interrupção do serviço.

---

## 📚 Reflexão Crítica

A principal limitação enfrentada foi a deduplicação de vagas via Airtable. O campo primário da tabela tem comportamento diferente dos demais campos nas fórmulas de busca, causando registros duplicados mesmo com a lógica corretamente estruturada. A solução parcial foi ajustar a fórmula de `{id}` para `{Id}` e posteriormente tentar `SEARCH()`, sem resolução completa dentro das possibilidades da plataforma.

A reflexão crítica mais importante do projeto foi perceber que ferramentas no-code são eficazes para **validar** a lógica de um produto e **visualizar** o fluxo do sistema rapidamente, mas apresentam limites reais quando a lógica exige controle fino. A solução proposta para contornar essa limitação estrutural é reescrever o sistema em Node.js para a versão de produção, onde deduplicação, múltiplas fontes, mensagem de fallback e digest consolidado são problemas triviais resolvidos com poucas linhas de código.

Essa comparação prática entre a abordagem no-code e a abordagem em código foi o maior aprendizado do projeto.

---

## 👥 Colaboração

**Kauan Santos Souza**

**Felipe Heleno Albuquerque de Souza**

As responsabilidades foram organizadas em fases sequenciais:

- **Fase 1:** Definição do problema e escolha das ferramentas
- **Fase 2:** Configuração da automação no Make (fluxo, filtros, scheduler)
- **Fase 3:** Configuração do banco de dados no Airtable
- **Fase 4:** Desenvolvimento do front-end no Softr e conexão com o Airtable
- **Fase 5:** Testes, ajustes e documentação

---

## 📝 Registro da Aula

Data: **11/05/2026**
Atividade: Discussão crítica + mini-projeto de aplicação
Local: Laboratório de informática / Quadro branco
Professor(a): Kadidja Valéria

---

## 🚀 Próximos Passos

**Melhorias no protótipo atual:**
- Resolver a deduplicação criando uma coluna secundária no Airtable exclusivamente para o ID, fora do campo primário
- Adicionar mensagem de fallback no Telegram para quando não houver vagas novas ("Nenhuma vaga nova hoje")
- Incluir filtro por tipo de contrato (full-time, contract, part-time) no fluxo do Make

**Evolução para o Projeto Final:**
- Reescrever o sistema em Node.js para eliminar as limitações identificadas nas plataformas no-code
- Adicionar múltiplas fontes de vagas (Adzuna, Arbeitnow, Reed, The Muse, Jobicy)
- Implementar score de compatibilidade por palavras-chave para ranquear as vagas mais relevantes
- Migrar o banco de dados de Airtable para SQLite com TTL de 30 dias para entradas antigas
- Implementar modelo freemium com controle de volume de alertas por dia
Debugging opaco — quando algo dá errado é difícil entender exatamente onde e por quê. Em Node.js você lê o erro, localiza a linha e corrige. No Make você testa bloco por bloco sem visibilidade real do que acontece por baixo.

Escalabilidade cara — o plano gratuito do Make tem limite de operações por mês. Adicionar mais fontes de vagas, mais usuários ou mais execuções diárias rapidamente ultrapassa esse limite, gerando custo. Em Node.js rodando no próprio servidor isso tem custo zero.
