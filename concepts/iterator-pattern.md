# Iterator Pattern

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