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