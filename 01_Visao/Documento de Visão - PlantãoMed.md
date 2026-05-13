# **PlantãoMed**

# **Documento de Visão**

1. # **Introdução**

	Este documento tem como propósito apresentar as diretrizes, o escopo e a visão de negócio do sistema PlantãoMed. Trata-se do projeto de construção de um novo software, em sua primeira versão (1.0), planejado como um sistema WEB multicliente voltado para o mercado, sem um cliente externo único, mas sim destinado a atender simultaneamente instituições de saúde (hospitais e clínicas) e médicos. O desenvolvimento da solução está sob a responsabilidade do Grupo 3, composto pelos membros Talles Henrique Pacheco de Queiroz, Felipe Alcântara Santos Ribeiro, Yuri Guerra, Miguel Luís Ferreira de Paula e Luíz Fernando Gomes de Almeida.  
	A motivação central para a criação do PlantãoMed surge da dificuldade crônica na democratização do acesso a plantões médicos. Hoje, muitos profissionais, especialmente os recém-formados, enfrentam um mercado de trabalho injusto, onde a alocação de turnos depende quase exclusivamente de indicações e networking. O uso de meios informais, como grandes grupos de WhatsApp, embora tente ampliar a circulação de vagas, resulta em informações desatualizadas, vagas preenchidas antes da visualização e falta de filtros adequados, fazendo com que as oportunidades circulem apenas entre os mesmos grupos. Em paralelo, hospitais perdem tempo e recursos tentando encontrar profissionais de qualidade para cobrir faltas de última hora.  
	A importância do PlantãoMed reside na sua capacidade de corrigir essas distorções e trazer justiça profissional ao setor. O software vem para centralizar oportunidades e conectar, de maneira inteligente, a necessidade urgente dos hospitais à disponibilidade de profissionais competentes, utilizando filtros de especialidade, localização e remuneração. Ao substituir a dependência exclusiva de "quem você conhece" por um sistema organizado e igualitário, o PlantãoMed garante que nenhum médico seja beneficiado de forma desonesta e que o mérito clínico prevaleça, além de trazer mais organização e segurança na validação de credenciais para os hospitais.

2. # **Contexto de negócio**

	O mercado de trabalho para plantões médicos no Brasil enfrenta um gargalo estrutural severo no que tange à alocação e distribuição de profissionais. A dinâmica de contratação para plantões é, historicamente, baseada na informalidade e no networking. Essa dependência de indicações cria um ecossistema injusto e restrito, onde o mérito clínico e a competência ficam em segundo plano. Como resultado, vagas circulam quase exclusivamente dentro de panelinhas, prejudicando médicos recém-formados, profissionais vindos de outras cidades ou aqueles que não possuem uma ampla rede de contatos.  
	Na outra ponta, o cenário para hospitais e clínicas também é ineficiente. Gestores de saúde perdem tempo e recursos valiosos na busca por profissionais para cobrir faltas de última hora, dependendo de ligações telefônicas e contatos informais para preencher escalas urgentes. Falta um processo padronizado que forneça às instituições a garantia imediata de que o médico alocado está com o registro profissional (CRM) válido e com sua documentação legal apta para o exercício da função.  
	A principal ferramenta utilizada atualmente para contornar a dependência de contatos são os grandes grupos de WhatsApp e Telegram. Embora tenham surgido com a intenção de democratizar as vagas, esses grupos rapidamente se tornaram ineficazes. Suas limitações incluem:

* Falta de organização e de filtros por região, especialidade ou disponibilidade de horário.  
* Volume excessivo de mensagens que se perdem em grupos com centenas de participantes.  
* Oportunidades que são preenchidas antes mesmo de o profissional visualizar o anúncio.  
* Risco elevado de exposição a golpes e informações desatualizadas.

	Os principais usuários impactados por este contexto dividem-se em dois grupos. O primeiro é composto por médicos (**com ênfase em recém-formados**) que buscam inserção no mercado, horários flexíveis e independência da indicação de terceiros. O segundo engloba as instituições de saúde (**hospitais e clínicas**), representadas por seus gestores e coordenadores de escala, que necessitam cobrir plantões rapidamente e com profissionais validados.  
	O problema ganha caráter de urgência diante da forte expansão demográfica da profissão médica. O Brasil forma atualmente mais de 50 mil novos médicos por ano. Projeções indicam que o país ultrapassará a marca de 1 milhão de médicos em atividade (cerca de 1.152.230) até o ano de 2035\. Além disso, o mercado de trabalho médico sofre com um processo contínuo de informalidade: em 2023, apenas 33,3% dos médicos ativos possuíam vínculo formal, demonstrando que a inserção via plantões, contratos autônomos e pessoas jurídicas (PJ) dominará o setor. Outro fator agravante é a má distribuição geográfica: em média, as capitais concentram 3,66 vezes mais médicos por mil habitantes do que as cidades do interior. Um sistema centralizado de plantões é urgente para absorver esse volume massivo de novos profissionais sem vínculos formais e alocá-los nas regiões e hospitais que mais necessitam.  
	Ao analisar o mercado, destacam-se métodos e plataformas que tentam suprir essa demanda:

* **Grupos de WhatsApp/Telegram (Solução Informal):**  
  * **Pontos Fortes:** Uso amplamente disseminado, gratuito, quebra parcial do monopólio de informações restritas.  
  * **Pontos Fracos:** Caótico, exige tempo excessivo para encontrar vagas, não possui filtros, alta concorrência desleal e total falta de segurança/validação de quem está publicando ou assumindo a vaga.

* **Revoluna (Concorrente de Mercado):**  
  * **Funcionalidades:** Utiliza uma inteligência artificial (Jullia) integrada ao WhatsApp para cruzar o perfil do médico (especialidade, região, horário) com oportunidades de plantão, enviando vagas direcionadas.  
  * **Pontos Fortes:** Elimina a poluição visual dos grupos de WhatsApp, traz agilidade enviando a vaga até o médico e promove a igualdade de acesso focada no perfil clínico.

* **Oportunidades de Melhoria (Lacunas para o PlantãoMed):** A Revoluna atua primariamente como uma assistente virtual focada no médico via WhatsApp. 

Há uma grande oportunidade para a criação de um sistema WEB centralizado (um painel completo) que ofereça uma interface robusta também para os hospitais, permitindo que gestores publiquem vagas de urgência ativamente e realizem a validação instantânea das credenciais e do CRM do médico, integrando as necessidades de gestão hospitalar com a alocação médica num ambiente mais seguro e estruturado.

3. # **Posicionamento**

   1. ## **Declaração do problema**

| O problema de | *Falta de médicos de qualidade para assumir plantões em hospitais de modo que nenhum seja beneficiado, onde é comum médicos assumem plantões apenas pelo networking que possuem.* |
| :---- | :---- |
| afeta | *Médicos e Hospitais*  |
| cujo impacto é | *Angariar médicos competentes para assumir plantões sem favorecer ninguém* |
| uma solução de sucesso deveria | *Nenhum beneficiado de forma desonesta  Profissionais competentes  Hospitais mas organizados*  |

   2. ## **Declaração da visão do software**

| Para | *Médicos como clientes e Hospitais como administradores contratantes* |
| :---- | :---- |
| Que | *Conecta ambos oferecendo oportunidades que, mesmo sendo únicas, são justas e organizadas* |
| O | PlantãoMed |
| É um | *Site* |
| Que | *Que conecta médicos com hospitais para suprir escalas de plantões* |
| Diferente de | *Sites que apenas fornecem looks de telegram*  |
| Nosso produto | *Garante bons profissionais dando a mesma oportunidade para todos, e possibilitando que tanto os profissionais quanto o hospital possam se organizar para cumprir aquilo sem ser “de última hora”.* |

4. # **Descrição das partes interessadas**

| Nome | Descrição | Responsabilidades |
| :---- | :---- | :---- |
| Administrador Hospitalar | Gestores de RH ou diretores técnicos de clínicas e hospitais. | Publicar vagas de plantão, validar credenciais dos candidatos e avaliar o desempenho profissional. |
| Médico Plantonista | Profissionais de medicina com registro ativo. | Buscar e candidatar-se a plantões, cumprir os horários assumidos e manter seu perfil atualizado. |
| Desenvolvedores | Equipe de desenvolvimento do software (Talles, Felipe, Yuri, Miguel e Luiz). | Garantir o funcionamento técnico do sistema, a segurança dos dados e a evolução da plataforma. |

5. # **Visão geral do produto**

   1. ## **Necessidades e funcionalidades**

| Necessidade | Funcionalidade | Prioridade | Responsável |
| :---- | :---- | :---- | :---- |
| **Otimização do tempo do médico:** Profissionais de saúde têm dificuldade em encontrar, de forma **centralizada**, plantões que se encaixem em suas especialidades, localização e horários livres. | **Painel de Busca e Filtros Personalizados:** Oferece aos médicos um mural para buscar plantões filtrando por especialidade, hospital, data e valor da remuneração. | Alta | Talles |
| **Cobertura rápida de ausências**: Hospitais e clínicas perdem muito tempo e esforço (ligações, grupos de mensagens) tentando encontrar médicos para cobrir faltas de última hora. | **Publicação de vagas de urgência**: Permite que gestores publiquem turnos abertos com um nível de urgência definido e o sistema notifica instantaneamente os médicos cadastrados e disponíveis. | Média | Felipe |
| **Segurança e conformidade:** Instituições de saúde precisam de garantias de que o profissional assumindo o plantão está legalmente apto e com a documentação em dia. | **Validação de Perfil e Credenciais:** Conferência da validade/ veracidade do registro profissional (CRM) | Baixa | Yuri |
| **Redução de absenteísmo:** Ocorrência de atrasos ou faltas por simples esquecimento do médico, o que desfalca o atendimento aos pacientes. | **Sistema de Lembretes e Confirmação:** Envio de notificações automáticas de aviso próximo ao início do plantão assumido pelo profissional. | Baixa | Miguel |
| **Garantia de qualidade e confiabilidade:** Hospitais e clínicas precisam monitorar o histórico de comprometimento (como pontualidade e postura) dos médicos plantonistas para embasar futuras contratações e manter o padrão de atendimento. | **Sistema de Avaliação Pós-Plantão:** Permite que os gestores avaliem o desempenho do profissional após a conclusão do turno (notas e comentários sobre pontualidade, qualidade do serviço, etc.), criando um perfil de reputação no sistema. | Média | Luís |
| **Comunicação ágil e centralizada:** Dúvidas rápidas sobre o perfil dos pacientes ou infraestrutura do hospital muitas vezes impedem que o médico aceite a vaga imediatamente, e o uso de apps pessoais (como WhatsApp) mistura vida pessoal e profissional. | **Chat Integrado (Mensageria Segura):** Canal de comunicação direto e seguro dentro do próprio aplicativo entre o médico interessado na vaga e a coordenação hospitalar. | Baixa | Yuri |
| **Transparência financeira e repasses:** Médicos frequentemente enfrentam dificuldade para acompanhar os valores a receber no fim do mês, e hospitais sofrem com a conciliação manual desses pagamentos. | **Módulo de Relatórios Financeiros e Extratos:** Geração automática de extratos detalhados dos plantões realizados e valores devidos, facilitando a conferência tanto para o profissional quanto para a clínica. | Alta | Talles |

   2. ## **Requisitos não funcionais preliminares**

| Requisito não funcional | Prioridade |
| :---- | :---- |
| O sistema deve estar disponível em todos os navegadores mais comuns (Chrome, Safari, Edge etc.) | 1 |
| O sistema deve garantir uma disponibilidade em grande parte do tempo. Deve suportar picos de acesso repentinos (ex: fim de mês na montagem de escalas) sem degradação do serviço. | 2 |
| O sistema deve estar em total conformidade com a LGPD (Lei Geral de Proteção de Dados). Dados sensíveis (CRM, documentos pessoais, informações financeiras) devem ser protegidos. | 3 |
| O sistema web de gestão deve ser leve o suficiente para rodar em computadores de escritório padrão dos hospitais, não exigindo hardware dedicado ou placas de vídeo avançadas. | 1 |
| A interface do médico deve ser intuitivo o suficiente para ser concluído em no máximo 3 cliques a partir da visualização da notificação. | 1 |
| Premissa de Conectividade: Assume-se que tanto os gestores hospitalares quanto os médicos plantonistas possuirão acesso à internet (Wi-Fi ou dados móveis 3G/4G/5G) estável para o uso do sistema e recebimento de alertas em tempo real. | 1 |
| A arquitetura deve suportar o acúmulo histórico de dados de milhares de plantões mensais sem perda de velocidade nas buscas diárias. Essa retenção é crucial para preparar a base para futuras análises de inteligência de dados e painéis gerenciais. | 3 |

