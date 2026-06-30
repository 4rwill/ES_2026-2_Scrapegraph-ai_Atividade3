
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
* **Responsáveis:** 
* **O que fez:** 
* **Onde procurou as informações:** 

### 2. Eixo B: Qualidade Técnica dos Testes
* **Responsáveis:** Eduardo Ferreira e Eduardo Curcino 
* **O que fez:** Conduzizam a auditoria forense do Eixo B, focada na Qualidade Técnica dos Testes. Mantendo o rigor metodológico do tripé "Evidência, Análise Crítica e Risco", aplicaram uma análise profundA sobre a suíte de testes automatizados do sistema. A investigação focou em diagnosticar três vulnerabilidades estruturais: a fragilidade das validações lógicas frente a retornos estocásticos (Asserções Fracas), a ausência de testes de resiliência e tratamento de falhas externas (Ilusão do Caminho Feliz), e o mascaramento de defeitos arquiteturais por meio de simulações engessadas (Tautologia por Mocks Excessivos). O trabalho resultou na elaboração de um diagnóstico clínico que comprova a atual incapacidade da suíte em reter software defeituoso antes da produção.
* **Onde procurou as informações:** As evidências técnicas foram mapeadas diretamente no código-fonte, por meio da inspeção detalhada do diretório tests/ do repositório. O rastreamento focou na anatomia dos testes de nós unitários e grafos de integração (especificamente nos arquivos test_generate_answer_node.py, test_smart_scraper_graph.py e test_fetch_node.py). A contextualização teórica e os critérios de validação utilizados na análise crítica foram fundamentados na literatura científica sobre testes em ambientes de IA (como os artigos "Evaluating large language models for software testing" e fundamentos de "Teste e Inspeção de Software"), ultrapassando métricas superficiais de cobertura de código.

  
### 3. Eixo C: Lacunas, Riscos e Falhas Potenciais
* **Responsáveis:** 
* **O que fez:** 
* **Onde procurou as informações:** 

### 4. Eixo D: Plano de Evolução da Qualidade
* **Responsáveis:** 
* **O que fez:** 
* **Onde procurou as informações:** 
