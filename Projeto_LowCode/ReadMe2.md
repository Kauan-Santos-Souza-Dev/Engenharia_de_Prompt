🚀 Project Scraper — Remote Job Board
Agregador automático de vagas remotas com notificação via Telegram e painel web. Desenvolvido como projeto prático da disciplina de Low Code / No Code.

📌 Sobre o Projeto
O Project Scraper resolve um problema real: acompanhar vagas de emprego remoto manualmente é trabalhoso. O sistema monitora automaticamente a API da Remotive, filtra as vagas relevantes, evit[...]

🛠️ Stack de Ferramentas
Ferramenta	Função
Make (Integromat)	Automação do fluxo — busca, filtra e notifica
Remotive API	Fonte de vagas remotas (gratuita, sem autenticação)
Airtable	Banco de dados — armazena vagas para deduplicação
Telegram Bot API	Notificações automáticas ao usuário
Softr	Front-end — painel web com listagem de vagas
⚙️ Fluxo do Sistema
Remotive API → Iterator → Filtro de Localização → Airtable Search → Filtro de Deduplicação → Airtable Create → Telegram Bot
Detalhe de cada etapa
Etapa	O que faz
HTTP Request	Busca vagas na Remotive API nas categorias software-dev, design e devops
Iterator	Processa cada vaga individualmente (equivalente a um loop)
Filtro de Localização	Verifica se o campo candidate_required_location aceita candidatos brasileiros
Airtable Search Records	Busca se o ID da vaga já existe no banco de dados
Filtro de Deduplicação	Se a vaga já foi notificada antes, descarta. Se é nova, segue
Airtable Create a Record	Salva a vaga nova no banco para referência futura
Telegram Bot	Envia notificação formatada com título, empresa, tipo, data e link
🔍 Lógica de Filtros
Filtro de Localização
Garante que apenas vagas acessíveis a candidatos brasileiros são notificadas.

A vaga passa se candidate_required_location:

Está vazio (sem restrição de local)
Contém: Brazil, Brasil, Worldwide, World, Remote, South America, Latin America, Americas
A vaga é descartada se especifica regiões que excluem brasileiros (ex: USA only, Europe only).

Filtro de Deduplicação
Compara o ID de cada vaga com os registros salvos no Airtable. Vagas já notificadas são descartadas automaticamente.

📊 Banco de Dados (Airtable)
Base: Scrapper
Tabela: Scrapper

Campo	Tipo	Descrição
Id	Text	ID único da vaga na Remotive
titulo	Text	Título da vaga
empresa	Text	Nome da empresa
link	URL	Link para candidatura
data da publicação	Date	Data de publicação da vaga
📱 Notificação Telegram
Cada vaga nova gera uma mensagem formatada:

🚀 Nova vaga!

💼 [Título da vaga]
🏢 [Empresa]
🔗 [Link para candidatura]
📅 [Data de publicação]
⏰ [Tipo de contrato]
🌐 Painel Web (Softr)
Interface web conectada diretamente ao Airtable exibindo:

Listagem de vagas em cards
Barra de busca
Filtros por tipo de contrato, região e categoria
Botão "Apply" abrindo o link externo da vaga
⏰ Scheduler
O sistema roda automaticamente todo dia às 08:00 (America/Sao_Paulo) via Make scheduler. Não requer intervenção manual.

🚧 Limitações Identificadas
Durante o desenvolvimento foram identificadas limitações inerentes às plataformas no-code:

Deduplicação: O campo primário do Airtable tem comportamento inconsistente em fórmulas de busca, causando registros duplicados em alguns cenários
Digest único: O Make não oferece controle fino para consolidar múltiplas vagas em uma única mensagem formatada sem ultrapassar o limite de caracteres do Telegram
Múltiplas fontes: Adicionar novas APIs de vagas exige blocos HTTP separados, tornando o fluxo mais complexo visualmente
Lógica customizada: Qualquer lógica além do que os módulos nativos oferecem requer gambiarras
Essas limitações fundamentam a decisão de reescrever o sistema em Node.js para a versão de produção.

🔮 Próximos Passos (Versão Node.js)
A versão de produção do Project Scraper será construída em Node.js com:

Deduplicação via seen.json com TTL de 30 dias
Múltiplas fontes: Adzuna, Arbeitnow, Reed, The Muse, Jobicy
fetchWithRetry com backoff exponencial
Scheduler via node-cron com timezone explícito
Score de compatibilidade por palavras-chave (MVP) e IA (Fase 3)
Logging em scraper.log
Mensagem "Nenhuma vaga nova hoje" quando não há novidades
📚 Contexto Acadêmico
Projeto desenvolvido para a disciplina de Low Code / No Code como exercício prático de automação de processos e desenvolvimento de produtos digitais sem código tradicional.

Conclusão prática: Ferramentas no-code são eficazes para validar a lógica de um produto, visualizar o fluxo do sistema e entregar uma versão funcional rapidamente. Para controle total, e[...]

👤 Autor
Kauan Santos Felipe Heleno Estudante de Análise e Desenvolvimento de Sistemas

👥 Divisão da Equipe
Kauan Santos
Estrutura da automação no Make
Integração com Telegram Bot
Lógica de deduplicação
Integração com Remotive API
Felipe Heleno
Modelagem do Airtable

Desenvolvimento do painel no Softr

Documentação técnica

Pesquisa e análise crítica da solução

🧠 Por que utilizar Low-Code / No-Code?
A proposta da disciplina incentivava o desenvolvimento rápido de soluções funcionais utilizando ferramentas low-code/no-code.

A abordagem escolhida permitiu:

Validar rapidamente a ideia do produto
Criar integrações reais sem infraestrutura própria
Automatizar fluxos complexos sem backend tradicional
Focar na lógica do sistema e experiência do usuário
Reduzir tempo de desenvolvimento
O uso de plataformas como Make, Airtable e Softr demonstrou como ferramentas no-code podem ser utilizadas para construir MVPs funcionais e automatizações reais de mercado.

Ao mesmo tempo, o projeto evidenciou limitações importantes relacionadas à escalabilidade, controle lógico e manutenção, justificando a futura migração para Node.js.
