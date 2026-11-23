# 🎯 Plano de Estudos: Certificação Oracle Cloud Infrastructure (OCI) Generative AI Professional (7 Dias)

Este guia prático foi desenhado sob a perspectiva de um **Especialista em IA e Arquitetura de Nuvem**, focado na preparação acelerada e prática para o exame oficial **Oracle Cloud Infrastructure Generative AI Certified Professional (1Z0-1127)** e **OCI AI Foundations (1Z0-1122)**.

---

## 🚀 Principais Melhorias em Relação ao Estudo Tradicional

1. **Abordagem Hands-on Prática (70% Prática / 30% Teoria):**
   Substituição da leitura passiva de documentação por testes ativos no OCI Generative AI Playground e chamadas de API.
2. **Engenharia de Prompt Aplicada a Modelos Nativos OCI:**
   Foco específico nos modelos integrados ao ecossistema Oracle (Cohere Command R/R+, Cohere Embed v3, Meta Llama 3), dominando seus hiperparâmetros de inferência.
3. **Domínio de RAG & Oracle AI Vector Search:**
   Integração profunda entre LLMs e o novo tipo de dado nativo `VECTOR` do **Oracle Database 23ai**, superando abordagens puramente teóricas.
4. **Resolução Ativa de Simulados com o Método "Pare, Confira, Use":**
   Auditoria criteriosa de enunciados para neutralizar as pegadinhas clássicas de arquitetura e segurança da banca da Oracle.

---

## 📊 Matriz do Cronograma Semanal (1 Hora / Dia)

| Dia | Tópico do Exame Oracle | Prioridade | Tempo Estimado | Resultado Esperado |
| :---: | :--- | :---: | :---: | :--- |
| **01** | OCI Generative AI Service & Pretrained Models | **Alta** | 60 min | Matriz comparativa de modelos e calibração de hiperparâmetros |
| **02** | Prompt Engineering Especializado (Cohere & Llama no OCI) | **Crítica** | 60 min | Prompts avançados no padrão Cohere Command validados |
| **03** | Embeddings & Oracle AI Vector Search (Database 23ai) | **Alta** | 60 min | Script SQL com busca por similaridade de cosseno |
| **04** | Arquitetura RAG (Retrieval-Augmented Generation) no OCI | **Crítica** | 60 min | Diagrama e especificação de pipeline RAG corporativo |
| **05** | OCI Generative AI Agents & Knowledge Bases | **Crítica** | 60 min | Especificação de agente OCI com ferramentas e busca |
| **06** | Fine-Tuning no OCI (LoRA, T-Few) e Dedicated AI Clusters | **Alta** | 60 min | Dataset JSONL validado e matriz de decisão "RAG vs Fine-Tuning" |
| **07** | Segurança, Políticas IAM e Simulado Final de Certificação | **Crítica** | 60 min | Simulado de 15 questões concluído com assertividade ≥ 85% |

---

## 📘 Passo a Passo Detalhado Dia a Dia

---

### Dia 1: OCI Generative AI Service & Pretrained Models
- **Prioridade:** **Alta**
- **Tempo Estimado:** **60 minutos** (15m teoria | 35m prática | 10m validação)
- **Melhorias Aplicadas:** Foco no funcionamento dos modelos de fundação pré-treinados disponíveis no OCI e suas diferenças de arquitetura (*Cohere Command R/R+* para raciocínio corporativo e *Meta Llama 3* para versatilidade open-source).
- **Atividade Prática:**
  1. Acessar o console do OCI (ou interface de simulação de playground).
  2. Testar o mesmo prompt de sumarização variando os hiperparâmetros:
     - `Temperature` (0.1 para fatos estritos vs 0.8 para criatividade);
     - `Top-p` e `Top-k` (corte de cauda probabilística);
     - `Frequency Penalty` e `Presence Penalty` (redução de repetição de tokens);
     - `Stop Sequences` (condições de parada controlada).
  3. Mapear a diferença entre endpoints compartilhados (Serverless) e Dedicated AI Clusters.
- **Resultado Esperado:** Uma tabela de parametrização ótima para cada caso de uso corporativo típico cobrado no exame.

---

### Dia 2: Prompt Engineering Especializado para Modelos OCI
- **Prioridade:** **Crítica**
- **Tempo Estimado:** **60 minutos** (15m teoria | 35m prática | 10m validação)
- **Melhorias Aplicadas:** Adaptação da engenharia de prompt clássica às especificidades da API do Cohere Command (diferença entre endpoint `/chat` com preâmbulo de sistema e `/generate`).
- **Atividade Prática:**
  1. Estruturar um prompt de classificação e extração usando o framework **CIOF** do kit.
  2. Implementar técnica Few-Shot com 3 exemplos de extração de termos contratuais.
  3. Adicionar restrições de formato estrito (JSON) e avaliar o comportamento do modelo frente a entradas incompletas.
- **Resultado Esperado:** Prompt no padrão corporativo da Oracle com 100% de precisão de extração e ausência de alucinações.

---

### Dia 3: Embeddings & Oracle AI Vector Search (Database 23ai)
- **Prioridade:** **Alta**
- **Tempo Estimado:** **60 minutos** (15m teoria | 35m prática | 10m validação)
- **Melhorias Aplicadas:** Compreensão prática de como o modelo *Cohere Embed v3* gera vetores densos e como o Oracle Database 23ai armazena e consulta vetores nativamente.
- **Atividade Prática:**
  1. Analisar como funciona a dimensão de embeddings (ex: 1024 dimensões no Cohere Embed v3) e os tipos de entrada (`search_document` vs `search_query`).
  2. Escrever a estrutura de uma tabela SQL no Oracle 23ai utilizando a coluna nativa `VECTOR`:
     ```sql
     CREATE TABLE documentos_bancarios (
         id NUMBER PRIMARY KEY,
         conteudo CLOB,
         vetor_embedding VECTOR(1024, FLOAT32)
     );
     ```
  3. Estruturar uma query utilizando funções de distância como `VECTOR_DISTANCE(..., COSINE)`.
- **Resultado Esperado:** Script SQL com modelagem e consulta vetorial completa compreendida para as questões da prova.

---

### Dia 4: Arquitetura RAG (Retrieval-Augmented Generation) no OCI
- **Prioridade:** **Crítica**
- **Tempo Estimado:** **60 minutos** (15m teoria | 35m prática | 10m validação)
- **Melhorias Aplicadas:** Mapeamento arquitetural do fluxo completo de RAG corporativo para responder às questões sobre mitigação de alucinação e frescor de dados sem necessidade de retreinamento.
- **Atividade Prática:**
  1. Projetar o fluxo de RAG no OCI:
     - Documentos brutos (Object Storage) → Processamento de texto e Chunking;
     - Geração de embeddings (OCI GenAI Service - Cohere Embed);
     - Armazenamento vetorial (Oracle Database 23ai ou OCI Search with OpenSearch);
     - Consulta do usuário → Vetorização da query → Busca top-k → Aumento do prompt → Resposta final fundamentada.
  2. Criar o prompt mestre do RAG que força o modelo a citar fontes e proíbe invenção de dados ausentes.
- **Resultado Esperado:** Diagrama de fluxo e prompt de ancoragem (*grounding*) validado para a arquitetura OCI.

---

### Dia 5: OCI Generative AI Agents & Knowledge Bases
- **Prioridade:** **Crítica**
- **Tempo Estimado:** **60 minutos** (15m teoria | 35m prática | 10m validação)
- **Melhorias Aplicadas:** Domínio do serviço totalmente gerenciado **OCI GenAI Agents**, que orquestra RAG de ponta a ponta sem necessidade de código complexo de pipeline.
- **Atividade Prática:**
  1. Estudar os componentes de um agente no OCI: *Agent*, *Knowledge Base*, *Data Source* (Object Storage) e *Runtime Session*.
  2. Mapear o ciclo de vida da sessão e como o agente preserva contexto multi-turn.
  3. Definir regras de moderação de conteúdo e permissões de segurança de acesso aos dados empresariais.
- **Resultado Esperado:** Especificação de configuração de um agente OCI de suporte com mitigação de riscos operacionais.

---

### Dia 6: Fine-Tuning no OCI (LoRA, T-Few) e Clusters Dedicados
- **Prioridade:** **Alta**
- **Tempo Estimado:** **60 minutos** (15m teoria | 35m prática | 10m validação)
- **Melhorias Aplicadas:** Clareza técnica e financeira sobre quando a Oracle recomenda Fine-Tuning vs. Engenharia de Prompt / RAG.
- **Atividade Prática:**
  1. Comparar as técnicas de Fine-Tuning com eficiência de parâmetros suportadas no OCI:
     - **T-Few:** Ajusta apenas frações mínimas de pesos para tarefas específicas de classificação;
     - **LoRA (Low-Rank Adaptation):** Insere matrizes de decomposição de baixo posto nos blocos de atenção.
  2. Preparar um modelo de arquivo de dataset em formato `JSONL` exigido pelo OCI:
     ```json
     {"prompt": "Classifique o risco do crédito: Cliente com score 850 e renda comprovada.", "completion": "Risco: Baixo."}
     ```
  3. Mapear o dimensionamento mínimo de Dedicated AI Clusters (mínimo de unidades de GPU para treinamento e hospedagem).
- **Resultado Esperado:** Matriz de decisão consolidada para o exame: "Quando usar Prompt vs RAG vs Fine-Tuning".

---

### Dia 7: Segurança, Governança IAM e Simulado Oficial
- **Prioridade:** **Crítica**
- **Tempo Estimado:** **60 minutos** (15m teoria | 35m prática | 10m validação)
- **Melhorias Aplicadas:** Domínio das garantias de privacidade da Oracle (os dados do cliente nunca são usados para retreinar modelos da Oracle ou de terceiros) e simulação de questões oficiais.
- **Atividade Prática:**
  1. Revisar as políticas de Identity and Access Management (IAM):
     ```text
     Allow group DataScientists to manage generative-ai-family in tenancy
     Allow group GenAIUsers to use generative-ai-family in compartment Analytics
     ```
  2. Resolver 15 questões no formato oficial da prova (múltipla escolha e cenários de caso de uso).
  3. Aplicar o checklist `03-checklists/01-pare-confira-use.md` para checar cada questão que envolveu custos ou escolha arquitetural.
- **Resultado Esperado:** Índice de acertos no simulado superior a 85% e domínio dos critérios de aprovação na certificação.
