# pedidos-service - Diagrama C4 de Componentes (nível 3)

![Diagrama de Componentes](pedidos-componentes.png)

Fonte: `pedidos-componentes.puml` (C4-PlantUML).

## ADR-009: qual componente garante e por que um quarto meio de pagamento não altera a criação de pedidos

- O ADR-009 é garantido pela interface **EstrategiaPagamento** (padrão Strategy), junto com o **RegistroEstrategiasPagamento**.
- **CriarPedidoService** depende só dessa interface, e não de cartão, Pix ou vale-refeição (DIP).
- Um quarto meio exige apenas uma nova classe que implemente a interface, registrada no Registro.
- **CriarPedidoService** não muda, pois não conhece nenhuma estratégia concreta: aberto à extensão e fechado à modificação (OCP).
