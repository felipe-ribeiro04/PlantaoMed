# 📋 PlantaoMed — Documentação do Projeto

> Repositório central de artefatos de documentação do sistema **PlantaoMed**.

---

## 📁 Estrutura do Repositório

```
PlantaoMed/
│
├── 01_Visao/                        # Documento de Visão do Projeto
├── 02_Requisitos/                   # Levantamento e especificação de requisitos
│   ├── funcionais/
│   ├── nao_funcionais/
│   └── casos_de_uso/
│
├── 03_Arquitetura/                  # Documento de Arquitetura e Diagramas
│   ├── diagramas/
│   │   ├── C4/                      # Diagramas C4 (Context, Container, Component, Code)
│   │   ├── UML/
│   │   │   ├── classes/
│   │   │   ├── sequencia/
│   │   │   ├── atividades/
│   │   │   └── estados/
│   │   ├── banco_de_dados/          # DER / Modelo Relacional
│   │   ├── implantacao/             # Diagrama de Implantação / Infraestrutura
│   │   └── componentes/             # Diagrama de Componentes
│   └── decisoes_arquiteturais/      # ADRs (Architecture Decision Records)
│
├── 04_Design/                       # Artefatos de design e UX/UI
│   ├── wireframes/
│   ├── prototipos/
│   └── guia_de_estilo/
│
├── 05_Testes/                       # Estratégia e artefatos de testes
│   ├── plano_de_testes/
│   ├── casos_de_teste/
│   └── relatorios/
│
├── 06_Implantacao/                  # Documentação de DevOps e infraestrutura
│   ├── infraestrutura/
│   ├── pipelines/
│   └── configuracoes/
│
├── 07_Contexto/                     # Artefatos de contexto e conhecimento do domínio
│   ├── glossario/                   # Glossário de termos do domínio
│   ├── referencias/                 # Referências e pesquisas externas
│   ├── atas_reuniao/                # Registro de decisões em reuniões
│   ├── personas/                    # Personas de usuário
│   └── regras_negocio/              # Regras de negócio documentadas
│
├── 08_Gestao/                       # Artefatos de gestão do projeto
│   ├── cronograma/
│   ├── riscos/
│   └── backlog/
│
├── 09_Entregas/                     # Histórico de versões e releases
│   └── versoes/
│
└── _templates/                      # Templates reutilizáveis de documentos
```

---

## 📄 Documentos Principais

| Documento | Localização | Status |
|-----------|-------------|--------|
| Visão do Projeto | `01_Visao/` | ✅ Concluído |
| Documento de Arquitetura | `03_Arquitetura/` | 🔄 Em elaboração |
| Requisitos Funcionais | `02_Requisitos/funcionais/` | ⏳ Pendente |
| Casos de Uso | `02_Requisitos/casos_de_uso/` | ⏳ Pendente |

---

## 🔄 Convenções de Nomenclatura

- **Documentos:** `NOME_DO_DOCUMENTO_vX.Y.md` (ex.: `documento_arquitetura_v1.0.md`)
- **Diagramas:** `TIPO_NOME_DIAGRAMA.puml` ou `.drawio` (ex.: `C4_contexto_plantaomed.puml`)
- **ADRs:** `ADR-NNN_titulo_curto.md` (ex.: `ADR-001_escolha_banco_de_dados.md`)
- **Atas:** `ATA_YYYY-MM-DD_assunto.md`

---

## 🛠️ Ferramentas Utilizadas

- **Diagramas:** PlantUML / Draw.io / Mermaid
- **Documentação:** Markdown
- **Versionamento:** Git

---

*Última atualização: Maio/2026*
