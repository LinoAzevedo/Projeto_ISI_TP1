# CO2Drive Analytics — Vendas × Emissões de CO₂ (KNIME)

**Objetivo:** calcular e analisar a **emissão média de CO₂ ponderada pelas vendas** (24 meses), por marca/modelo/combustível, com um pipeline **KNIME → BD → (opcional) dashboard**.

## Estrutura
```
co2drive-analytics/
├─ knime/                     # workflows .knwf (importa no KNIME)
├─ data/
│  ├─ raw/                    # fontes originais (CSV/JSON/XML/YAML)
│  ├─ staged/                 # dados após limpeza/normalização
│  └─ warehouse/              # extratos para dashboard
├─ db/                        # DDL schema estrela
├─ dashboards/                # Node-RED ou HTML simples
├─ scripts/                   # utilitários (ex.: geração de dados)
├─ logs/                      # logs do ETL
└─ docs/
   ├─ relatorio/              # relatório final (PDF)
   └─ video/                  # vídeo + QR
```

## Dados de exemplo
- `data/raw/car_specs.csv` — specs por modelo (CO₂, NOx, Euro, combustível…)
- `data/raw/sales.csv` — vendas mensais por modelo (24 meses)
- `data/raw/fuel_mapping.json` — mapeamento de combustíveis (EV/PHEV/…)
- `data/raw/regulatory_limits.xml` — limites por Euro/fuel (exemplo)
- `data/raw/segments.yaml` — segmentos (exemplo)

> Substitui por dados reais quando tiveres. Os formatos foram escolhidos para cumprir diversidade (CSV/JSON/XML/YAML) e integração via HTTP.

## KPIs
- **CO₂ médio ponderado por vendas** (mensal, por marca/segmento).
- Mix de vendas por **combustível**.
- Top modelos que mais sobem/baixam a média de CO₂.

## Passos rápidos
1. **BD**: cria o schema com [`db/ddl.sql`](db/ddl.sql) no PostgreSQL/MySQL.
2. **KNIME**: cria um workflow com:
   - `CSV Reader` (car_specs, sales) + `JSON Reader` (ou `GET Request`) p/ `fuel_mapping.json`
   - `XML Reader` p/ `regulatory_limits.xml`
   - Limpeza com `String Manipulation (Regex)` e `Column Expressions`
   - `Joiner` para cruzar vendas↔specs; calcular KPIs com `Math Formula`
   - Escrever dimensões e factos com `DB Writer`
   - Encadear no `Try/Catch` e gravar logs em `logs/`
3. (Opcional) **Dashboard**: exporta agregados para `data/warehouse/` e usa Node-RED/HTML.

## GitHub — como publicar
```bash
git init
git add .
git commit -m "Initial commit: KNIME CO2Drive Analytics scaffold"
git branch -M main
# cria o repo vazio no GitHub com este mesmo nome (via UI ou GitHub CLI)
git remote add origin https://github.com/<teu-utilizador>/co2drive-analytics.git
git push -u origin main
```

## Licença
MIT — vê [`LICENSE`](LICENSE).
