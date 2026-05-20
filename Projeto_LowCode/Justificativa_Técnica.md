# Justificativa Técnica da Escolha das Plataformas

## Make foi escolhido como motor de automação por ser a plataforma low-code com maior controle sobre fluxos de dados complexos dentre as avaliadas. 
Diferente do Zapier e do IFTTT, o Make permite iterar sobre arrays, aplicar filtros condicionais com múltiplas regras, encadear módulos com lógica de deduplicação e configurar schedulers com timezone explícito — funcionalidades essenciais para o funcionamento do Scraper.

## Airtable foi escolhido como banco de dados por oferecer integração nativa com o Make e com o Softr, eliminando a necessidade de configurar uma camada intermediária de API. 
Para o MVP, sua interface visual também facilita inspecionar os dados salvos e identificar problemas durante o desenvolvimento.

## Softr foi escolhido como plataforma de front-end por ser a única ferramenta da lista que conecta diretamente ao Airtable como fonte de dados e gera interfaces responsivas com componentes prontos para listagem, busca e filtragem — exatamente o que um painel de vagas exige. 
Ferramentas como Wix e Webflow são mais adequadas para sites institucionais estáticos e não oferecem essa integração dinâmica com banco de dados externo.

## Telegram Bot API foi mantido como canal de notificação por já estar disponível gratuitamente, sem limite de mensagens no plano gratuito,
e por ser o canal mais direto para entregar alertas em tempo real ao usuário sem exigir que ele acesse o painel web.
