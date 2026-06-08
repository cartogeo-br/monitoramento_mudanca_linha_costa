# 🌊 Monitoramento de Mudanças em Linhas de Costa (Litoral do RJ)

Uma aplicação web interativa, leve e responsiva para visualização e análise espacial de dinâmicas costeiras (Erosão e Progradação) nos municípios do Rio de Janeiro. O sistema consome dados geoespaciais e consolida indicadores socioambientais críticos em tempo real.

---

## 🚀 Funcionalidades Principais

* **Mapa Interativo Multi-Basemap:** Alternância fluida entre visualização vetorial (OpenStreetMap) e imagens de satélite (Esri World Imagery) via Leaflet.
* **Filtros Dinâmicos:** Cruzamento instantâneo de dados por tipo de fenômeno dinâmico e por município.
* **Painel de KPIs Socioambientais:** Cálculo agregado em tempo real do impacto em:
    * População estimada e total de domicílios afetados.
    * Áreas de ecossistemas sensíveis (Mangue e Restinga em hectares).
* **Análise de Vetores Costeiros:** Renderização inteligente de feições espaciais com espessura otimizada e comportamento *hover/click* para detalhamento de atributos.
* **Exportação de Dados:** Motor nativo para download dos dados filtrados diretamente em formato CSV.
* **Fallback Flexível de Dados:** Suporte integrado para carregamento automático via API/Fetch local ou via Upload manual de arquivos GeoJSON.

---

## 🛠️ Tecnologias Utilizadas

O projeto foi desenvolvido sob a filosofia *Single Page Application (SPA)* vanilla, garantindo alta performance sem dependências pesadas de frameworks:

* **HTML5 & CSS3:** Estrutura semântica com layout responsivo baseado em *Flexbox* e *CSS Grid*, adaptando-se de monitores UltraWide a dispositivos móveis.
* **JavaScript (ES6+):** Lógica de manipulação de estados, filtragem de arrays geográficos e normalização de chaves de atributos (*fuzzy matching* de propriedades do GeoJSON).
* **Leaflet.js (v1.9.4):** Biblioteca de mapeamento de código aberto para renderização de geometrias espaciais.
* **Design System:** Tipografia profissional com as fontes *Source Sans 3* e *Source Code Pro*.

---

## 📂 Estrutura de Dados Suportada

O ecossistema consome um arquivo estruturado `lc_cidades_rj.geojson`. O algoritmo possui um mapeamento adaptativo (*Field Map*) capaz de identificar e normalizar os seguintes atributos geográficos, independentemente de estarem grafados com acentos ou em inglês:

* `ano` (ou `year`)
* `cidade` (ou `municipio`, `name`)
* `fenomeno` (Mapeia e estiliza automaticamente classes de *Erosão* e *Progradação*)
* `distancia_km`
* `domicilios`, `pop_est`
* `mangue_ha`, `restringae_ha`

---

## 🔧 Como Executar o Projeto

Como o projeto faz requisições assíncronas para ler o arquivo GeoJSON local, as políticas de segurança do navegador (CORS) bloqueiam a execução direta via protocolo `file://`. Utilize uma das abordagens abaixo:

### Opção 1: Servidor Local Rápido (Recomendado)
Certifique-se de ter o Python instalado, navegue até a pasta do projeto e execute:

```bash
# Python 3.x
python -m http.server 8000
