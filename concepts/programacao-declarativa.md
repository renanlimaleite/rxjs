# Programação Declarativa

> Na programação declarativa, você está descrevendo o **"o quê" - o que você quer alcançar**, _sem especificar exatamente como chegar lá_. Você está descrevendo a lógica sem a necessidade de controlar o fluxo do programa. _O foco está no resultado final_, não em como você chega lá.

A programação declarativa, em essência, busca tornar o código mais legível e fácil de entender, abstraindo os detalhes de "como" uma operação é realizada. Bibliotecas como RxJS ou Lodash fornecem uma série de funções que permitem escrever código de maneira mais declarativa.

```javascript
// Forma IMPERATIVA (você escreve como o programa deve ser executado, linha por linha)
let numbers = [1, 2, 3, 4, 5];
let oddNumbers = [];

for (let i = 0; i < numbers.length; i++) {
  if (numbers[i] % 2 !== 0) {
    oddNumbers.push(numbers[i]);
  }
}

console.log(oddNumbers); // [1, 3, 5]

// Forma DECLARATIVA (você não se preocupa como o código foi escrito, mas sim com resultado final)
let numbers = [1, 2, 3, 4, 5];
// Aqui delegamos ao filter fazer a reestruturação dos dados.
let oddNumbers = numbers.filter((n) => n % 2 !== 0);

console.log(oddNumbers); // [1, 3, 5]
```