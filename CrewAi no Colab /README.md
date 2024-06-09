## CrewAI no Google Colab: Usando o Gemini para Criação de Conteúdo

Este notebook do Google Colab demonstra como usar o CrewAI em conjunto com a API do Gemini para tarefas de criação de conteúdo.

### **O que é CrewAI?**

CrewAI é uma estrutura para construir agentes colaborativos. Esses agentes são projetados para trabalhar juntos em tarefas, cada um especializado em uma área específica. Este notebook utiliza três agentes:

* **Treinador de Carreira Sênior:** Fornece conselhos para iniciantes que estão entrando no campo da programação.
* **Escritor Influenciador:** Cria postagens envolventes de mídia social sobre o tema.
* **Redator Sênior:** Refinar postagens para concisão e clareza, garantindo que sejam adequadas para a mídia social.

### **Começando**

1. **Instalar Dependências:**
   ```bash
   !pip install -U duckduckgo-search langchain_google_genai crewai crewai_tools
   ```
2. **Obter a Chave da API do Google:**
   Você precisará de uma chave da API do Google para usar o LLM Gemini.  
   * **No Google Colab, use o código a seguir para armazenar sua chave da API:**
     ```python
     from google.colab import userdata
     userdata.set('GOOGLE_API_KEY1', 'SUA_CHAVE_API_AQUI') 
     ```
3. **Executar o Notebook:**
   Após definir sua chave da API, execute as células do notebook. Isso fará o seguinte:
    * Configurar o modelo Gemini Pro como seu LLM.
    * Definir os agentes e suas ferramentas.
    * Criar as tarefas para os agentes completarem.
    * Iniciar a Crew e executar as tarefas sequencialmente.
    * Exibir a postagem final no formato Markdown.

### **Seções Importantes de Código**

* **Configurando o LLM e as Ferramentas:** Esta seção define o LLM Gemini Pro e uma ferramenta de pesquisa na Web para os agentes usarem.
* **Criando Agentes:** Esta seção define os três agentes, suas funções, metas e histórias.
* **Definindo Tarefas:** Cada agente recebe uma tarefa relacionada à criação de conteúdo.
* **Iniciando a Crew:** Os agentes e as tarefas são combinados para formar uma Crew, que executa as tarefas sequencialmente.
* **Visualizando a Saída:** O notebook exibe a postagem final no formato Markdown.

### **Possíveis Melhorias**

* **Tratamento de Erros:** Este notebook não trata erros com graça. Você pode adicionar tratamento de erros para tornar o código mais robusto.
* **Processos Diferentes:** Explore o uso de diferentes tipos de `Process` (por exemplo, `Process.concurrent`) para ver como os agentes interagem de forma diferente.
* **Personalização:** Modifique as funções, metas e tarefas dos agentes para experimentar diferentes cenários de criação de conteúdo.

### **Exploração Adicional**

Este notebook é apenas um ponto de partida para usar o CrewAI com o Gemini. Explore a documentação do CrewAI ([(https://docs.crewai.com/)](https://docs.crewai.com/)) para saber mais sobre:

* **Tipos de Agentes** 
* **Ferramentas**  
* **Processos**
* **E mais**

***
