# Âncora

## Problema do Anti-Padrão

A âncora é um pedaço de software ou hardware que não tem nenhum propósito útil ao projeto atual. Frequentemente, a âncora é uma aquisição onerosa, que torna a compra ainda mais irônica.

*A Boat Anchor is a piece of software or hardware that serves no useful purpose on the current project. Often, the Boat Anchor is a costly acquisition, which makes the purchase even more ironic.*

As razões para aquisição da âncora geralmente são atraentes no momento. Por exemplo, a política ou uma ligação programática requer a compra e o uso de um pedaço particular de hardware ou software. Este é o pressuposto inicial (ou restrição) para o projeto de software. Outra razão é quando um gerente chave está convencido da utilidade desta aquisição.

*The reasons for acquiring a Boat Anchor are usually compelling at the time. For example, a policy or programmatic relationship may require the purchase and usage of a particular piece of hardware or software. This is a starting assumption (or constraint) of the software project. Another compelling reason is when a key manager is convinced of the utility of the acquisition.*

Uma pratica de venda chamada "pessoa muito importante (_VIP_) marketing" tem como alvo tomadores de decisão senior que tem autoridade para compra. _VIP marketing_ geralmente tem como foco gerentes executivos de pequenas - a média - corporações. Um comitê para o produto é feito sem uma avaliação técnica apropriada.

*A sales practice called "very important person (VIP) marketing" targets the sales pitch at senior decision makers who have buying authority. VIP marketing often focuses on chief executive officers of small- to medium-size corporations. A commitment to the product is made without proper technical evaluation.*

![](https://sourcemaking.com/files/sm/images/anchor.jpg)

As consequências para gerentes e desenvolvedores de software resultam em um esforço significante para fazer o produto funcionar.

*The consequences for managers and software developers are that significant effort may have to be devoted to making the product work.*

Após um investimento significante de tempo e recursos, o pessoal técnico percebe que o produto é inútil no contexto atual, e abandonam para outra abordagem técnica. Eventualmente, a Âncora é deixada de lado e acumula poeira em algum canto (se for hardware).

*After a significant investment of time and resources, the technical staff realizes that the product is useless in the current context, and abandons it for another technical approach. Eventually, the Boat Anchor is set aside and gathers dust in some corner (if it's hardware).*

## Solução Refatorada

Boas práticas de engenharia incluem a provisão de um _backup_ técnico, uma abordagem alternativa pode ser instituindo um mínimo de retrabalho de software. A escolha do _backup_ técnico uma importante estratégia de redução de riscos.

*Good engineering practice includes the provision for technical backup, an alternative approach that can be instituted with minimal software rework. The selection of technical backup is an important risk-mitigation strategy.*

_Backups_ técnicos devem ser identificados para a maioria de tecnologias de infraestrutura (dos quais a maiora dos softwares dependem), e para outras tecnologias em áreas de alto risco. _Backups_ técnicos 

*Technical backups should be identified for most infrastructure technologies (upon which most software depends), and for other technologies in high-risk areas. Technical backups should be evaluated along with critical-path technologies in the selection process. Prototyping with evaluation licenses (available from most vendors) is recommended for both critical-path and back-up technologies.*

## AntiPadrões Relacionados

*Rational decision making is explained in the solution to the Irrational Management AntiPattern. Rational decision making can be used as an objective technology selection process to identify Boat Anchors prior to acquisition. The solution to the Smoke and Mirrors AntiPattern describes the practices for prepurchase technology evaluation, including review of product documentation and train-before-you-buy.*
