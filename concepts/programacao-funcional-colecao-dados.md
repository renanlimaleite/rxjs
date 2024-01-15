# Functional programming with collections (programação funcional com coleções)

> "Functional Programming with Collections" refere-se à prática de utilizar programação funcional para manipular e transformar coleções de dados. Na programação funcional, os dados são tratados como imutáveis e as operações são realizadas por meio de funções puras, que não têm efeitos colaterais e sempre produzem o mesmo resultado para os mesmos argumentos.

A manipulação de coleções é uma parte fundamental da programação de muitos aplicativos. Em um contexto funcional, o foco é em operações de alto nível que são aplicadas à coleção como um todo, muitas vezes utilizando funções de ordem superior como map, filter e reduce.

Alguns pontos principais a programação funcional:

- High order functions
- Imutabilidade
- Pipeline de funções
- Funçẽos puras

```javascript
const numeros = [1, 2, 3, 4, 5];

const aoQuadrado = numeros
  .map((numero) => numero * numero)
  .filter((numero) => numero % 2 === 0)
  .reduce((acumulador, numero) => acumulador + numero, 0);

console.log(aoQuadrado); // Saída: 20
```