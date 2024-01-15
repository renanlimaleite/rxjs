# Programação Reativa
> Programação reativa é um paradigma de programação, onde se concentra na propagação automática de mudanças e orquestrar fluxos de dados assíncronos (streams). Em vez de definir explicitamente como os dados e as mudanças nos dados devem ser manipulados, a programação reativa permite que você declare as relações entre os dados e o sistema cuida automaticamente da propagação de mudanças.

Por exemplo, imagine que temos dois fluxos de dados assíncronos sendo passados para um aplicativo: **um conjunto de arrays vindo de um callback de uma função** e **uma chamada a uma API que retorna o usuário logado**.

No RxJS, esses fluxos de dados (streams) seriam representados como Observáveis. Suponto que, quando o array tem mais de 10 itens, um operador do RxJS, como filter ou map, poderia ser usado para transformar o fluxo de dados em apenas metade desses itens. Esses dados transformados são então propagados automaticamente para todos os Observadores que estão inscritos neste Observável. Em outras palavras, qualquer parte do aplicativo que "escuta" esse fluxo de dados receberá automaticamente a nova versão transformada dos dados.

Da mesma forma, quando um usuário está logado, essa informação poade ser representada como outro Observável. Quando o estado de login do usuário muda, essa mudança é propagada automaticamente para todos os Observadores inscritos neste Observável. Isso significa que qualquer parte do aplicativo que precisa saber se um usuário está logado será automaticamente atualizada com as informações mais recentes.

Portanto, o RxJS permite que você crie e manipule fluxos de dados assíncronos de uma maneira que seja fácil de entender e gerenciar, tornando a programação reativa mais acessível e eficaz.