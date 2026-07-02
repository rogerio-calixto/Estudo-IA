# Informações gerais

## Harness Engineering
  
   Limites de ações que sáo passados para a I.A.

   - Claude.md
   - MCPs
   - Skills
   - Specs

## Zero-shot - Prompt sem passar exemplos de como fazer algo.
           Passa-se apenas diretrizes
           (Usado para coisas de uso padrao)

## Few-shot - Prompt passando exemplos de como fazer algo.
           (Usado para algo customiado)

## Role Prompt

Determina a área de domínio da ação que será executada


## Chain of thought

Você dirige o raciocinio na LLM

## Engenharia de prompt
   Como a gente fala com o agente

## Engenharia de contexto
    O que o agente tem como base para raciocinar


## Skill (Nao passar de 500 linhas)

Define para a I.A. uma forma de se comportar ou insere uma nova habilidade para o agente
É um prompt em um arquivo markdown com uma sequencia de etapas que devem ser executadas pela I.A.

   ### Frontmatter: 
   
      Tem todas as definições para a I.A. saber em que situaações essa skill será usada
   
      ---
      - name: XXX
      - description:> YYY
      ---

   ### Body
   Markdown com as instruções

## Referências

https://www.skills.sh/