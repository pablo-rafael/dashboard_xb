# 📊 Xbox Game Pass — Dashboard de Assinaturas 2024

Dashboard de vendas desenvolvido em Excel para análise de desempenho de assinaturas do Xbox Game Pass, com foco em visualização de dados, segmentação de planos e evolução mensal de receita.

---

## 🗂️ Estrutura do Arquivo

O arquivo `dashboard_vendas.xlsx` é organizado em 4 abas:

| Aba | Descrição |
|---|---|
| `Assets` | Paleta de cores e elementos visuais da identidade Xbox |
| `Bases` | Base de dados bruta com todos os registros de assinantes |
| `Cálculos` | Dados agregados e KPIs que alimentam o dashboard |
| `Dashboard` | Painel visual com gráficos, tabelas e indicadores |

---

## 📁 Dados Utilizados

### Fonte
Arquivo: `base_de_dados.xlsx`  
Período coberto: **Janeiro a Dezembro de 2024**  
Total de registros: **295 assinantes**

### Colunas da Base (`Bases`)

| Coluna | Tipo | Descrição |
|---|---|---|
| `Subscriber ID` | Inteiro | Identificador único do assinante |
| `Name` | Texto | Nome do assinante |
| `Plan` | Texto | Plano contratado: `Core`, `Standard` ou `Ultimate` |
| `Start Date` | Data | Data de início da assinatura |
| `Auto Renewal` | Texto | Renovação automática ativa: `Yes` / `No` |
| `Subscription Price` | Número | Valor base do plano (R$) |
| `Subscription Type` | Texto | Periodicidade: `Monthly`, `Quarterly` ou `Annual` |
| `EA Play Season Pass` | Texto | Possui add-on EA Play: `Yes` / `No` |
| `EA Play Season Pass Price` | Número | Preço do add-on EA Play (R$) |
| `Minecraft Season Pass` | Texto | Possui add-on Minecraft: `Yes` / `No` |
| `Minecraft Season Pass Price` | Número | Preço do add-on Minecraft (R$) |
| `Coupon Value` | Número | Valor de desconto aplicado (R$) |
| `Total Value` | Número | Valor total pago pelo assinante (R$) |

### Lógica do `Total Value`
```
Total Value = Subscription Price + EA Play Price + Minecraft Price - Coupon Value
```

---

## 📈 KPIs e Métricas do Dashboard

| Indicador | Valor |
|---|---|
| Total de Assinantes | 295 |
| Receita Total | R$ 7.633 |
| Ticket Médio | R$ 25,87 |
| Taxa de Renovação Automática | ~50% |
| Assinantes com Minecraft Pass | 194 (66%) |
| Assinantes com EA Play Pass | 98 (33%) |
| Assinantes com Cupom | 244 (83%) |

---

## 🥧 Segmentações Analisadas

### Por Plano
| Plano | Assinantes | Receita (R$) | % da Base |
|---|---|---|---|
| Core | 101 | 444 | 34,2% |
| Standard | 96 | 1.801 | 32,5% |
| Ultimate | 98 | 5.388 | 33,2% |

### Por Tipo de Assinatura
| Tipo | Assinantes | Receita (R$) |
|---|---|---|
| Monthly | 139 | 3.571 |
| Quarterly | 85 | 2.308 |
| Annual | 71 | 1.754 |

---

## 🛠️ Como Reproduzir

### Pré-requisitos
- Microsoft Excel 2016 ou superior (recomendado para suporte completo a gráficos)
- Python 3.8+ com as bibliotecas abaixo (caso queira regenerar via script)

```bash
pip install pandas openpyxl
```

### Passo a Passo

**1. Clone ou baixe os arquivos**
```
base_de_dados.xlsx   ← arquivo de dados brutos
build_dashboard.py   ← script de geração do dashboard
```

**2. Execute o script Python**
```bash
python build_dashboard.py
```
O arquivo `dashboard_vendas.xlsx` será gerado na mesma pasta.

**3. Abra no Excel**
- Navegue até a aba **Dashboard** para a visão completa
- A aba **Cálculos** contém todas as agregações intermediárias
- A aba **Bases** preserva os dados originais sem alteração

### Atualizar com Novos Dados

Para atualizar o dashboard com uma nova base:

1. Substitua os dados na aba `Bases` mantendo a mesma estrutura de colunas
2. Execute novamente o script `build_dashboard.py`, **ou**
3. Atualize manualmente as agregações na aba `Cálculos` — os gráficos se recalculam automaticamente

---

## 🎨 Identidade Visual

O dashboard segue a paleta de cores oficial do Xbox Game Pass, definida na aba `Assets`:

| Cor | Hex | Uso |
|---|---|---|
| Verde Escuro | `#1A5C1A` | Headers, títulos, fundo principal |
| Verde Médio | `#22C55E` | Subtítulos, bordas de seção |
| Verde Claro | `#9BC848` | Totais, destaques secundários |
| Menta | `#2AE6B1` | Acentos, cabeçalhos de tabela |
| Card Background | `#F0F7F0` | Fundo dos cards de KPI |

---

## 📌 Observações

- Os meses de **janeiro e fevereiro** contêm apenas 2 registros cada, sendo considerados fora do período de análise completa nos gráficos de evolução mensal.
- O mês de **dezembro** foi registrado apenas até o dia 16, sendo tratado como mês parcial.
- Os gráficos de evolução utilizam o intervalo **março a novembro** como base representativa.

---

*Projeto desenvolvido como desafio de visualização de dados em Excel*
