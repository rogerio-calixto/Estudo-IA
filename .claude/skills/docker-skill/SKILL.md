---
name: docker-skill
description: Regras obrigatórias de boas práticas para CRIAÇÃO de novos arquivos Dockerfile e docker-compose.yml neste projeto. Use sempre que a tarefa envolver escrever um Dockerfile ou docker-compose.yml novo, mesmo que o usuário não mencione "boas práticas" explicitamente. Não se aplica a auditoria ou correção de arquivos já existentes.
---

Estas regras valem apenas para a criação de **novos** arquivos `Dockerfile` e `docker-compose.yml`. Arquivos já existentes não são revisados por esta skill.

## Dockerfile — projetos Node.js

- Não usar multi-stage build: o build/transpilação da aplicação já acontece fora do Docker (pipeline de CI externo), então o Dockerfile tem um único estágio.
- Instalar as dependências de produção dentro do próprio Dockerfile, com `npm ci --omit=dev` (ou equivalente do gerenciador usado). Nunca copiar `node_modules` já instalado de fora do container: se a imagem base for `alpine` (musl) e as dependências tiverem módulos nativos compilados fora (geralmente em glibc), eles não vão rodar.
- Copiar para dentro da imagem apenas o artefato já compilado (ex: pasta `dist/`), não o código-fonte.

## Dockerfile — qualquer linguagem

- Nunca usar a tag `latest` na imagem base.
- Fixar a tag com versão completa major.minor.patch (ex: `node:20.11.1-alpine`), não apenas major (ex: `node:20-alpine`).
- Preferir a variante mais enxuta disponível da imagem (ex: `alpine`).

## docker-compose.yml

- O projeto tem um único `docker-compose.yml`, sempre assumido como ambiente de desenvolvimento.
- Sempre que um serviço precisar de volume, usar bind-mount (não named volume).
- Todo bind-mount deve apontar para dentro de uma pasta `.docker/` na raiz do projeto (criar subpastas conforme necessário).
