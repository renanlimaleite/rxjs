# RxJS

# Programação Reativa
> Programação reativa é um paradigma de programação, onde se concentra na propagação automática de mudanças e orquestrar fluxos de dados assíncronos (streams). Em vez de definir explicitamente como os dados e as mudanças nos dados devem ser manipulados, a programação reativa permite que você declare as relações entre os dados e o sistema cuida automaticamente da propagação de mudanças.

Por exemplo, imagine que temos dois fluxos de dados assíncronos sendo passados para um aplicativo: **um conjunto de arrays vindo de um callback de uma função** e **uma chamada a uma API que retorna o usuário logado**.

No RxJS, esses fluxos de dados (streams) seriam representados como Observáveis. Suponto que, quando o array tem mais de 10 itens, um operador do RxJS, como filter ou map, poderia ser usado para transformar o fluxo de dados em apenas metade desses itens. Esses dados transformados são então propagados automaticamente para todos os Observadores que estão inscritos neste Observável. Em outras palavras, qualquer parte do aplicativo que "escuta" esse fluxo de dados receberá automaticamente a nova versão transformada dos dados.

Da mesma forma, quando um usuário está logado, essa informação pode ser representada como outro Observável. Quando o estado de login do usuário muda, essa mudança é propagada automaticamente para todos os Observadores inscritos neste Observável. Isso significa que qualquer parte do aplicativo que precisa saber se um usuário está logado será automaticamente atualizada com as informações mais recentes.

Portanto, o RxJS permite que você crie e manipule fluxos de dados assíncronos de uma maneira que seja fácil de entender e gerenciar, tornando a programação reativa mais acessível e eficaz.

# Programação Declarativa
> Na programação declarativa, você está descrevendo o **"o quê" - o que você quer alcançar**, *sem especificar exatamente como chegar lá*. Você está descrevendo a lógica sem a necessidade de controlar o fluxo do programa. *O foco está no resultado final*, não em como você chega lá.

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
let oddNumbers = numbers.filter(n => n % 2 !== 0); 

console.log(oddNumbers); // [1, 3, 5]
```

# Observer Pattern
> O padrão Observer é um padrão de projeto comportamental que permite que você defina um mecanismo de assinatura para notificar múltiplos objetos sobre quaisquer eventos que aconteçam com o objeto que eles estão observando. O padrão Observer define uma dependência de um para muitos (1 para n) entre objetos de modo que quando um objeto (Observável) muda de estado, todos os seus dependentes (Observadores) sejam notificados e atualizados automaticamente.

Uma analogia comum para o padrão Observer é a de uma editora de jornais (Observável) e seus assinante (Observadores). A editora é o objeto observado e os assinantes são os objetos observadores. Quando a editora publica um novo jornal, todos os assinantes recebem uma cópia automaticamente.

# Iterator Patter
> O Iterator Pattern é um padrão de design comportamental que fornece uma maneira de acessar os elementos de um objeto agregado sequencialmente sem expor sua representação subjacente.

O padrão Iterator envolve duas partes principais:

- Iterator: Esta é a interface que define os métodos para percorrer o objeto agregado. Os métodos comuns incluem next(), hasNext(), first(), current(), etc.

- Aggregate: Esta é a interface ou classe que fornece um método para criar um iterador. Normalmente, é fornecido um método chamado getIterator() ou similar.

A ideia é que você possa percorrer o objeto agregado sem precisar entender os detalhes de sua estrutura interna. Isso torna o código mais modular e fácil de entender, pois a lógica de iteração é abstraída para o objeto Iterator.

Exemplo: 
```javascript
class ArrayIterator {
  constructor(items) {
    this.index = 0;
    this.items = items;
  }

  hasNext() {
    return this.index < this.items.length;
  }

  next() {
    return this.items[this.index++];
  }
}

const array = [1, 2, 3, 4, 5];
const iterator = new ArrayIterator(array);

while (iterator.hasNext()) {
  console.log(iterator.next());
}
```

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
  .map(numero => numero * numero)
  .filter(numero => numero % 2 === 0)
  .reduce((acumulador, numero) => acumulador + numero, 0);

console.log(aoQuadrado); // Saída: 20
```

# Observer Pattern + Iterator Patter + Functional Programming
> "ReactiveX combines the **Observer pattern** with the **Iterator pattern** and **functional programming with collections** to fill the need for an ideal way of managing sequences of events."

Exemplo:

```javascript
const { from } = require('rxjs');
const { map, filter } = require('rxjs/operators');

// Cria um Observable a partir de um array de arrays (Iterator Pattern)
const source$ = from([
  [1, 2, 3, 4, 5],
  [6, 7, 8, 9, 10],
  [11, 12, 13, 14, 15]
]);

// Usa operadores do RxJS para processar os dados (programação funcional)
const processed$ = $source.pipe(
  map(arr => arr.map(n => n * 2)),
  filter(arr => arr.some(n => n % 2 === 0))
);

// Se inscreve no Observable para receber os dados processados (Observer Pattern)
const processed$ = source$.pipe(.subscribe(arr => console.log(arr));
```