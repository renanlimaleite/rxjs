# Pureza
> O que faz o RxJS poderezo é a habilidade de criar outputs usando funções puras, Isso significa que seu código está menos sujeitos a erros.
> Funções puras, também conhecidas como funções imutáveis ou sem efeitos colaterais, Essas funções têm características específicas que as tornam previsíveis e fáceis de entender. Aqui estão algumas características e benefícios das funções puras:

- **Imutabilidade**: As funções puras não modificam o estado externo ou têm efeitos colaterais. Isso significa que, dado um conjunto específico de entradas, uma função pura sempre produzirá o mesmo resultado, independentemente de quando ou quantas vezes for chamada.

- **Determinismo**: A imutabilidade das funções puras leva ao determinismo. Isso significa que, dado um conjunto de entradas, o resultado da função será sempre o mesmo, tornando o código mais previsível e fácil de entender.

- **Facilidade** de teste: Funções puras são fáceis de testar porque não dependem de estados externos ou variáveis globais. Você pode testar uma função pura passando diferentes conjuntos de entradas e verificando se os resultados são os esperados.

- **Composição**: Funções puras podem ser facilmente combinadas ou encadeadas para criar funções mais complexas. A composição de funções puras é uma prática comum na programação funcional, o que torna o código mais modular e reutilizável.

- **Paralelismo**: Como as funções puras não dependem de estados compartilhados ou variáveis globais, é mais fácil introduzir paralelismo no código. Isso pode levar a melhorias de desempenho em ambientes que suportam execução concorrente.

- **Melhor** legibilidade e manutenção: O código que utiliza funções puras tende a ser mais legível e fácil de manter. Como as funções puras têm um escopo mais restrito, é mais fácil entender seu comportamento sem ter que rastrear efeitos colaterais em outras partes do código.

- **Facilidade** de refatoração: Funções puras facilitam a refatoração do código, pois as mudanças locais têm menos probabilidade de afetar outras partes do sistema de forma inesperada.

- **Cacheabilidade**: Como as funções puras sempre produzem o mesmo resultado para um conjunto dado de entradas, elas são candidatas ideais para caching (armazenamento em cache), o que pode melhorar significativamente o desempenho em determinados casos.

Normalmente quando você cria funções impuras, outras partes do seu código pode atrapalhar seu estado, seja ele local, global etc.

```javascript
let count = 0;
document.addEventListener("click", () =>
  console.log(`Clicked ${++count} times`)
);
```

Usando RxJS você isola esse estado, fazendo com que nenhuma outra parte do código consiga mudar esse estado (evita atrapalhar)

```javascript
import { fromEvent, scan } from "rxjs";

fromEvent(document, "click")
  .pipe(scan((count) => count + 1, 0))
  .subscribe((count) => console.log(`Clicked ${count} times`));
```
