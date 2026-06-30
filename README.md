
# Auditoria de Testes de Software e Plano de Evolução da Qualidade

**Disciplina:** Engenharia de Software  
**Projeto Analisado:** [Scrapegraph-ai](https://github.com/ScrapeGraphAI/Scrapegraph-ai)  
**Auditoria Técnica (Vídeo):** 
 

## Integrantes:
* ARTHUR SOARES SANTANA (202400051087)
* ARTUR JOSÉ SOARES SANTOS (202400072372)
* ANGELO DE SOUSA MUTTI (202100045555)
* CHRISTIAN WILL SILVA SANTOS NUNES (202400050796)
* EDUARDO FERREIRA BOMFIM FILHO (202400050811)
* EDUARDO CURCINO MONTEIRO FILHO (202400051102)
* IURI MAURICIO MAIA PEREIRA (202400051120)
* RIAN PURIFICAÇÃO DE OLIVEIRA (202400051013)

---

## Detalhamento das Contribuições por Eixo

### 1. Eixo A: Estratégia Atual de Testes
* **Responsáveis:** Rian P e Christian Will
* **O que fez:** Conduziram a investigação técnica do Eixo A, focada no mapeamento e análise da Estratégia Atual de Testes do sistema. Mantendo o rigor metodológico baseado em evidências empíricas no código-fonte, realizaram um diagnóstico forense da infraestrutura de qualidade. A auditoria abrangeu a organização estrutural das suítes de testes, a identificação empírica dos níveis de teste efetivamente implementados (unitários, integração e performance) e a avaliação do processo de automação e integração contínua (CI/CD). A investigação focou em diagnosticar lacunas operacionais, revelando vulnerabilidades significativas na esteira de qualidade: uma grave divergência entre a maturidade descrita na documentação teórica e a fragilidade da implementação real, a ausência de rastreamento de cobertura de código no pipeline, e a existência de um processo de release desprovido de quality gates 
* **Onde procurou as informações:** As evidências técnicas foram extraídas por meio da inspeção detalhada da arquitetura do repositório e de seus arquivos de configuração. O rastreamento concentrou-se na análise anatômica do diretório `tests/` (verificando a distribuição de grafos, nós, utilitários e fixtures compartilhadas no `conftest.py`) e nos parâmetros de execução definidos no `pytest.ini` e `Makefile`.

### 2. Eixo B: Qualidade Técnica dos Testes
* **Responsáveis:** Eduardo Ferreira e Eduardo Curcino 
* **O que fez:** Conduzizam a auditoria forense do Eixo B, focada na Qualidade Técnica dos Testes. Mantendo o rigor metodológico do tripé "Evidência, Análise Crítica e Risco", aplicaram uma análise profundA sobre a suíte de testes automatizados do sistema. A investigação focou em diagnosticar três vulnerabilidades estruturais: a fragilidade das validações lógicas frente a retornos estocásticos (Asserções Fracas), a ausência de testes de resiliência e tratamento de falhas externas (Ilusão do Caminho Feliz), e o mascaramento de defeitos arquiteturais por meio de simulações engessadas (Tautologia por Mocks Excessivos). O trabalho resultou na elaboração de um diagnóstico clínico que comprova a atual incapacidade da suíte em reter software defeituoso antes da produção.
* **Onde procurou as informações:** As evidências técnicas foram mapeadas diretamente no código-fonte, por meio da inspeção detalhada do diretório tests/ do repositório. O rastreamento focou na anatomia dos testes de nós unitários e grafos de integração (especificamente nos arquivos test_generate_answer_node.py, test_smart_scraper_graph.py e test_fetch_node.py). A contextualização teórica e os critérios de validação utilizados na análise crítica foram fundamentados na literatura científica sobre testes em ambientes de IA (como os artigos "Evaluating large language models for software testing" e fundamentos de "Teste e Inspeção de Software"), ultrapassando métricas superficiais de cobertura de código.

  
### 3. Eixo C: Lacunas, Riscos e Falhas Potenciais
* **Responsáveis:** Iuri Mauricio e Ângelo Mutti
* **O que fez: Conduziram a auditoria forense do Eixo C, focada nas Lacunas, Riscos e Falhas Potenciais do ecossistema. Mantendo o rigor metodológico do formato "Evidência, Diagnóstico, Risco e Recomendação", aplicaram uma investigação aprofundada sobre as fragilidades e as áreas descobertas da atual estratégia de validação do sistema. A análise focou em mapear vulnerabilidades estruturais críticas que escapam da atual suíte de testes: a total inexistência de testes semânticos balizados por gabaritos de referência (Ground Truth), a alta probabilidade de regressões em cascata motivada por forte acoplamento e violações arquiteturais no núcleo (God Objects e Vendor Lock-in), e a dependência nociva e não isolada de chamadas reais a APIs de Inteligência Artificial em etapas de integração. O trabalho culminou em um diagnóstico clínico que mapeia de forma incontestável os graves riscos operacionais, arquiteturais e financeiros atrelados à atual cobertura do projeto.**
* **Onde procurou as informações: As evidências técnicas foram mapeadas diretamente pelo cruzamento da arquitetura central do repositório com o escopo do seu diretório tests/. O rastreamento forense mirou a anatomia do núcleo de instanciamento e dos nós de execução (especificamente apontando os gargalos em scrapegraphai/graphs/abstract_graph.py, scrapegraphai/nodes/fetch_node.py e na família generate_answer_node.py), confrontando-os com as limitações de seus respectivos arquivos de teste (como o tests/integration/test_multi_graph_integration.py e test_batch_api.py). A contextualização teórica e os critérios de análise de risco foram fundamentados nas restrições de qualidade estipuladas por padrões de projeto (SOLID e Design Patterns do GoF), além de métricas essenciais para V&V (Verificação e Validação) de sistemas estocásticos guiados por IA, como isolamento via Record-and-Replay e mitigação de alucinações.**

### 4. Eixo D: Plano de Evolução da Qualidade
* **Responsáveis:** 
* **O que fez:** 
* **Onde procurou as informações:** 
