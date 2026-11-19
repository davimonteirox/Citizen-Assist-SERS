# Citizen Assist AI | Luz para estudar

**Soluções em Energias Renováveis e Sustentáveis · Global Solution 2026.2**  
Davi Monteiro · RM 573290

## Para quem e para quê

Um estudante que usa a mesa de casa à tarde e à noite quer saber se vale trocar uma incandescente ainda em uso e aproximar a mesa de uma janela. O serviço a preservar é conseguir ler no mesmo local durante todo o período de estudo. A janela fornece luz solar diretamente. O LED complementa a iluminação quando necessário. O caso é ilustrativo, sem medição domiciliar.

## Executar

Baixe e extraia o repositório. Abra **index.html** em um navegador com **energia.js** na mesma pasta. Funciona offline, sem instalação ou chave de API. Altere as horas, dias, tarifa e preço. Selecione uma das quatro perguntas para consultar a recomendação, o retorno, o impacto ou o cálculo. As respostas são geradas por regras com os números da rotina atual.

## Dados e premissas

| Dado | Valor inicial | Origem e interpretação |
|---|---:|---|
| Fluxo luminoso nominal | 800 lm | Referência [1] para comparar fontes de luz elétrica equivalentes |
| Incandescente existente | 60 W | Tabela 2 de [1] |
| LED novo | 9 W | Dentro do intervalo de 5,9 a 10,5 W de [1], também exemplificado em [2] |
| Estudo | 4 h/dia, 20 dias/mês | Hipótese de quatro semanas com cinco dias de estudo |
| Luz natural útil | 2 h/dia | Hipótese de metade da sessão à tarde, com mesa próxima da janela. Substituir por observação local |
| Tarifa variável | R$ 1,00/kWh | Valor redondo para simulação. Usar o custo variável aplicável na fatura local |
| LED | R$ 15,00 | Orçamento hipotético de uma unidade, sem mão de obra. Substituir por cotação |
| Janela, mesa e luminária | Já disponíveis | Reposicionar a mesa e apagar a lâmpada manualmente. Sem reforma |

A eficácia luminosa nominal passa de 800/60 ≈ 13,3 para 800/9 ≈ 88,9 lm/W. O fluxo da lâmpada não determina sozinho a iluminância sobre o livro. Confirmar a adequação no plano da mesa, inclusive em dias nublados. Se o local já usa LED, a economia relevante vem apenas da redução das horas acesas.

## Memória de cálculo

Energia da rede (kWh) = potência (W) × horas acesas por dia × dias / 1.000. Custo variável = energia × tarifa. A última coluna inclui a compra do LED no primeiro mês.

| Opção | Conta mensal em kWh | Custo mensal | Investimento | Desembolso no 1º mês |
|---|---|---:|---:|---:|
| Incandescente existente | 60 × 4 × 20 / 1.000 = 4,80 | R$ 4,80 | R$ 0,00 | R$ 4,80 |
| A · LED da rede | 9 × 4 × 20 / 1.000 = 0,72 | R$ 0,72 | R$ 15,00 | R$ 15,72 |
| B · Luz solar direta + LED | 9 × (4 − 2) × 20 / 1.000 = 0,36 | R$ 0,36 | R$ 15,00 | R$ 15,36 |

A evita 4,08 kWh/mês (85%). B evita 4,44 kWh/mês (92,5%). Os percentuais usam a incandescente como base. Comparada apenas ao LED, a janela economiza mais 0,36 kWh ou R$ 0,36 por mês. A economia só incide sobre a parcela de iluminação estudada.

Retorno simples = investimento adicional / economia mensal. Para A, 15/4,08 ≈ 3,68 meses. Para B, 15/4,44 ≈ 3,38 meses. Em meses inteiros, ambas recuperariam o investimento durante o quarto mês se as premissas se mantivessem. O cálculo desconsidera juros, manutenção e mudanças de uso.

## Decisão e sensibilidade

- **Estudo à noite ou sem janela adequada.** A substituição por LED conserva o fluxo nominal e reduz a energia. Conferir tensão, soquete, distribuição da luz e preço antes da compra.
- **Estudo diurno e janela existente.** B tem o menor custo de operação do caso. Evitar reflexos na tela e sombras no livro. Se o ambiente ficar quente ou a luz cair, ajustar a cortina ou acender o LED. Uma reforma exigiria novo orçamento e cálculo.
- **Pouca luz natural.** Com apenas 1 h útil/dia, B consome 0,54 kWh/mês. Com 0 h, consome os mesmos 0,72 kWh de A. A comparação preserva as 80 horas mensais de leitura.
- **Impacto ambiental.** Menor demanda elétrica reduz o uso da rede. A opção solar passiva dispensa painel e bateria. Ambas exigem a fabricação de um LED e a destinação da lâmpada retirada. A análise contabiliza energia operacional e não estima o ciclo de vida nem emissões sem inventário e fator de emissão. Custos fixos da fatura permanecem fora da conta.

## Referências

1. U.S. Department of Energy. *Purchasing Energy-Efficient Light Bulbs*, tabela 2. https://www.energy.gov/cmei/femp/purchasing-energy-efficient-light-bulbs
2. U.S. Department of Energy. *Consumer Guide to Energy-Efficient Lighting*, seções sobre lúmens e iluminação natural. https://www.energy.gov/sites/default/files/2021-08/ES-EE%20Lighting_080921_0.pdf

## Testes

Veja TESTES.md para os cenários funcionais verificados e o protocolo de avaliação com estudantes.

Mantenha **calculo.js** junto de **energia.js** e **index.html**. O primeiro arquivo concentra as fórmulas usadas nas duas interfaces. Para reproduzir a demonstração em modo texto, com Node.js, execute `node consulta.cjs 2 1`. O primeiro argumento indica horas de sol útil na sessão de 4 h e o segundo seleciona a pergunta (1 a 4, na ordem dos botões). Rode `node testar.cjs` para verificar os resultados.
