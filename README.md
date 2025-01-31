# azureopenai-intro
Resumo das diferentes configurações e parâmetros utilizados no Playground do Azure OpenAI

---

## **Tokenização**
### O que é?
A tokenização é o processo de **dividir texto** em **tokens**, que podem ser palavras, subpalavras, caracteres ou até unidades especiais.  
Este processo é essencial para modelos de linguagem de inteligência artificial entenderem e processarem texto.  
Os modelos têm um limite máximo de tokens por resposta. Se um texto ultrapassa esse limite, os tokens extras são cortados.  

### Como funciona?
1. **Divisão do texto:**  
   O texto é quebrado em partes menores (tokens), que podem ser palavras inteiras ou pedaços de palavras.  
   **Exemplo:** O texto *"Eu gosto de programação"* seria dividido em `["Eu", "gosto", "de", "programação", "!"]`  
2. **Uso de subpalavras (BPE - Byte Pair Encoding):**  
   Para lidar com palavras desconhecidas, pode ser utilizada a técnica BPE, que quebra palavras em subpartes.  
   **Exemplo:** A palavra *"programação"* pode ser dividida em `["programa", "ção"]`  
3. **Transformação de cada token em números:**  
   Modelos de inteligência artificial não compreendem texto diretamente. Por isso, cada token é convertido num número (ID do token).  

### Exemplo de Tokenização
**Frase:** *A tokenização é um aspeto crucial nos modelos de linguagem.*  
**Divisão do texto em tokens:** `["A", "token", "ização", "é", "um", "asp", "eto", "crucial", "nos", "modelos", "de", "linguagem", "."]`  
**Número de tokens:** 13  
**IDs dos tokens:** `[32, 6602, 17403, 1212, 1713, 20545, 7555, 19008, 4001, 39564, 334, 108504, 13]`  

### Porque a tokenização é importante?  
✅ **Eficiência**: O modelo processa tokens em vez de letras individuais, acelerando o processo.  
✅ **Redução de Memória**: Menos tokens significam menos consumo de recursos.  
✅ **Palavras Desconhecidas**: Ao dividir palavras complexas em partes menores, o modelo entende melhor termos novos.  

---

## **System Message**
### O que é?
A **System Message** é uma mensagem especial usada para definir o comportamento do modelo antes do início da conversa. Diferente das mensagens do usuário, essa configuração é invisível para quem interage com o modelo, mas influencia suas respostas.

### Como funciona?
1. **Define o papel da IA:** Pode instruir o modelo a agir como um especialista em uma área específica.  
   **Exemplo:** *"Você é um assistente especializado em segurança cibernética."*
2. **Ajusta o tom e o estilo das respostas:** Pode determinar se o modelo responde de forma formal, casual ou técnica.  
   **Exemplo:** *"Responda de maneira objetiva e concisa."*
3. **Restringe ou amplia certos conteúdos:** Pode bloquear tópicos proibidos ou incentivar explicações detalhadas.  
   **Exemplo:** *"Evite dar conselhos médicos."*

### Porque a System Message é importante?
✅ **Personalização**: Permite ajustar o comportamento da IA conforme a necessidade.  
✅ **Controle**: Evita respostas inadequadas ou fora do escopo.  
✅ **Consistência**: Garante que o modelo siga uma abordagem uniforme ao longo da interação.  

---

## **Temperatura vs Top-P**
### O que são?
Os parâmetros **Temperatura** e **Top-P** controlam a aleatoriedade e a criatividade das respostas do modelo.  

### Como funcionam?
1. **Temperatura (🔥 Aleatoriedade):** Ajusta o quão imprevisível a resposta pode ser.  
   - Valores **baixos (ex: 0.1 - 0.3)** → Respostas mais diretas e previsíveis.  
   - Valores **altos (ex: 0.8 - 1.5)** → Respostas mais criativas e variadas.  
   **Exemplo:** Pergunta: *"Qual a capital da França?"*  
   - `Temperatura 0.2`: *"Paris."*  
   - `Temperatura 1.0`: *"Paris, a cidade luz, famosa por sua Torre Eiffel!"*  

2. **Top-P (🎯 Nucleus Sampling):** Controla a diversidade da resposta restringindo a escolha de palavras.
   - `Top-P = 1.0` → Considera todas as palavras possíveis.  
   - `Top-P = 0.9` → Usa apenas as palavras que somam 90% da probabilidade total.  
   - `Top-P = 0.5` → Escolhe entre um grupo ainda mais restrito, tornando as respostas mais previsíveis.  

### Quando usar?
✅ **Use Temperatura para ajustar aleatoriedade** (valores altos = criatividade, valores baixos = precisão).  
✅ **Use Top-P para limitar escolhas de palavras** (valores baixos = respostas mais seguras).  
✅ **Normalmente, se ajusta um ou outro, não ambos ao mesmo tempo.**  

---

## **Frequency Penalty vs Presence Penalty**
### O que são?
Os parâmetros **Frequency Penalty** e **Presence Penalty** controlam como o modelo lida com palavras repetidas, evitando redundância e incentivando diversidade.

### Como funcionam?
1. **Frequency Penalty (🔁 Evita Repetições)**
   - Penaliza palavras que já apareceram **muitas vezes** no texto.  
   - Quanto maior o valor, menos repetição ocorre.  
   **Exemplo:**
   - `Frequency Penalty = 0.0`: *"O cachorro é bonito. O cachorro gosta de brincar. O cachorro é feliz."*  
   - `Frequency Penalty = 1.0`: *"O cachorro é bonito. Ele gosta de brincar e é muito feliz."*  

2. **Presence Penalty (🆕 Incentiva Novidade)**
   - Penaliza palavras que **já apareceram pelo menos uma vez**, empurrando o modelo para introduzir novos conceitos.  
   **Exemplo:**
   - `Presence Penalty = 0.0`: *"Paris é uma cidade incrível. Paris tem monumentos históricos. Paris é um destino famoso."*  
   - `Presence Penalty = 1.0`: *"Paris é uma cidade incrível. Seus monumentos históricos, como a Torre Eiffel e o Louvre, atraem turistas do mundo todo."*  

### Quando usar?
✅ **Use Frequency Penalty para evitar repetições desnecessárias.**  
✅ **Use Presence Penalty para incentivar novas ideias e temas.**  
✅ **Valores moderados (~0.5) ajudam a equilibrar coerência e criatividade.**  

---

