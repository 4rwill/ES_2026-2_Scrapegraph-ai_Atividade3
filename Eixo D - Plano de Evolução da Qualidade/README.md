# Eixo D: Plano de Evolução da Qualidade

**Projeto:** Scrapegraph-ai  
**Disciplina:** Engenharia de Software  

---

## Evidências

As evidências abaixo fundamentam as prioridades e ações propostas no plano de qualidade. Os arquivos originais foram copiados para o diretório `evidencias/`.

| # | Evidência | Arquivo Original | Cópia |
|---|-----------|------------------|-------|
| E1 | Pipeline de CI executa apenas `pytest -m "unit or not integration"`, excluindo testes de integração e benchmarks | `.github/workflows/test-suite.yml` | `evidencias/test-suite.yml` |
| E2 | Workflow de release não depende do workflow de testes; publicação pode ocorrer com testes falhando | `.github/workflows/release.yml` | `evidencias/release.yml` |
| E3 | Cobertura configurada com `--cov-branch` e relatórios XML/HTML, mas sem threshold mínimo (`--cov-fail-under`) | `pytest.ini` | `evidencias/pytest.ini` |
| E4 | Sete marcadores personalizados: `integration`, `slow`, `llm_provider`, `requires_api_key`, `benchmark`, `unit`, `e2e` | `pytest.ini` | `evidencias/pytest.ini` |
| E5 | 21 arquivos de teste, 51 arquivos Python em `tests/` | `tests/` | — |
| E6 | Método `_create_llm` com 162 linhas e 12+ branches condicionais para 18 provedores; sem teste unitário dedicado | `scrapegraphai/graphs/abstract_graph.py` | `evidencias/abstract_graph.py` |
| E7 | Nenhum teste valida saída LLM contra gabarito esperado (Ground Truth) | `tests/` | — |
| E8 | Makefile com targets `lint`, `type-check`, `test` | `Makefile` | `evidencias/Makefile` |
| E9 | Pre-commit com 6 hooks: black, ruff, isort, trailing-whitespace, end-of-file-fixer, check-yaml | `.pre-commit-config.yaml` | `evidencias/pre-commit-config.yaml` |
| E10 | Ferramentas configuradas no pyproject.toml: Ruff (F/E/W/C), Black (88/py310), isort (black profile), Mypy (strict) | `pyproject.toml` | `evidencias/pyproject.toml` |

---

## Plano de Evolução da Qualidade

### 1. Priorização

**Prioridade 1 — Testes de Integração com Provedores LLM no CI.**  
Fundamento: E1 (pipeline exclui integração), E2 (release independe de testes).  
Ação: adicionar job de integração com segredos de ambiente e dependência no workflow de release.

**Prioridade 2 — Cobertura Substantiva em Módulos de Alta Complexidade.**  
Fundamento: E6 (`_create_llm` com 162 linhas e 12+ branches), E5 (apenas 21 arquivos de teste para 27 grafos).  
Ação: testes unitários com asserções de conteúdo para cada ramo condicional.

**Prioridade 3 — Testes de Validação Semântica contra Dados de Referência (Ground Truth).**  
Fundamento: E7 (ausência total de testes Ground Truth).  
Ação: criar dataset de páginas emparelhadas a gabaritos JSON/CSV e implementar testes de acurácia.

### 2. Camadas de Foco

- **Unidade** (E6, E8): reforçar asserções em nós e utilitários.
- **Contrato** (E10): validar schema de respostas LLM com Pydantic.
- **Regressão semântica** (E7): testar grafos completos contra gabaritos conhecidos.

### 3. Implantação Gradual (4 fases de 2 semanas)

1. Criar dataset Ground Truth + 5 testes semânticos (E7).
2. Reforçar asserções unitárias frágeis + testes para `_create_llm` (E6).
3. Job de integração no CI com segredos (E1, E2).
4. Threshold de cobertura e badge no README (E3).

### 4. Automação

**Ferramentas existentes** (E8, E9, E10): pytest-cov, ruff, black, isort, mypy, pre-commit.  
**Pipeline proposto:** job de integração no CI (E1), `--cov-fail-under=60` (E3), mutação semanal.  
**Política:** push para `main` → lint + type-check + unit + integration; releases → suíte completa + threshold.

### 5. Critérios de Sucesso

**Entrada:** dataset Ground Truth disponível (E7), job de integração configurado (E1), Codecov integrado.  
**Saída (3 meses):** 400 testes, cobertura ≥ 50%, 85% asserções fortes, 10 testes semânticos.  
**Saída (6 meses):** 550 testes, cobertura ≥ 65%, 25 testes semânticos, mutation score ≥ 75%, bloqueio de PRs que reduzam cobertura.
