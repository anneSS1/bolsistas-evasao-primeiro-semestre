# Bolsa de estudos e evasão entre estudantes com insucesso acadêmico no primeiro semestre

Código e notebook do artigo *Associação entre condição de bolsista e evasão entre estudantes com insucesso acadêmico no primeiro semestre*, desenvolvido na disciplina de Pesquisa Acadêmica (UFSCar Sorocaba, 2026).

**Autores:** Anne Mari Suenaga Sakai, Bianca Ribeiro Barros e Pedro Henrique Pereira Machado.

[![Abrir no Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/anneSS1/bolsistas-evasao-primeiro-semestre/blob/main/bolsistas-evasao.ipynb)

## Pergunta de pesquisa

Entre alunos que se matricularam em pelo menos uma disciplina no 1º semestre e não foram aprovados em todas, ter bolsa (`Scholarship holder`) está associado a uma menor taxa de abandono do curso (`Abandonou`)?

O estudo é observacional: os resultados indicam associação, e não causalidade.

## Dados

- **Conjunto:** *Predict Students' Dropout and Academic Success*, UCI Machine Learning Repository, conjunto 697.
- **DOI:** [10.24432/C5MC89](https://doi.org/10.24432/C5MC89)
- **Licença dos dados:** Creative Commons Attribution 4.0 International (CC BY 4.0).
- **Tamanho:** 4.424 alunos de uma instituição de ensino superior portuguesa; o grupo estudado tem 2.516 alunos.

Os dados não estão neste repositório: o notebook os baixa diretamente da UCI com o pacote `ucimlrepo`, sem nenhuma alteração manual.

**Como citar os dados:**

> REALINHO, V.; VIEIRA MARTINS, M.; MACHADO, J.; BAPTISTA, L. *Predict students' dropout and academic success*. UCI Machine Learning Repository, 2021. DOI: 10.24432/C5MC89.

## Conteúdo do repositório

| Arquivo | Descrição |
|---|---|
| `bolsistas-evasao.ipynb` | Notebook com todo o código, as tabelas, os gráficos e a interpretação dos resultados, já executado |
| `README.md` | Este arquivo |

## Como reproduzir

1. Clique em **Abrir no Colab**, acima, ou abra `bolsistas-evasao.ipynb` no [Google Colab](https://colab.research.google.com/).
2. No menu, escolha **Ambiente de execução → Executar tudo**.
3. A primeira célula de código instala o pacote `ucimlrepo`; as demais carregam os dados e refazem toda a análise.

Todos os sorteios usam a semente fixa `SEMENTE = 2026`, definida na seção 1 do notebook. Com as versões abaixo, os números devem ser iguais aos do artigo.

**Ambiente usado:**

| Ferramenta | Versão |
|---|---|
| Python | 3.13.18 |
| NumPy | 2.4.6 |
| pandas | 2.2.3 |
| SciPy | 1.16.3 |
| Matplotlib | 3.10.0 |
| scikit-learn | 1.6.1 |
| ucimlrepo | 0.0.7 |

## Etapas da análise

| Seção do notebook | O que faz |
|---|---|
| 1. Preparação | Bibliotecas, versões e semente |
| 2. Carregar os dados | Download da UCI e descrição das colunas |
| 3. Análise exploratória | Distribuição de `Target`, checagens de qualidade e correlações para escolher os fatores de controle |
| 4. Recorte | Seleção do grupo estudado (2.516 alunos, 426 bolsistas) |
| 5. Estatística descritiva | Tabela de contingência e taxas de abandono por bolsa |
| 6. Teste de hipótese | Qui-quadrado, razão de chances bruta e verificação sem os alunos `Enrolled` |
| 7. Bootstrap | 1.000 reamostragens da diferença entre as taxas |
| 8. Controle de fatores | Análise estratificada em 10 subgrupos (qui-quadrado ou Fisher, com Bonferroni) |
| 9. Modelo de classificação | Regressão logística com e sem bolsa em 100 separações treino/teste, teste t corrigido de Nadeau e Bengio e razão de chances ajustada com bootstrap |

## Código baseado em

- HANJI, S. *Predicting student dropout using machine learning*. Medium, 2024 (modelo de classificação).
- SCIKIT-LEARN DEVELOPERS. *Statistical comparison of models using grid search* (teste t corrigido).
- PAYONG, A.; MUKHERJEE, S. *Mastering logistic regression with scikit-learn: a complete guide*. DigitalOcean, 2025 (razão de chances).
- BROWNLEE, J. *How to calculate bootstrap confidence intervals for machine learning results in Python*. Machine Learning Mastery, 2020 (bootstrap).

As referências completas estão na última seção do notebook.
