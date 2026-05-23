# Projeto Módulo 3 – Low Code/No Code/Vibecode

## 📌 Desafio Escolhido

Desenvolvimento de um agregador automático de vagas de emprego. O desafio consistiu em construir um sistema capaz de consumir uma API pública de vagas, e entregar as oportunidades novas automaticamente ao usuário.

---

## 🖥️ Protótipo

### Como o protótipo funciona

Todo dia o sistema executa automaticamente o seguinte ciclo:

1. Busca até 150 vagas.
2. Para cada vaga, verifica se o campo de localização aceita candidatos brasileiros
3. Consulta o banco de dados para verificar se a vaga já foi notificada anteriormente
4. Se a vaga é nova, salva no banco de dados (Airtable)
5. Todas as vagas salvas ficam disponíveis no painel web para consulta


### Painel Web

Interface com listagem de vagas em cards, barra de busca, tipo de contrato e região, e botão "Apply" redirecionando para a candidatura externa.


---

## ⚙️ Plataforma Utilizada

### Plataformas

| Plataforma | Função no projeto |
|------------|-------------------|
| **Make** | Automação do fluxo completo |
| **Airtable** | Banco de dados de vagas |
| **Softr** | Front-end — painel web |

### Justificativa da Escolha

**Make** foi escolhido como motor de automação por ser a plataforma low-code com maior controle sobre fluxos de dados complexos dentre as avaliadas.

**Airtable** foi escolhido como banco de dados por oferecer integração nativa com o Make e com o Softr, eliminando a necessidade de configurar uma camada intermediária. Sua interface visual também facilita inspecionar os dados salvos e identificar problemas durante o desenvolvimento.

**Softr** foi escolhido como plataforma de front-end por ser a única ferramenta da lista que conecta diretamente ao Airtable como fonte de dados e gera interfaces responsivas com componentes prontos para listagem e busca. Ferramentas como Wix e Webflow são mais adequadas para sites institucionais estáticos e não oferecem essa integração dinâmica com banco de dados externo.


---

## ✅ Vantagens Identificadas

1. **Velocidade de prototipagem** — o ciclo completo (buscar API → armazenar →  notificar → exibir no painel) foi construído e validado em menos de um dia, sem escrever uma linha de código.

2. **Visualização do fluxo** — cada etapa do sistema se torna um bloco visual no Make, o que facilita entender e comunicar a lógica do produto antes de qualquer implementação técnica. Funciona como pseudocódigo executável.

3. **Integração nativa entre ferramentas** — Make, Airtable, e Softr se conectam diretamente sem precisar configurar servidores, autenticação complexa ou infraestrutura própria.

---

## ⚠️ Limitações Encontradas

1. **Lógica customizada restrita** — deduplicação com o campo primário do Airtable apresentou comportamento inconsistente nas fórmulas de busca. Funcionalidades simples em código exigiram múltiplas tentativas e gambiarras no Make.

2. **Debugging opaco** — quando algo falhou foi difícil identificar exatamente onde e por quê. A plataforma não oferece visibilidade real do que acontece por baixo de cada módulo, tornando a resolução de problemas mais lenta do que em código tradicional.

---

## 📚 Reflexão Crítica


A reflexão crítica mais importante do projeto foi perceber que ferramentas no-code são eficazes para **validar** a lógica de um produto e **visualizar** o fluxo do sistema rapidamente, mas apresentam limites reais quando a lógica exige controle fino. 


Essa comparação prática entre a abordagem no-code e a abordagem em código foi o maior aprendizado do projeto.

---

## 👥 Colaboração

**Kauan Santos Souza**

**Felipe Heleno Albuquerque de Souza**

As responsabilidades foram organizadas em fases sequenciais:

- **Fase 1:** Definição do problema e escolha das ferramentas
- **Fase 2:** Configuração da automação no Make.
- **Fase 3:** Configuração do banco de dados no Airtable.
- **Fase 4:** Desenvolvimento do front-end no Softr e conexão com o Airtable.
- **Fase 5:** Testes, ajustes e documentação.

---

## 📝 Registro da Aula

Data: **11/05/2026**
Atividade: Discussão crítica + mini-projeto de aplicação
Local: Laboratório de informática / Quadro branco
Professor(a): Kadidja Valéria

---

## 🚀 Próximos Passos

**Melhorias no protótipo atual:**
- Adicionar mensagem de fallback quando não houver vagas novas ("Nenhuma vaga nova hoje")

**Evolução para o Projeto Final:**

- Migrar o banco de dados de Airtable para SQLite com TTL de 30 dias para entradas antigas
Debugging opaco — quando algo dá errado é difícil entender exatamente onde e por quê.
