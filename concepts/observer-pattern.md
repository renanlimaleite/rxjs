# Observer Pattern

> O padrão Observer é um padrão de projeto comportamental que permite que você defina um mecanismo de assinatura para notificar múltiplos objetos sobre quaisquer eventos que aconteçam com o objeto que eles estão observando. O padrão Observer define uma dependência de um para muitos (1 para n) entre objetos de modo que quando um objeto (Observável) muda de estado, todos os seus dependentes (Observadores) sejam notificados e atualizados automaticamente.

Uma analogia comum para o padrão Observer é a de uma editora de jornais (Observável) e seus assinante (Observadores). A editora é o objeto observado e os assinantes são os objetos observadores. Quando a editora publica um novo jornal, todos os assinantes recebem uma cópia automaticamente.