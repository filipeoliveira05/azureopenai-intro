# azureopenai-intro
Resumo das diferentes configurações e parâmetros utilizados no Playground do Azure OpenAI

# Tokenização
## O que é?
A tokenização é o processo de dividir texto em tokens, que podem ser palavras, subpalavras, caracteres ou até unidades especiais.\n
Este processo é essencial para modelos de linguagem de inteligência artificial entenderem e processarem texto.\n
Os modelos têm um limite máximo de tokens por resposta. Se um texto ultrapassa esse limite, os tokens extras são cortados.

## Como funciona?
1. Divisão do texto\n
   O texto é quebrado em partes menores (tokens), que podem ser palavras inteiras ou pedaços de palavras.\n
   Exemplo: O texto "Eu gosto de programação" seria dividido em ["Eu", "gosto", "de", "programação", "!"]
2. Uso de subpalavras (BPE - Byte Pair Encoding)\n
   Para lidar com palavras desconhecidas, pode ser utilizado a técnica BPE, que quebra palavras em subpartes.\n
   Exemplo: A palavra "programação" pode ser dividida em ["programa", "ção"]
3. Transformação de cada token em números\n
   Modelos de inteligência artificial não compreendem texto diretamente. Por isso, cada token é convertido num número (ID do token).

## Exemplo de Tokenização\n
Frase: *A tokenização é um aspeto crucial nos modelos de linguagem.*\n
Divisão do texto em tokens: ["A", "token", "ização", "é", "um", "asp", "eto", "crucial", "nos", "modelos", "de", "linguagem", "."]\n
Número de tokens: 13\n
IDs dos tokens: [32, 6602, 17403, 1212, 1713, 20545, 7555, 19008, 4001, 39564, 334, 108504, 13]

## Porque a tokenização é importante?\n
✅ **Eficiência**: O modelo processa tokens em vez de letras individuais, acelerando o processo.\n
✅ **Redução de Memória**: Menos tokens significam menos consumo de recursos.\n
✅ **Palavras Desconhecidas**: Ao dividir palavras complexas em partes menores, o modelo entende melhor termos novos.
