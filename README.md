# Vamos do início! :sunglasses:

Pra ficar mais fácil, você pode escolher se guiar pelas temas abaixo, só clicar em alguma das palavras-chaves e você vai direto pro tópico desejado.

* [O que é Reactjs](https://github.com/bragamat/aprenda-reactjs-testando/tree/solucao/0#o-que-é-reactjs-)
* [Como Começar Com Reactjs ?](https://github.com/bragamat/aprenda-reactjs-testando/tree/solucao/0#como-começar-com-reactjs-)
* [Por que testar ?](https://github.com/bragamat/aprenda-reactjs-testando/tree/solucao/0#por-que-testar-)
* [O que testar ?](https://github.com/bragamat/aprenda-reactjs-testando/tree/solucao/0#-que-testar-)
* [Como Testar ?](https://github.com/bragamat/aprenda-reactjs-testando/tree/solucao/0#-como-testar-)

# O que é Reactjs ?

## Introdução
 - _"O React é uma biblioteca JavaScript de código aberto com foco em criar interfaces de usuário em páginas web desenvolvida e mantida pelo facebook"_. Essa é a definição pelo [wikipédia](https://pt.wikipedia.org/wiki/React_(JavaScript)). É um biblioteca dentro do ambiente _react_ que nos ajuda no desenvolvimento de interfaces amigáveis e performáticas, renderizando somente o que precisa ser renderizado! :smiley: 
 <br/>
 - É uma **biblioteca** baseada em componentes que conseguem gerenciar o próprio estado individualmente. Sendo extremamente prática a reutilização desses componentes em vários lugares da nossa aplicação.
 <br/>
 - O react utiliza uma ferramenta chamada [Virtual Dom (VDOM)](https://pt-br.reactjs.org/docs/faq-internals.html#what-is-the-virtual-dom) que, em resumo, faz a diferenciação do estado da aplicação no DOM do browser com o estado da aplicação em si, renderizando somente o que é necessário! Pra isso, uma outra biblioteca é utilizada: O [ReactDOM](https://pt-br.reactjs.org/docs/react-dom.html#overview) é resposável por renderizar o container da aplicação em um template também (entre vaárias outras coisas). Esta imagem ilustra muito bem como ocorre essa diff: 
 ![](https://miro.medium.com/max/1624/1*638z1MCoYN1MyCFQV9a2SA.gif)
 Está sendo re-renderizado somente a diferença.


## Como Começar Com Reactjs
- Por ser uma lib simples de javascript, a gente pode simplesmente importar um direto de um servidor "publico" em um html simples.<br />
Então vamos criar um arquivo "index.html" simples pra gente começar a entender o fluxo de trabalho (esse arquivo vai estar nesse repositório, só procurar por _index.html_):

==============================================================
## Por que testar ?
Vou resumir com alguns comentários que peguei na comunidade :+1:

- ```"pra não ter que consertar bug em produção sexta à noite na correria quando você deveria estar tomando uma cerveja"``` :beer:

- ```"Testar prova para VOCÊ MESMO que o código produzido faz o que se espera que ela faça. ```

- ```"Pra saber onde eu começo e onde eu termino"```

- ```"[...] dar manutenção ou alterar o comportamento de determinado fluxo as vezes uma pequena mudança pode acabar quebrando em diversos lugares e com os testes você percebe na hora exatamente quais pontos  aquela alteração está influenciando"```

Em resumo, o teste te dá a segurança necessária pra realizar modificações futuras em aplicações além de guiar você do começo ao fim do desenvolvimento de um componente, fluxo de interação ou até mesmo um simples método de soma. :smile:

## O que testar ?
A ideia principal de um teste é sempre ver se o valor entregado por um recurso, função, componente, fluxo (ou qualquer _feature_) está entregando é o mesmo pensado e implementado!

Então por exemplo, se temos um recurso que recebe um _input_ e faz com que apareça um _modal_ na tela com esse _input_. Simulamos o valor a ser digitado no _input_ e simulamos o modal aparecendo e comparamos com o valor que aparece nele. 


## Como Testar ? 
- Iremos utilizar um _framework_ de testes: [_**JEST**_](https://jestjs.io/) que possuei várias ferramentas que nos ajudarão a escrever nossos testes de forma rápida, simples, e prática! :rocket:
  Também, utilizaremos uma biblioteca recomendada pela própria documentação do [**Reactjs**](https://pt-br.reactjs.org/): [_React-Testing-Library_](https://testing-library.com/docs/react-testing-library/intro) - Que é uma lib que facilita simular ações do usuário. :smiley:

Primeiro se cria o arquivo que vai conter os testes. Vamos criar um arquivo chamado `App.test.js`. 

E Dentro: 

```
import React from "react";
import { render } from "@testing-library/react";
import App from "../App";

describe("<App />", () => {
  it("renders without errors", () => {
    expect(render(<App />)).toBeTruthy();
    // o expect aqui não seria necessário
    // o metodo render já retorna um erro caso o render não funcione
  });
});
```

Temos palavras chaves aqui:
- **describe**: é um _syntax-sugar_ para escrever o contexto que a gente está escrevendo o teste. Nesse caso, eu escolhi deixar `<App />`;
- **it**: Palavra chave pra onde escreveremos o que está sendo testado e o teste em si dentro;
- **expect**: É o que compara um valor com o valor do _.toBe_;
- **toBe**: É o que compara um valor com o valor do _expect_;
- **render**: método disponível pela importação da biblioteca `"@testing-library/react"`;

De modo geral, testes são escritos nessa forma:

"espero que (valor) seja igual (valor)" => ```expect(true).toBe(true)```



O _Jest_ nos permite digitar `jest` na linha de comando do terminal e rodar como testes todos os arquivos quem possuem `.spec` ou `.test` no nome. Então por exemplo:
digamos que temos o seguinte arquivo: 
`App.test.js`

src/__tests__/
├── App.test.js

Quando usarmos o comando `jest`, o arquivo `App.test.js` será rodado. ![jestRun](./public/images/runningJestApp.png)
