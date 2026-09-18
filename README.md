# 

## Introdução

Sistemas de NDR (Network Detection and Response) utilizam frameworks para identificar e responder ameaças, fornecendo ensaios de detecção e resposta para cobrir lacunas na gestão e segurança de eventos em uma rede. O uso dessa abordagem visa reduzir os indicadores de tempo médio de detecção e resposta (MTTD - Mean Time to Detect e MTTR - Mean Time to Repair) à ameaças, colaborando para a investigação com metadados da rede com eventos da rede, relação entre dispositivos e qualquer outra informação que ajude a isolar a ameaça **[[1]](#1---udipi-sudhir-the-event-data-management-problem-getting-the-most-from-network-detection-and-response-network-security-v-2021-n-1-p-12-14-2021)**. 

O autor **[[1]](#1---udipi-sudhir-the-event-data-management-problem-getting-the-most-from-network-detection-and-response-network-security-v-2021-n-1-p-12-14-2021)** também traz uma lista de desafios tradicionais para análises de trafego de rede:

- Viabilidade e custo de escalonamento de recursos de captura, análise e armazenamento de dados.
- Visibilidade limitada, dados criptografados e capacidade de monitoramento passivo.
- Custo da infraestrutura necessária para realizar a captura completa de pacotes em conexções de 10Gbps (como captura forense)
- Dificuldade de aplicar Machine Learning (ML) e realizar análises com os dados do tráfego.
- Tempo de resposta longo devido à softwares de alertas e tickets.


Ao que tange à análise comportamental de dados da rede em plataformas NDR, vale ressaltar que esta é utilizada para determinar um limiar base para determinar o que seriam variações ou anomalias do comportamento mapeado. Dentre os metadados utilizados para esse tipo de análise estão as consultas à DNS, ***handshakes*** de TLS e estatística de fluxo, o que pode permitir escalar o processo de análise mesmo com o aumento de largura de banda **[[2]](#2---sufyan-ali-et-al-trends-capabilities-and-challenges-in-modern-cyber-defense-a-systematic-review-of-detection-and-response-technologies-spectrum-of-engineering-sciences-v-4-n-1-p-464-503-2026)**.

[...]

Com base em análise comportamental, este projeto tem como objetivo aplicar conhecimentos de Mineração de Processos para a detecção de anomalias em uma rede utilizando a base de dados **CTU-13** criada pela CTU University, Czech Republic, que contém dados de tráfego de botnets e comportamentos considerados comuns de usuários e dispositivos.

## Metodologia

A base de dados selecionada para este projeto (**CTU-13**) contém descrições para cada coleta, informando o momento exato em que uma máquina foi infectada ou em que uma atividade do malware foi realizada, informando também o IP de cada computador, o tipo de bot e os links para a análise do malware. Um exemplo dessas notas pode ser visualizada em [CTU-Note-Example](./ctu-note-example.md). Todas as informações a respeito de como foi feita a coleta estão disponíveis em https://www.stratosphereips.org/datasets-ctu13.

O conjunto de dados está divido em três partes, sendo a primeira com o tráfego considerado "normal", a segunda apenas com o tráfego com bots e a última o tráfego misto. Também serão separados em série de tempos para a validação do processo que está sendo mapeado, como por exemplo o tráfego misto servindo de validação para o tráfego normal e vice-versa. Aqui "conjunto de dados" trata-se de dados de pacotes extraídos dos arquivos pcaps.

```
Obs: Este repositório contém apenas os dados extraídos e gravados em arquivos com a extensão CSV. Pois a junção dos arquivos pcaps ultrapassam 30GB e estão disponíveis no site da base de dados. 
```

Para aplicar os algoritmos de Mineração de Processos será necessário o pré-processamento dos dados brutos coletados em arquivos **.pcap**. Esses arquivos geralmente possuem poucas informações, mas o principal objetivo é extrair e organizar a comunicação dos dispositivos da rede por sessões, caputando se a comunicação foi completa ou interrompida através das flags TCP, por tempo de não resposta da conexão ou um novo pedido de conexão. Já para outros protocolos como UDP (sem flags de controle) outras métricas serão implementadas.

A extração e processamento será feita mediante alguns critérios, estes serão aplicados em etapas como: 

- 1- Extração de Fluxos (5-tupla ou 7-tupla);
- 2 - Enriquecimento (DNS - domínio consultado/regex, HTTP - Host, User-Agent, URI, método, País provedor - se possível)`;
- 3 - Rotulagem (Início de Fluxo, Final de Fluxo, Consulta DNS, Sem Resposta);
- 4 - Agrupamento (host interno -> externo, janelas temporais);
- 5 - Criação dos event logs para servir de input para algoritmos de MP.

```
Obs: 5-tuplas identifica um fluxo entre dois dispositivos, utilizando 5 atributos sendo eles: IP e Porta de Origem, IP e Porta de Destino e Protocolo Utilizado (TCP, UDP, ...).

(192.168.0.15, 50000, 8.8.8.8, 443, TCP)
```

Alguns testes foram realizados apenas com a primeira etapa `Extração de Fluxos (5-tupla)`, [...] seus resultados estão descritos na seção [Resultados](#testes-apenas-com-extração-de-fluxos-5-tupla).


### Extração dos dados

[...]


### Escolha dos Algoritmos de Mineração de Processos

[...]

## Resultados

[...]

### Testes apenas com Extração de Fluxos 5-tupla

[...]

## Referências

##### [1] - UDIPI, Sudhir. The event data management problem: getting the most from network detection and response. Network Security, v. 2021, n. 1, p. 12-14, 2021. 

#### [2] - SUFYAN, Ali et al. Trends, capabilities, and challenges in modern cyber defense: A systematic review of detection and response technologies. Spectrum of Engineering Sciences, v. 4, n. 1, p. 464-503, 2026.