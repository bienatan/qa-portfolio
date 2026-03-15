# Falha na ordenação de resultados causa erro HTTP 500 em endpoint de API
## Descrição do Problema:

- Durante a execução de testes funcionais e de API em um módulo de análises operacionais, foi identificada uma falha na funcionalidade de ordenação de resultados, 
onde determinados campos, ao serem utilizados como critério de ordenação, fazem com que a API retorne erro interno do servidor (HTTP 500).

- O problema ocorre de forma seletiva: alguns parâmetros de ordenação funcionam corretamente, enquanto outros causam falha completa da requisição.

## Contexto do Teste:
- Tipo de teste: Teste de API / Validação de Regra de Negócio
- Ambiente: Produção
- Plataforma: Web (Backend / API REST)
- Perfil de usuário: Usuário autenticado com acesso ao módulo de análises

# Passos para Reprodução:
- Acessar o módulo de análises operacionais
- Realizar uma consulta válida utilizando filtros padrão
- Selecionar a opção de ordenação por determinados campos, como:
- FluidChanged
- FilterChanged
- OverallInterpretation
- Enviar a requisição
- Observar a resposta da API

## Resultado Esperado:
- A API deve retornar HTTP 200
- Os dados devem ser exibidos corretamente
- A ordenação deve respeitar o campo selecionado
- O comportamento deve ser consistente para todos os critérios de ordenação disponíveis

## Resultado Atual:
- A API retorna HTTP 500 – Internal Server Error
- Mensagem genérica de erro (“API Error”)
- Nenhum dado é retornado ao usuário
- Para outros campos de ordenação, a API responde corretamente com HTTP 200

# Impacto:
- Funcionalidade de ordenação indisponível para determinados critérios
- Dificuldade na análise correta dos dados
- Perda de confiabilidade do sistema
- Impacto direto na tomada de decisão do usuário
- Possível aumento de chamados de suporte

## Análise Técnica:
### Comportamento observado:
- O endpoint aceita múltiplos parâmetros de ordenação
- Apenas alguns valores específicos causam erro
- Não há validação prévia ou mensagem clara de erro para o usuário

## Indícios técnicos:
- Falha no tratamento de determinados campos no backend
- Possível problema de mapeamento ou serialização
- Ausência de validação de parâmetros permitidos para ordenação

# Técnicas de Teste Aplicadas:
- Teste de API
- Teste Negativo
- Análise de Regras de Negócio
- Teste de Consistência de Resposta
- Comparação de comportamento entre parâmetros válidos e inválidos

# Sugestões de Melhoria:
- Implementar validação dos campos permitidos para ordenação
- Garantir tratamento consistente para todos os critérios disponíveis
- Retornar mensagens de erro claras e informativas
- Evitar retorno de erro genérico (HTTP 500) para falhas previsíveis
- Criar testes automatizados para cobertura de ordenação

# Classificação do Defeito:
- Severidade: Alta
- Prioridade: Alta
- Tipo: Bug funcional / Falha de regra de negócio / Erro de API

# Aprendizado Demonstrado no Case:
- Importância de validar parâmetros aceitos pela API
- Riscos de falhas silenciosas em funcionalidades de apoio à decisão
- Impacto de erros de backend na experiência do usuário
- Necessidade de consistência no comportamento de endpoints

**Observação:**
- *Este case foi anonimizado e documentado exclusivamente para fins de estudo, aprendizado e portfólio profissional em QA.*
- *Nenhuma informação sensível, endpoint privado ou dado real de cliente foi exposto.*
