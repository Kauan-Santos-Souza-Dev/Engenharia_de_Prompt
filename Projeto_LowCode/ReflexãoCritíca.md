**Vantagens**

1. **Velocidade de prototipagem** — o ciclo completo (buscar API → filtrar → notificar → armazenar → exibir no painel) foi construído e validado em menos de um dia, sem escrever uma linha de código.

2. **Visualização do fluxo** — cada etapa do sistema se torna um bloco visual, o que facilita entender a lógica antes de implementar em código. Funciona como pseudocódigo executável.

3. **Integração nativa entre ferramentas** — Make, Airtable, Telegram e Softr se conectam diretamente sem precisar configurar servidores, autenticação complexa ou infraestrutura.

---

**Limitações**

1. **Lógica customizada é limitada** — deduplicação com campo primário do Airtable, digest consolidado no Telegram e mensagem de fallback são simples em código e complexos ou impossíveis no Make sem gambiarras.

2. **Debugging opaco** — quando algo dá errado é difícil entender exatamente onde e por quê. Em Node.js você lê o erro, localiza a linha e corrige. No Make você testa bloco por bloco sem visibilidade real do que acontece por baixo.

3. **Escalabilidade cara** — o plano gratuito do Make tem limite de operações por mês. Adicionar mais fontes de vagas, mais usuários ou mais execuções diárias rapidamente ultrapassa esse limite, gerando custo. Em Node.js rodando no próprio servidor isso tem custo zero.
