# Falha de validação permite cadastro com e-mail inexistente, resultando em bloqueio permanente de acesso

## Descrição do Problema:

- Durante a execução de testes funcionais no fluxo de cadastro de usuário de um site com grande volume de acessos a nível nacional, foi identificada uma falha crítica onde o sistema permite a criação de contas utilizando um endereço de e-mail inexistente ou inválido, sem qualquer validação técnica ou confirmação prévia.

- Posteriormente, o sistema exige validação de e-mail para login, impossibilitando o acesso do usuário e gerando um bloqueio permanente da conta, sem alternativa de recuperação.

## Contexto do Teste:
Tipo de teste: Teste Funcional / Validação de Regras de Negócio
- Ambiente: Produção
- Plataforma: Web
- Perfil de usuário: Novo usuário (primeiro acesso)

# Passos para Reprodução:
- Acessar a página de cadastro
- Preencher os campos obrigatórios com dados válidos
- Informar um e-mail inexistente (exemplo):
usuario.teste@dominioinexistente123 (sem um .com mesmo, oque agrava a situação)
- Finalizar o cadastro
- Tentar realizar login no sistema
- Sistema solicita confirmação de e-mail
- Tentativa de confirmação falha, pois o e-mail não existe

# Resultado Esperado:
- O sistema não deve permitir o cadastro com e-mails inválidos ou inexistentes
OU
- Deve existir uma validação técnica do formato + confirmação do e-mail antes da ativação da conta

# Deve haver um mecanismo de recuperação, como:
- Alteração de e-mail
- Reenvio de confirmação
- Suporte automatizado

# Resultado Atual:

O sistema:
- Aceita e-mail inválido no cadastro
- Exige validação de e-mail para login
- Não oferece alternativa de correção
- Usuário fica definitivamente bloqueado
- Conta fica inutilizável

# Impacto:
- Impacto crítico para o usuário final
- Perda de acesso permanente
- Aumento de chamados de suporte
- Frustração do usuário
- Risco de abandono da plataforma
- Falha grave de experiência do usuário (UX)

# Análise Técnica:

Ausência de:
- Validação de formato de e-mail (regex)
- Validação de domínio
- Confirmação de e-mail antes da ativação
- Regra de negócio inconsistente:
- Cadastro permissivo
- Autenticação restritiva

# Técnicas de Teste Aplicadas:
- Teste de Validação de Entrada
- Análise de Fluxo de Usuário
- Teste Negativo
- Análise de Regras de Negócio
- Teste de Experiência do Usuário (UX)

# Sugestões de Melhoria:
- Implementar validação de formato de e-mail no front-end e back-end
- Exigir confirmação de e-mail antes de ativar a conta
- Criar fluxo de alteração de e-mail não confirmado

# Classificação do Defeito:
- Severidade: Alta / Crítica
- Prioridade: Alta
- Tipo: Bug funcional / Regra de negócio

# Aprendizado Demonstrado no Case:
- Visão crítica de regras de negócio
- Foco em impacto real ao usuário
- Capacidade de identificar falhas além do “happy path”
- Pensamento analítico e preventivo em QA

Observação:
Este case foi anonimizado e documentado exclusivamente para fins de estudo, aprendizado e portfólio profissional em QA.
