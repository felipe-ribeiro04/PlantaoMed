# Documento de Arquitetura de Software

| *PM – PlantãoMed* |  |
| :---: | :---: |
| **Gestor do Projeto** | **Gerente de Projeto** |
| Equipe responsável | Equipe responsável |
| A definir | A definir |
| A definir | A definir |

| *Objetivo deste Documento* |
| ----- |
| Este documento tem como objetivo descrever as principais decisões de projeto tomadas pela equipe de desenvolvimento e os critérios considerados durante a tomada destas decisões. Suas informações incluem a parte de *hardware* e *software* do sistema. |

| *Histórico de Revisão* |  |  |  |  |
| :---: | :---: | ----- | ----- | :---: |
| **Data** | **Demanda** | **Autor** | **Descrição** | **Versão** |
| 13/05/2026 | PM-001 | Equipe responsável | Criação inicial do Documento de Arquitetura de Software do PlantãoMed | 1 |
|  |  |  |  |  |
|  |  |  |  |  |

---

**Sumário**

[1. INTRODUÇÃO](#introdução)

[1.1 Finalidade](#finalidade)

[1.2 Escopo](#escopo)

[1.3 Definições, Acrônimos e Abreviações](#definições-acrônimos-e-abreviações)

[1.4 Referências](#referências)

[2. REPRESENTAÇÃO ARQUITETURAL](#representação-arquitetural)

[3. REQUISITOS E RESTRIÇÕES ARQUITETURAIS](#requisitos-e-restrições-arquiteturais)

[4. VISÃO DE CASOS DE USO](#visão-de-casos-de-uso)

[4.1 Casos de Uso significantes para a arquitetura](#casos-de-uso-significantes-para-a-arquitetura)

[5. VISÃO LÓGICA](#visão-lógica)

[5.1 Visão Geral – pacotes e camadas](#visão-geral-pacotes-e-camadas)

[6. VISÃO DE IMPLEMENTAÇÃO](#visão-de-implementação)

[6.1 Caso de Uso 001 – Busca e Candidatura a Plantões](#caso-de-uso-001)

[6.1.1 Diagrama de Classes](#diagrama-de-classes)

[6.1.2 Diagrama de Sequência](#diagrama-de-sequência)

[7. VISÃO DE IMPLANTAÇÃO](#visão-de-implantação)

[8. DIMENSIONAMENTO E PERFORMANCE](#dimensionamento-e-performance)

[8.1 Volume](#volume)

[8.2 Performance](#performance)

[9. QUALIDADE](#qualidade)

---

## 1. INTRODUÇÃO {#introdução}

### 1.1 Finalidade {#finalidade}

Este documento fornece uma visão arquitetural abrangente do sistema **PlantãoMed**, usando diversas visões de arquitetura para **representar** diferentes aspectos do sistema. O objetivo deste documento é capturar e comunicar as decisões arquiteturais significativas que foram tomadas em relação ao sistema.

O documento irá adotar uma estrutura baseada na visão "4+1" de modelo de arquitetura [KRU41].

*Figura 1 – Arquitetura 4+1*

> O modelo 4+1 organiza a arquitetura em cinco visões complementares: Lógica, Processo, Implementação, Implantação e Casos de Uso. Cada visão descreve o sistema sob uma perspectiva diferente, atendendo às necessidades de diferentes partes interessadas.

---

### 1.2 Escopo {#escopo}

Este Documento de Arquitetura de Software se aplica ao **PlantãoMed**, que será desenvolvido pelo **Grupo 3** (Talles Henrique Pacheco de Queiroz, Felipe Alcântara Santos Ribeiro, Yuri Guerra, Miguel Luís Ferreira de Paula e Luíz Fernando Gomes de Almeida).

O PlantãoMed é um sistema WEB multicliente voltado para o mercado de plantões médicos no Brasil. Seu escopo abrange a conexão entre médicos plantonistas e instituições de saúde (hospitais e clínicas), incluindo os módulos de publicação de vagas, busca e candidatura, validação de credenciais via CFM, sistema de notificações interno, avaliação pós-plantão, chat integrado e relatórios financeiros.

---

### 1.3 Definições, Acrônimos e Abreviações {#definições-acrônimos-e-abreviações}

**QoS** – Quality of Service, ou qualidade de serviço. Termo utilizado para descrever um conjunto de qualidades que descrevem os requisitos não-funcionais de um sistema, como performance, disponibilidade e escalabilidade [QOS].

**CRM** – Conselho Regional de Medicina. Registro profissional obrigatório para o exercício da medicina no Brasil.

**CFM** – Conselho Federal de Medicina. Órgão responsável pelo registro e regulamentação dos médicos no Brasil.

**API** – Application Programming Interface. Interface de programação que permite a comunicação entre sistemas de software.

**MVC** – Model-View-Controller. Padrão de projeto arquitetural que separa a aplicação em três camadas: Modelo (dados e regras de negócio), Visão (interface do usuário) e Controlador (intermediário entre Modelo e Visão).

**LGPD** – Lei Geral de Proteção de Dados. Legislação brasileira (Lei nº 13.709/2018) que regula o tratamento de dados pessoais.

**REST** – Representational State Transfer. Estilo arquitetural para sistemas distribuídos utilizado na construção de APIs web.

**JSON** – JavaScript Object Notation. Formato leve de troca de dados amplamente utilizado em APIs REST.

**PJ** – Pessoa Jurídica. Forma de contratação comum entre médicos plantonistas no Brasil.

---

### 1.4 Referências {#referências}

[KRU41]: The "4+1" view model of software architecture, Philippe Kruchten, November 1995, http://www3.software.ibm.com/ibmdl/pub/software/rational/web/whitepapers/2003/Pbk4p1.pdf

[QOS]: https://docs.oracle.com/cd/E19636-01/819-2326/6n4kfe7dj/index.html

**Documento de Visão – PlantãoMed** (versão 1.0): Descreve as diretrizes, escopo, contexto de negócio, partes interessadas e funcionalidades do sistema PlantãoMed. Elaborado pelo Grupo 3.

---

## 2. REPRESENTAÇÃO ARQUITETURAL {#representação-arquitetural}

Este documento irá detalhar as visões baseado no modelo "4+1" [KRU41], utilizando como referência os modelos definidos na MDS. As visões utilizadas no documento serão:

| Visão | Público | Área | Modelo da MDS |
| :---- | :---- | :---- | :---- |
| Lógica | Analistas | Realização dos Casos de Uso | Diagrama de Classes e Pacotes |
| Processo | Integradores | Performance, Escalabilidade, Concorrência | Diagrama de Sequência |
| Implementação | Programadores | Componentes de Software | Diagrama de Componentes |
| Implantação | Gerência de Configuração | Nodos físicos | Diagrama de Implantação |
| Caso de Uso | Todos | Requisitos funcionais | Diagrama de Casos de Uso |
| Dados | Especialistas em dados / Administradores de dados | Persistência de dados | Modelo Entidade-Relacionamento |

*Tabela 1 – Visões, Público, Área e Artefatos da MDS*

O sistema PlantãoMed adota a **arquitetura MVC (Model-View-Controller)**, organizada em três camadas principais:

- **Model (Modelo):** Responsável pela lógica de negócio, regras de domínio e acesso ao banco de dados MySQL. Implementado no backend Node.js.
- **View (Visão):** Interface do usuário construída com React, responsável pela apresentação dos dados e pela interação com o usuário.
- **Controller (Controlador):** Camada intermediária implementada no backend Node.js que recebe as requisições da View, aciona o Model e retorna as respostas adequadas.

A comunicação entre o frontend React e o backend Node.js ocorre por meio de uma API REST, utilizando o formato JSON para troca de dados.

---

## 3. REQUISITOS E RESTRIÇÕES ARQUITETURAIS {#requisitos-e-restrições-arquiteturais}

Esta seção descreve os requisitos de software e restrições que têm um impacto significante na arquitetura.

| Requisito | Solução |
| :---- | :---- |
| **Linguagem** | JavaScript (utilizada tanto no frontend quanto no backend, promovendo consistência tecnológica na equipe) |
| **Plataforma** | Servidor de aplicações Node.js com framework Express.js para exposição da API REST. Frontend servido via navegador web, compatível com Chrome, Safari, Edge e demais navegadores modernos. |
| **Segurança** | Autenticação simples com usuários armazenados no banco de dados interno MySQL. Senhas armazenadas com hash. Sem provedor externo de identidade neste momento. Conformidade com LGPD a definir em fases posteriores. |
| **Persistência** | Banco de dados relacional MySQL. O sistema deve suportar o acúmulo histórico de dados de milhares de plantões mensais sem perda de velocidade nas buscas diárias. |
| **Internacionalização (i18n)** | O sistema será desenvolvido exclusivamente em português do Brasil, sem suporte a internacionalização neste momento. |

*Tabela 2 – Requisitos e restrições arquiteturais*

---

## 4. VISÃO DE CASOS DE USO {#visão-de-casos-de-uso}

Esta seção lista as especificações centrais e significantes para a arquitetura do sistema.

Lista de casos de uso do sistema:

- **Caso de Uso 001 – Busca e Candidatura a Plantões**
- **Caso de Uso 002 – Publicação de Vaga de Urgência**
- **Caso de Uso 003 – Validação de Perfil e Credenciais (CRM via API do CFM)**
- **Caso de Uso 004 – Recebimento de Notificações e Lembretes**
- **Caso de Uso 005 – Avaliação Pós-Plantão**
- **Caso de Uso 006 – Chat Integrado entre Médico e Hospital**
- **Caso de Uso 007 – Geração de Relatórios Financeiros**
- **Caso de Uso 008 – Autenticação de Usuário**

### 4.1 Casos de Uso significantes para a arquitetura {#casos-de-uso-significantes-para-a-arquitetura}

**Descrição textual do Diagrama de Casos de Uso (arquivo de referência: `diagramas/UML/casos_de_uso/UC_principal_plantaomed.puml`)**

O diagrama deve apresentar dois atores principais:

- **Médico Plantonista:** Interage com os casos de uso de Autenticação, Busca e Candidatura a Plantões, Recebimento de Notificações, Chat Integrado e Geração de Relatórios Financeiros.
- **Administrador Hospitalar:** Interage com os casos de uso de Autenticação, Publicação de Vaga de Urgência, Validação de Credenciais, Avaliação Pós-Plantão, Chat Integrado e Geração de Relatórios Financeiros.

O sistema PlantãoMed aparece como o limite do sistema (system boundary), e a **API do CFM** aparece como ator secundário externo, acionada pelo caso de uso "Validação de Perfil e Credenciais".

Os casos de uso arquiteturalmente mais significativos são:

1. **UC-001 – Busca e Candidatura a Plantões:** Representa o fluxo central de valor para o médico. Envolve filtragem por especialidade, localização, data e remuneração, e desencadeia a candidatura do profissional.

2. **UC-003 – Validação de Credenciais:** Demonstra a integração externa com a API oficial do CFM, aspecto crítico para a confiabilidade e segurança da plataforma.

3. **UC-004 – Notificações Internas:** Representa o mecanismo de alerta em tempo real dentro do painel da aplicação, sem dependência de canais externos (e-mail, SMS ou push).

---

## 5. VISÃO LÓGICA {#visão-lógica}

Descrever uma visão lógica da arquitetura. Descreve as classes mais importantes, sua organização em pacotes de serviços e subsistemas, e a organização desses subsistemas em camadas. Também descreve as realizações dos casos de uso mais importantes, por exemplo, aspectos dinâmicos da arquitetura.

### 5.1 Visão Geral – pacotes e camadas {#visão-geral-pacotes-e-camadas}

**Descrição textual do Diagrama de Camadas (arquivo de referência: `diagramas/componentes/camadas_plantaomed.puml`)**

A arquitetura MVC do PlantãoMed é organizada nas seguintes camadas, da mais externa para a mais interna:

**Camada de Apresentação (View – React)**
- Componentes React responsáveis pela interface do usuário.
- Pacotes: `components/` (componentes reutilizáveis), `pages/` (telas da aplicação), `services/` (chamadas à API REST do backend).
- Principais módulos: PainelMedico, PainelHospital, BuscaPlantoes, ChatIntegrado, RelatorioFinanceiro, PainelNotificacoes.

**Camada de Controle (Controller – Node.js/Express)**
- Recebe requisições HTTP da View, valida parâmetros de entrada, aciona os serviços de negócio e retorna respostas JSON.
- Pacotes: `controllers/` (um controller por domínio de negócio).
- Principais controllers: UsuarioController, PlantaoController, ValidacaoController, NotificacaoController, AvaliacaoController, ChatController, FinanceiroController.

**Camada de Modelo (Model – Node.js)**
- Contém a lógica de negócio e as regras de domínio.
- Pacotes: `models/` (entidades do banco de dados), `services/` (regras de negócio), `repositories/` (acesso ao banco de dados MySQL).
- Principais entidades: Usuario, Medico, Hospital, Plantao, Candidatura, Notificacao, Avaliacao, Mensagem, Relatorio.

**Camada de Dados (MySQL)**
- Banco de dados relacional responsável pela persistência de todas as informações do sistema.
- Organizado em tabelas que correspondem às entidades do modelo.

**Integração Externa**
- **API CFM:** Acionada pelo ValidacaoController para verificar a validade do CRM do médico. A comunicação ocorre via requisição HTTP/REST.

**Descrição textual do Diagrama de Pacotes (arquivo de referência: `diagramas/UML/classes/pacotes_plantaomed.puml`)**

```
plantaomed/
├── frontend/                  (React)
│   ├── src/
│   │   ├── components/
│   │   ├── pages/
│   │   └── services/
│   └── public/
└── backend/                   (Node.js)
    ├── controllers/
    ├── models/
    ├── services/
    ├── repositories/
    ├── routes/
    ├── middlewares/
    └── config/
```

---

## 6. VISÃO DE IMPLEMENTAÇÃO {#visão-de-implementação}

### 6.1 Caso de Uso 001 – Busca e Candidatura a Plantões {#caso-de-uso-001}

#### 6.1.1 Diagrama de Classes {#diagrama-de-classes}

**Descrição textual do Diagrama de Classes (arquivo de referência: `diagramas/UML/classes/classes_uc001_plantaomed.puml`)**

O diagrama de classes para o caso de uso UC-001 deve apresentar as seguintes classes e relacionamentos:

**Classe `Medico`**
- Atributos: id, nome, crm, especialidade, localizacao, disponibilidade, email, senha (hash)
- Métodos: buscarPlantoes(filtros), candidatar(plantaoId), visualizarCandidaturas()

**Classe `Plantao`**
- Atributos: id, hospitalId, especialidade, dataHora, duracao, remuneracao, urgencia, status
- Métodos: listar(filtros), obterDetalhes(id)

**Classe `Candidatura`**
- Atributos: id, medicoId, plantaoId, dataCandidatura, status
- Métodos: criar(medicoId, plantaoId), listarPorMedico(medicoId), listarPorPlantao(plantaoId)

**Classe `PlantaoController`**
- Métodos: buscarPlantoes(req, res), candidatar(req, res)

**Relacionamentos:**
- `Medico` — 1 para N — `Candidatura` (um médico pode ter várias candidaturas)
- `Plantao` — 1 para N — `Candidatura` (um plantão pode receber várias candidaturas)
- `PlantaoController` depende de `Medico`, `Plantao` e `Candidatura`

#### 6.1.2 Diagrama de Sequência {#diagrama-de-sequência}

**Descrição textual do Diagrama de Sequência – UC-001 (arquivo de referência: `diagramas/UML/sequencia/seq_uc001_busca_candidatura.puml`)**

O diagrama deve representar o seguinte fluxo de interação:

1. **Médico** acessa o painel de busca no **Frontend React** e informa os filtros desejados (especialidade, localização, data, remuneração).
2. O **Frontend** envia uma requisição HTTP GET para o endpoint `/api/plantoes` no **PlantaoController** (Backend Node.js), com os filtros como parâmetros de query.
3. O **PlantaoController** aciona o **PlantaoService**, passando os filtros recebidos.
4. O **PlantaoService** consulta o **PlantaoRepository**, que executa a query SQL no banco de dados **MySQL** filtrando os plantões disponíveis.
5. O **MySQL** retorna a lista de plantões ao **PlantaoRepository**, que repassa ao **PlantaoService** e ao **PlantaoController**.
6. O **PlantaoController** retorna a resposta JSON ao **Frontend**, que renderiza a lista de plantões para o médico.
7. O **Médico** seleciona um plantão e confirma a candidatura.
8. O **Frontend** envia uma requisição HTTP POST para `/api/candidaturas` com o ID do médico e o ID do plantão.
9. O **PlantaoController** aciona o **CandidaturaService**, que registra a candidatura no **MySQL** via **CandidaturaRepository**.
10. O sistema retorna confirmação ao **Frontend**, que exibe mensagem de sucesso ao médico.

---

## 7. VISÃO DE IMPLANTAÇÃO {#visão-de-implantação}

Descrever os nodos físicos, as configurações e os artefatos que serão implantados.

**Descrição textual do Diagrama de Implantação (arquivo de referência: `diagramas/implantacao/implantacao_plantaomed.puml`)**

O diagrama de implantação deve apresentar os seguintes nodos e artefatos:

**Nodo: Dispositivo do Usuário (Client)**
- Tipo: Computador de escritório hospitalar ou dispositivo pessoal do médico
- Artefato: Navegador Web (Chrome, Safari, Edge etc.)
- Requisito: Acesso à internet (Wi-Fi ou dados móveis 3G/4G/5G)
- Comunicação: HTTPS para o Servidor Web

**Nodo: Servidor Web (Web Server)**
- Hospedagem: A definir
- Artefato: Aplicação React (bundle estático servido via servidor HTTP)
- Comunicação: Recebe requisições HTTPS do Client; realiza chamadas à API REST do Servidor de Aplicação

**Nodo: Servidor de Aplicação (Application Server)**
- Hospedagem: A definir
- Artefato: Aplicação Node.js com Express.js (API REST)
- Comunicação: Recebe chamadas REST do Servidor Web; consulta o Servidor de Banco de Dados; realiza chamadas à API externa do CFM

**Nodo: Servidor de Banco de Dados (Database Server)**
- Hospedagem: A definir
- Artefato: Instância MySQL
- Comunicação: Recebe queries SQL do Servidor de Aplicação via TCP/IP

**Nodo externo: API CFM**
- Sistema externo de propriedade do Conselho Federal de Medicina
- Comunicação: HTTPS/REST, acionada pelo Servidor de Aplicação para validação de CRM

**Observação:** Estratégias de containerização (Docker, Kubernetes), cloud provider e pipelines CI/CD estão **a definir** para versões futuras do sistema.

---

## 8. DIMENSIONAMENTO E PERFORMANCE {#dimensionamento-e-performance}

### 8.1 Volume {#volume}

Enumerar os itens relativos ao volume de acesso aos recursos da aplicação:

- Número estimado de usuários: A definir (o mercado conta com mais de 1 milhão de médicos ativos no Brasil até 2035; estimativa inicial de crescimento gradual)
- Número estimado de acessos diários: A definir
- Número estimado de acessos por período: Picos esperados ao final de cada mês, durante o período de montagem de escalas hospitalares
- Tempo de sessão de um usuário: A definir

### 8.2 Performance {#performance}

Enumerar os itens referentes à resposta esperada do sistema:

- Tempo máximo para a execução de determinada transação: O sistema deve ser suficientemente leve para rodar em computadores de escritório padrão dos hospitais, sem exigir hardware dedicado. A interface do médico deve permitir a candidatura a um plantão em no máximo 3 cliques a partir da visualização da notificação.

---

## 9. QUALIDADE {#qualidade}

Enumerar os itens de qualidade de software [QOS] significativos para a aplicação:

| Item | Descrição | Solução |
| :---- | :---- | :---- |
| **Escalabilidade** | O sistema deve suportar picos de acesso repentinos (ex.: fim de mês na montagem de escalas) sem degradação do serviço. Deve também suportar o acúmulo histórico de dados de milhares de plantões mensais sem perda de velocidade nas buscas diárias. | Arquitetura MVC com separação clara de responsabilidades entre frontend React e backend Node.js, facilitando escalonamento horizontal de cada camada de forma independente. Estratégia de escalonamento em cloud a definir em fases posteriores. |
| **Confiabilidade, Disponibilidade** | O sistema deve estar disponível em grande parte do tempo, garantindo que hospitais e médicos possam acessar a plataforma sempre que necessário, especialmente em situações de urgência. | Infraestrutura de hospedagem e estratégia de alta disponibilidade a definir. O banco de dados MySQL deve ser configurado com backups regulares. |
| **Portabilidade** | O sistema web deve estar disponível em todos os navegadores mais comuns (Chrome, Safari, Edge etc.) e deve rodar em computadores de escritório padrão dos hospitais, sem exigir hardware dedicado ou placas de vídeo avançadas. | Desenvolvimento em React, garantindo compatibilidade cross-browser. Layout responsivo para suporte a diferentes tamanhos de tela. |
| **Segurança** | O sistema deve estar em conformidade com a LGPD. Dados sensíveis (CRM, documentos pessoais, informações financeiras) devem ser protegidos. A autenticação é realizada com usuários armazenados no banco de dados interno MySQL. Sem provedor externo de identidade neste momento. | Senhas armazenadas com hash criptográfico. Comunicação via HTTPS. Validação de credenciais médicas integrada à API oficial do CFM. Regras avançadas de conformidade com LGPD a definir em fases posteriores. |
