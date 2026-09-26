# ADR 0001 - Uso de cache em conjunto com banco de dados 

## Status

Aceita

## Contexto

O sistema realiza consultas frequentes ao banco de dados.
Em horários de pico, o aumento das consultas pode sobrecarregar
o banco e aumentar o tempo de resposta.

A equipe precisa reduzir a quantidade de consultas ao banco,
mantendo o banco com fonte oficial dos bancos.

## Alternativas

1. Consultar diretamente o banco de dados.
2. Utilizar cache em memória.
3. Utilizar cache com tempo de expiração (TTL).

## Critérios

- Desempenho
- Redução da carga no banco
- Consistência dos dados
- Escalabilidade
- Custo operacional

## Trade-offs

O cache reduz a quantidade de consultas ao banco e pode melhorar 
o desempenho, mas adiciona complexidade e pode fazer com que 
alguns dados fiquem temporariamente desatualizados.

## Decisão

Utilizaremos cache com tempo de expiração (TTL) para armazenar 
temporariamente dados consultados com frequência.

O banco de dados continuará sendo a fonte oficial das informações.

## Consequências

## Positivas

- Redução das consultas ao banco.
- Menor carga em horários de pico.
- Melhoria no tempo de resposta.
- Maior capacidade de atender acessos simultâneos.

### Negativas

- Aumento da complexidade da aplicação.
- Necessidade de controlar o cache.
- Possibilidade de dados temporariamente desatualizados.
- Necessidade de definir o tempo de expiração.

## Revisão

A decisão poderá ser revisada caso os requisitos de desempenho,
consistência ou infraestrutura sejam alterados.
