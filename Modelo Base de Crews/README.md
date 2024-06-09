
## CrewAI com Google Gemini - Modelo Base

Este repositório fornece um modelo base para a criação de CrewsAI utilizando o poderoso modelo de linguagem Google Gemini 1.5 Pro no Google Colab. 

**O que é CrewAI?**

CrewAI é uma estrutura de agentes de inteligência artificial que trabalham juntos para atingir um objetivo comum. Em vez de depender de um único modelo de linguagem, CrewAI permite a criação de equipes de agentes, cada um com habilidades e ferramentas específicas, que colaboram para solucionar problemas complexos.

**Este modelo base te permite:**

- Definir agentes com diferentes papéis, objetivos e ferramentas.
- Criar tarefas específicas para cada agente.
- Configurar a ordem de execução dos agentes e a forma como eles interagem.
- Executar a CrewAI e visualizar os resultados.

**Este modelo base te permite:**

- Definir agentes com diferentes papéis, objetivos e ferramentas.
- Criar tarefas específicas para cada agente.
- Configurar a ordem de execução dos agentes e a forma como eles interagem.
- Executar a CrewAI e visualizar os resultados.

###  Inserção da API do Gemini

**Configure a API Key do Gemini:**

  * Acesse a sua conta do Google Cloud Platform e procure por "API Keys".
  * Crie uma nova chave API e copie o valor da chave.
  * **Importante:** Guarde sua chave API em um local seguro, pois ela permite acesso total à sua conta do Google Cloud Platform.

![Screen Shot 2024-06-09 at 19 56 53](https://github.com/GeorgeMyller/crews/assets/49486067/fb0c94b1-3846-48b7-9be6-a25962463c1c)

**Configuração Inicial:**
   
 **Instale as bibliotecas necessárias:**
        
 **Defina as ferramentas:**

**Crie os agentes:**

Criando Agentes:

Define a estrutura básica de agentes, com as seguintes informações:

- role: Posição do agente
- goal: Objetivo do agente
- backstory: Contexto do agente
- tools: Ferramentas que o agente irá usar
- temperature: Parâmetro para controlar a criatividade do agente
  
![Screen Shot 2024-06-09 at 19 55 49](https://github.com/GeorgeMyller/crews/assets/49486067/85c2a98d-f344-46f5-8544-d82a859a1580)

    ```python
    # Exemplo de agente
    agente_pesquisador = Agent(
        role="Pesquisador",
        goal="Encontrar informações relevantes sobre um tema específico.",
        backstory="Sou um especialista em encontrar informações na internet.",
        tools=[search_tool, youtube_tool],
llm = ChatGoogleGenerativeAI(
    model="gemini-1.5-pro",
    verbose=True,
    temperature=0.25 
    ,
    google_api_key=GOOGLE_API_KEY    )

    agente_analista = Agent(
        role="Analista",
        goal="Analisar informações coletadas e gerar insights.",
        backstory="Sou um especialista em interpretar dados e gerar conclusões.",
        tools=[scraper_tool, serper_tool],
        llm = ChatGoogleGenerativeAI(
    model="gemini-1.5-pro",
    verbose=True,
    temperature=0.25 
    ,
    google_api_key=GOOGLE_API_KEY    )
    ```

**Crie as tarefas:**

Define a estrutura básica de tarefas, com as seguintes informações:

- description: Descrição da tarefa
- agent: Agente responsável pela tarefa
- expected_output: Saída esperada da tarefa
- async_execution: Opção para executar a tarefa de forma assíncrona

![Screen Shot 2024-06-09 at 19 56 01](https://github.com/GeorgeMyller/crews/assets/49486067/4c544bc1-291a-44c2-860e-0be7fcc2258e)

    ```python
    # Exemplo de tarefa
    tarefa_pesquisa = Task(
        description="Pesquisar sobre 'inteligência artificial'.",
        agent=agente_pesquisador,
        expected_output="Um resumo sobre inteligência artificial.",
        async_execution=False
    )

    tarefa_analise = Task(
        description="Analisar os resultados da pesquisa e identificar as principais tendências.",
        agent=agente_analista,
        expected_output="Um relatório com as principais tendências em inteligência artificial.",
        async_execution=False
    )
    ```

 **Crie a Crew:**

Define a Crew com os seguintes parâmetros:

- agents: Lista de agentes, na ordem de execução
- tasks: Lista de tarefas a serem executadas
- verbose: Nível de detalhamento da saída
- process: Tipo de processamento (sequencial ou hierárquico)

![Screen Shot 2024-06-09 at 19 56 19](https://github.com/GeorgeMyller/crews/assets/49486067/eb18b6db-3f8c-413d-ae75-971a1b9bac1b)

    ```python
    crew = Crew(
        agents=[agente_pesquisador, agente_analista],
        tasks=[tarefa_pesquisa, tarefa_analise],
        verbose=2,
        process=Crew.Process.sequential
    )
    ```

 **Execute a Crew e exiba o resultado:**

    ```python
    result = crew.kickoff()

print("######################")
print(result)
    ```

**Observações:**

- Você pode adicionar mais agentes, tarefas e ferramentas conforme necessário.
- Ajuste os parâmetros de `temperature` para controlar a criatividade dos agentes.
- Explore diferentes modos de processamento (sequencial ou hierárquico) para ajustar a forma como os agentes trabalham.

**Recursos Adicionais:**

- [Documentação do CrewAI]( https://github.com/joaomdmoura/crewai/)
- [Documentação do Google Gemini]( https://ai.google.dev/gemini-api)

Com este modelo base, você pode começar a construir suas próprias CrewAI e explorar o potencial da inteligência artificial para solucionar problemas complexos.



