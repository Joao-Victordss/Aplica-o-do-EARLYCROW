<br />

<div align="center">
  <a href="https://github.com/ICL-ml4csec/EarlyCrowAPT">
    &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;<img src="https://raw.githubusercontent.com/ICL-ml4csec/EarlyCrowAPT/main/EarlyCrow_logo.png" class="center"  width="700" height="148.75">
  </a>

  </p>
</div>





## Sobre

Ameaças Persistentes Avançadas (APTs) estão entre as ameaças mais sofisticadas enfrentadas por organizações críticas no mundo todo. APTs
empregam táticas, técnicas e procedimentos (TTPs) específicos, o que os torna mais difíceis de detectar em comparação com ataques
frequentes e agressivos. Sistemas de detecção de intrusão em redes frequentemente têm dificuldade em identificar comunicações de APT,
permitindo que essas ameaças permaneçam despercebidas em máquinas vítimas por meses ou até anos.

Neste trabalho apresentamos o EarlyCrow, uma abordagem para detectar conexões de Comando e Controle (C2) de malwares APT usando
sumários contextuais. O design do EarlyCrow é fundamentado em um modelo de ameaça que foca nos TTPs presentes no tráfego gerado por
ferramentas recentemente utilizadas em campanhas APT. O modelo destaca a importância do contexto em torno das conexões maliciosas e
aponta atributos de tráfego que ajudam na detecção de APTs. O EarlyCrow define um novo formato de fluxo de rede chamado PairFlow,
utilizado para construir o sumário contextual de uma captura PCAP, representando informações comportamentais, estatísticas e de
protocolo relevantes para os TTPs de APT. Avaliamos a efetividade do EarlyCrow em APTs não vistas, obtendo média macro-F1 de 93.02%
com FPR de 0.74%.

Se decidir usar este código ou os dados, por favor cite o artigo abaixo.

```
@inproceedings{alageel2022earlycrow,
  title={EarlyCrow: Detecting APT Malware Command and Control 
        Over HTTP(S) Using Contextual Summaries},
  author={Alageel, Almuthanna and Maffeis, Sergio},
  booktitle={International Conference on Information Security},
  pages={},
  year={2022},
  organization={Springer}
}
# EarlyCrowAPT — aplicação do repositório original

Este repositório contém uma cópia / adaptação local da aplicação EarlyCrow publicada em:

https://github.com/ICL-ml4csec/EarlyCrowAPT

Importante: este projeto NÃO é meu — é a aplicação do trabalho de Almuthanna Alageel e Sergio Maffeis.

Referência:

Alageel, Almuthanna and Maffeis, Sergio.
"EARLYCROW: Detecting APT Malware Command and Control over HTTP(S) Using Contextual Summaries".

Link do repositório original: https://github.com/ICL-ml4csec/EarlyCrowAPT

----

## O que eu atualizei aqui

- Substituí usos obsoletos de pandas (DataFrame.append) por alternativas compatíveis com pandas 2.x (usando `pd.concat` e acumulação de linhas).
- Não houve necessidade de alterar imports `from sklearn.externals import joblib` no código do projeto — não havia ocorrências fora do ambiente (`.venv`).
- Atualizei o arquivo `.gitignore` para não versionar `data/` e o ambiente virtual.
- Atualizei `requirements.txt` para incluir dependências necessárias para gerar os gráficos (matplotlib, seaborn).

Se for necessário, posso reverter/ajustar qualquer alteração — veja o histórico de commits antes de publicar.

## Requisitos e instalação

Este repositório foi testado com Python 3.10+ em um ambiente virtual. Atualizei o `requirements.txt` para incluir bibliotecas de visualização.

1) Criar e ativar um ambiente virtual (PowerShell):

```powershell
python -m venv .venv
.venv\Scripts\Activate
```

2) Instalar dependências:

```powershell
pip install -r requirements.txt
```

Observação: se ocorrerem erros de permissões ao criar o venv, feche programas que possam bloquear arquivos, ou execute o PowerShell como Administrador.

## Observações sobre `requirements.txt`

Atualizei `requirements.txt` para incluir bibliotecas de plotting que os scripts usam (por exemplo `matplotlib` e `seaborn`). Mantive as versões principais do projeto (numpy, pandas, scipy, scikit-learn, joblib, threadpoolctl) como no original.

Se desejar, posso congelar (pip freeze) as versões exatas num arquivo `requirements-lock.txt`.

## Uso rápido

Defina `PYTHONPATH` para a raiz do projeto (Windows PowerShell):

```powershell
$env:PYTHONPATH = (Get-Location).Path
```

Executar a geração de ContextualSummaries (opcional):

```powershell
python EarlyCrow/dataflow.py
```

Rodar os experimentos (exemplos):

```powershell
python experiments/measurements_study.py
python experiments/classification_performance_known_malware.py
python experiments/classification_performance_unseen_malware.py
```

Se estiver em um ambiente sem interface gráfica (headless), defina:

```powershell
$env:MPLBACKEND='Agg'
python experiments/measurements_study.py
```

## Dados

Este repositório não inclui dados grandes. Para reproduzir os experimentos a partir de PCAPs, siga as instruções em `data/README.md` e na pasta `EarlyCrow/PairFlow_data_format/` do repositório original.

Os arquivos de `ContextualSummaries` necessários para rodar os experimentos podem ser colocados em `data/contextual_summaries/`.

## Licença e atribuição

Este repositório contém código e dados derivados do trabalho dos autores citados. Respeite a licença original e cite o artigo quando reutilizar o código ou os dados.

----

Se quiser, eu:
- crio o commit com essas alterações e adiciono `.gitignore`; ou
- gero um `requirements-lock.txt` (freeze) para fixar versões; ou
- configuro Actions/CI simples para rodar lint/testes antes de push.

Diga qual passo você quer que eu execute agora.

  </a>

  </p>
</div>

<br />


#### Distribuição das Principais Features

Investigamos a importância das features no terceiro conjunto de dados em modo HTTPS, que compreende APTs, botnets e amostras legítimas,
por ser o cenário mais próximo de uma situação realista para detecção de APTs.

Para gerar a figura das principais features execute:

```powershell
python experiments/unseen_malware_top_features_distribution.py
```

<br />
<div align="center">
  <a href="https://github.com/ICL-ml4csec/EarlyCrowAPT/blob/main/experiments/unseen_malware_top_features_distribution.py">
    <img src="https://raw.githubusercontent.com/ICL-ml4csec/EarlyCrowAPT/main/experiments/figures/top_features_distribution.png" class="center" width="900" height="125">
  </a>

  </p>
</div>

<p align="right">(<a href="#top">voltar ao topo</a>)</p>
