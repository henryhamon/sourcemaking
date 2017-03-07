# Âncora

## Problema do Anti-Padrão

A âncora é um pedaço de software ou hardware que não tem nenhum propósito útil ao projeto atual. Frequentemente, a âncora é uma aquisição onerosa, que torna a compra ainda mais irônica.

As razões para aquisição da âncora geralmente são atraentes no momento. Por exemplo, a política ou uma ligação programática requer a compra e o uso de um pedaço particular de hardware ou software. Este é o pressuposto inicial (ou restrição) para o projeto de software. Outra razão é quando um gerente chave está convencido da utilidade desta aquisição.

Uma pratica de venda chamada "pessoa muito importante (_VIP_) marketing" tem como alvo tomadores de decisão senior que tem autoridade para compra. _VIP marketing_ geralmente tem como foco gerentes executivos de pequenas - a média - corporações. Um comitê para o produto é feito sem uma avaliação técnica apropriada.

![](https://sourcemaking.com/files/sm/images/anchor.jpg)

As consequências para gerentes e desenvolvedores de software resultam em um esforço significante para fazer o produto funcionar.

Após um investimento significante de tempo e recursos, o pessoal técnico percebe que o produto é inútil no contexto atual, e abandonam para outra abordagem técnica. Eventualmente, a Âncora é deixada de lado e acumula poeira em algum canto (se for hardware).

## Solução Refatorada

Boas práticas de engenharia incluem a provisão de um _backup_ técnico, uma abordagem alternativa pode ser instituindo um mínimo de retrabalho de software. A escolha do _backup_ técnico uma importante estratégia de redução de riscos.

_Backups_ técnicos devem ser identificados para a maioria de tecnologias de infraestrutura (dos quais a maiora dos softwares dependem), e para outras tecnologias em áreas de alto risco. Os _backups_ técnicos devem ser avaliados juntamente com as tecnologias críticas no processo de seleção. A prototipagem com licenças de avaliação (disponível na maioria dos fornecedores) é recomendada para tecnologias de críticas e de tecnologias de _back-up_.

## AntiPadrões Relacionados

Fazer decisões racionais é explanado na solução do _Irrational Management AntiPattern_. Fazer decisões racionais pode ser usada no objetivo do processo de seleção de tecnologias para identificar Âncoras e priorizar a aquisição. A solução do _the Smoke and Mirrors AntiPattern_ descreve as práticas de précompra de tecnologia para avaliação, incluindo o _review_ da documentação do produto e o treine-antes-de-comprar.
