# Reprograma - Semana 10

Bem vindas a semana 10!
> Vimos muita coisa até aqui e o objetivo dessa aula é nivelar e alinhar o conhecimento de vocês em JavaScript, vamos revisar mas também vamos aprender coisas novas!

## O que vamos ver nessa semana?

1. [Variáveis](#variáveis)
2. [String X Template strings](#string-x-template-strings)
3. [Condicional](#condicional)
   - [if...else X Operador condicional ternário](#if...else-x-operador-condicional-ternário)
   - [switch](#switch)
4. [Function X Arrow function](#function-x-arrow-function)
5. [Função Callback](#função-callback)
6. [Array](#array)
7. [Métodos de iteração](#métodos-de-iteração)
    - [while](#while)
    - [for](#for)
    - [forEach](#foreach)
    - [find](#find)
    - [map](#map)
    - [filter](#filter)
    - [reduce](#reduce)
8. [Objetos](#objetos)
9. [JSON](#json)
10. [Spoiler alert!!!](#spoiler-alert!!!)

---

### Variáveis

Declarando variáveis:

```js
var nome = 'Reprograma'
```

Formato ES6:

```js
const nome = 'Reprograma'

let idade = 18
idade = 19
```

MDN: [var](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Statements/var), [const](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Statements/const), [let](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Statements/let)

---

### String X Template strings

Exemplo de string:

```js
const frase = 'Olá, mundo!'

console.log(frase)
```

Exemplo de template string:

```js
const elogio = 'Maravilhosa'

const templateString = `Olá, ${elogio}`

console.log(templateString)
```

MDN: [template strings](https://developer.cdn.mozilla.net/pt-BR/docs/Web/JavaScript/Reference/template_strings)

---

### Condicional 

#### if...else X Operador condicional ternário

Exemplo de condicional usando `if...else`:

```js
const nota = 3

if (nota >= 7) {
  return 'aprovado'
} else {
  return 'reprovado'
}
```

Exemplo de condicional usando ternário:

```js
const nota = 3

(nota >= 7) ? 'aprovado' : 'reprovado'
```

MDN: [if...else](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Statements/if...else), [operador condicional ternário](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Operators/Operador_Condicional)

---

#### switch

> A estrutura condicional switch permite executar um bloco de código diferente de acordo com cada opção(case) especifica. Seu uso é indicado quando os valores a serem analisados nessas condições são pré-definidos.

Exemplo de condicional usando `switch`:

```js
const expressao = 'Beyoncé';
switch (expressao) {
  case 'Shakira':
    console.log('É colombiana!');
    break;
  case 'Beyoncé':
  case 'Katy Perry':
    console.log('É americada!');
    break;
  case 'IZA':
    console.log('É brasileira!');
    break;
  default:
    console.log(`Desculpe, não encontramos a nacionalidade da ${expressao}.`);
}
// É americada!
```

Exemplo: O que acontece se eu esquecer um break?
> Se você esquecer um break então o script irá rodar a partir do caso onde o critério foi correspondido e irá rodar também o caso seguinte independentemente do critério ter sido correspondido ou não

```js
const expressao = 0;
switch (expressao) {
    case -1:
        console.log('Amo gatinhos!');
        break;
    case 0: // expressao é 0 então aqui o critério foi correspondido
        console.log('Amo cachorrinhos!')
        // NOTA: o break esquecido deveria estar aqui
    case 1: // nenhuma instrução break em 'case 0:' então verificação continua
        console.log('Amo esquilos!');
        break; // o programa encontra esse break então não vai continuar para o 'case 2:'
    case 2:
        console.log('Amo pandas!');
        break;
    default:
        console.log('Amo todos os animais!');
}
// Amo cachorrinhos!
// Amo esquilos!
```

MDN: [switch](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Statements/switch)

---

### Function X Arrow function

Declarando funções:

```js
function falar() {
    return 'pipipi popopo'
}
console.log(falar()) // pipipi popopo

function dobro(num) {
    return num * 2
}
console.log(dobro(2)) // 4

function calcularMedia(nota1, nota2, nota3) {
    const soma = (nota1 + nota2 + nota3)
    const media = soma / 3
    return media
}
console.log(calcularMedia(10, 5, 6)) // 7
```

Ou, podemos declarar as mesmas funções da seguinte forma:

```js
const falar = function() {
  return 'pipipi popopo'
}

const dobro = function(num) {
  return num * 2
}

const calcularMedia = function(nota1, nota2, nota3) {
  const soma = (nota1 + nota2 + nota3)
  const media = soma / 3
  return media
}
```

Arrow function possui uma sintaxe mais curta, e sabemos que é uma função pelo símbolo `=>`
```js
const falar = () => {
  return 'pipipi popopo'
}

const dobro = (num) => {
  return num * 2
}

const calcularMedia = (nota1, nota2, nota3) => {
  const soma = (nota1 + nota2 + nota3)
  const media = soma / 3
  return media
}
```

Conseguimos deixar a função ainda mais concisa, pois:
- caso a função só tenha uma linha de instrução, as chaves `{}` são opcionais
- e ao remover as chaves `{}`, o `return` é implícito e, portanto, também removemos:

```js
const falar = () => 'pipipi popopo'

const dobro = (num) => num * 2

const calcularMedia = (nota1, nota2, nota3) => (nota1 + nota2 + nota3) / 3
```

- caso a função só tenha 1 parâmetro, os parênteses em volta do parâmetro `(param)` também são opcionais:

```js
const dobro = num => num * 2
```

MDN: [funções](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Guide/Fun%C3%A7%C3%B5es),[arrow function](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Functions/Arrow_functions)

---

### Função Callback

> Uma função callback é uma função passada a outra função como parâmetro, que é então invocada dentro da função externa para completar algum tipo de rotina ou ação. 

```js
function somar(a, b) {
  return a + b
}

function subtrair(a, b) {
  return a - b
}

function multiplicar(a, b) {
  return a * b
}

function dividir(a, b) {
  return a / b
}

function ordenar(a, b) {
  if (a <= b) {
    return [a, b]
  } else {
    return [b, a]
  }
}

function calcular(a, b, callback) {
  return callback(a, b)
}

const num1 = 7
const num2 = 2

const somaDoisNumeros = calcular(num1, num2, somar)
console.log(somaDoisNumeros) // 9

const subtracaoDoisNumeros = calcular(num1, num2, subtrair)
console.log(subtracaoDoisNumeros) // 5

const multiplicacaoDoisNumeros = calcular(num1, num2, multiplicar)
console.log(multiplicacaoDoisNumeros) // 14

const divisaoDoisNumeros = calcular(num1, num2, dividir)
console.log(divisaoDoisNumeros) // 3.5

const ordenarDoisNumeros = calcular(num1, num2, ordenar)
console.log(ordenarDoisNumeros) // [2, 7]
```

Deixando a sintaxe reduzida:

```js
const somar = (a, b) => a + b

const subtrair = (a, b) => a - b

const multiplicar = (a, b) => a * b

const dividir = (a, b) => a / b

const ordenar = (a, b) => (a <= b) ? [a, b] : [b, a]

const calcular = (a, b, callback) => callback(a, b)
```

MDN: [Função callback](https://developer.mozilla.org/pt-BR/docs/Glossario/Callback_function)

---

### Array

Declaração de array

```js
const lista = new Array('pera', 'uva', 'maçã', 'salada mista')

const numeros = [9, 2, 5]
```

Acessando elementos pela posição do array:

```js
const primeiroItem = lista[0]

console.log(primeiroItem) // pera
```

Tamanho de array:

```js
const tamanho = numeros.length

console.log(tamanho) // 4
```

Atribuição via desestruturação

```js
const [primeiro, segundo, terceiro, quarto] = lista

console.log(primeiro) // pera
console.log(segundo) // uva
console.log(terceiro) // maçã
console.log(quarto) // salada mista
```

MDN: [array](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Array), [atribuição via desestruturação](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Operators/Atribuicao_via_desestruturacao)

---

### Métodos de iteração

#### while

```js
const numeros = [9, 2, 5]

let i = 0

while (i < numeros.length) {
  const dobro = numeros[i] * 2
  console.log(dobro)
  i++
}
// 18
// 4
// 10
```

MDN: [while](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Statements/while)

---

#### for
> A instrução for cria um loop que consiste em três expressões opcionais, dentro de parênteses e separadas por ponto e vírgula, seguidas por uma declaração ou uma sequência de declarações executadas em sequência(inicialização, condição , expressão final e declaração).

```js
const numeros = [9, 2, 5]

for (let i = 0; i < numeros.lenght; i++) {
  const dobro = numeros[i] * 2
  console.log(dobro)
}
// 18
// 4
// 10
```

Modificando a lista de números:

```js
const numeros = [9, 2, 5]

for (let i = 0; i < numeros.lenght; i++) {
  numeros[i] = numeros[i] * 2
}

console.log(numeros) // [18, 4, 10]
```

MDN: [for](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Statements/for)

---

#### forEach
> O método forEach() executa uma dada função para cada elemento de um array.

```js
const numeros = [9, 2, 5]

function dobrar(item) {
  const dobro = item * 2
  console.log(dobro)
}

numeros.forEach(dobrar)
// 18
// 4
// 10
```

Modificando a lista de números:

```js
const numeros = [9, 2, 5]

function dobrar(item) {
  item = item * 2
}
numeros.forEach(dobrar)
console.log(numeros) // [9, 2, 5] 

// Ele usa o item do array de forma imutável(não muda), para resolver podemos usar os demais parâmetros da função callback
const numeros = [9, 2, 5]

function dobrar(item, index, numeros) {
    numeros[index] = item * 2
}
numeros.forEach(dobrar)
console.log(numeros) // [18, 4, 10]

```

Deixando mais conciso:

```js
const numeros = [9, 2, 5]

numeros.forEach(function dobrar(item, index, numeros) {
    numeros[index] = item * 2
})

console.log(numeros) // [18, 4, 10]
```

Refatorando para JS moderno:

```js
numeros.forEach((item, index, numeros) => numeros[index] = item * 2)

console.log(numeros) // [18, 4, 10]
```

MDN: [forEach](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach)

---

#### map
> O método `map()` invoca a função `callback` passada por argumento para cada elemento do Array e devolve um novo Array como resultado.

```js
const numeros = [9, 2, 5]

function dobrar(item) {
  return item * 2
}

const numerosDobrados = numeros.map(dobrar)

console.log(numerosDobrados) // [18, 4, 10]
```

Deixando mais conciso:

```js
const numerosDobrados = numeros.map(function (item) {
  return item * 2
})

console.log(numerosDobrados) // [18, 4, 10]
```

Refatorando para JS moderno:

```js
const numerosDobrados = numeros.map(item => item * 2)

console.log(numerosDobrados) // [18, 4, 10]
```

**Obs:** o método `map` não altera o array original. Ele retorna um array novo com o resultado do `map`.

MDN: [map](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Array/map)

---

#### find

> O método find executa a função callback uma vez para cada elemento presente no array até que encontre um onde callback retorne o valor true. Se o elemento é encontrado, find retorna imediatamente o valor deste elemento. Caso contrário, find retorna undefined.

```js
const numeros = [9, 2, 5]

function procuraCinco(item) {
  return item === 5
}

const achouCinco = numeros.find(procuraCinco)

console.log(achouCinco) // 5
```

MDN: [find](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Array/find)

---

#### filter

```js
const numeros = [9, 2, 5]

function impar(item) {
  return item % 2 !== 0
}

const numerosImpares = numeros.filter(impar)
```

Deixando mais conciso:

```js
const numerosImpares = numeros.filter(function (item) {
  return item % 2 !== 0
})
```

Refatorando para JS moderno:

```js
const numerosImpares = numeros.filter(item => item % 2 !== 0)

console.log(numerosImpares) // [9, 5]
```

**Obs:** o método `filter` não alterar o array original. Ele retorna um array novo com o resultado do `filter`.

MDN: [filter](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Array/filtro)

---

#### reduce

O método `reduce` recebe uma função callback com alguns parâmetros e essa função é executada a cada elemento presente no array. O resultado é a redução do array a um valor só. Normalmente, utilizamos os dois primeiros parâmetros: `acumulador` e `itemAtual`.

Por exemplo, podemos executar a soma de todos os valores do array utilizando o método `reduce`:

```js
const numeros = [9, 2, 5]

function somarTodos(acumulador, itemAtual) {
  return acumulador + itemAtual
}

const numerosSomados = numeros.reduce(somarTodos)

console.log(numerosSomados) // 16
```

Deixando mais conciso:

```js
const numerosSomados = numeros.reduce(function (acumulador, itemAtual) {
  return acumulador + itemAtual
})

console.log(numerosSomados) // 16
```

Refatorando para JS moderno:

```js
const numerosSomados = numeros.reduce((acumulador, itemAtual) => acumulador + itemAtual)

console.log(numerosSomados) // 16
```

MDN: [reduce](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Array/Reduce)

---

### Objetos

Declaração de objetos

```js
const objeto = new Object()
objeto.nome = 'mesa'
objeto.tipo = 'madeira'
objeto.peso = 20

const pokemon = {
  nome: 'Pikachu',
  tipo: 'elétrico',
  altura: 40.6,
}
```

Acessando o valor de uma propriedade do objeto.

```js
console.log(pokemon.nome) // Pikachu
```

Declarando uma variável de mesmo nome que a propriedade.

```js
const nome = pokemon.nome
const tipo = pokemon.tipo
const altura = pokemon.altura

console.log(nome) // Pikachu
console.log(tipo) // elétrico
console.log(altura) // 40.6
```

Atribuição via desestruturação

```js
const { nome, tipo, altura } = pokemon

console.log(nome) // Pikachu
console.log(tipo) // elétrico
console.log(altura) // 40.6
```

MDN: [objetos](https://developer.mozilla.org/pt-BR/docs/Aprender/JavaScript/Objetos/B%C3%A1sico), [atribuição via desestruturação](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Operators/Atribuicao_via_desestruturacao)

---
### JSON
> JSON significa **J**ava**S**cript **O**bject **N**otation - Notação de Objetos JavaScript. É uma formatação leve de troca de dados. Para seres humanos, é fácil de ler e escrever. Para máquinas, é fácil de interpretar e gerar. Está baseado em um subconjunto da linguagem de programação JavaScript, a pesar disso, JSON é em formato texto e completamente independente de linguagem, pois usa convenções que são familiares à maioria das linguagens atuais.

Os dados salvos em um arquivo .json e consistem em uma lista com uma sequencia de pares chave / valor. Cujo formato se parece muito com o formato literal do objeto JavaScript.


```json
    { 
      "key": "value" 
    }
```

```json
  [
      {
          "key": "value"
      },
      {
          "key": "value"
      },
      {
          "key": "value"
      }
  ]
```

Você pode incluir os mesmos tipos de dados básicos dentro do JSON, como em um objeto JavaScript padrão — strings, números, matrizes, booleanos e outros literais de objeto. Porem, diferente das Arrays e Objetos os nomes das propriedades(key) devem ser strings com aspas duplas e as vírgulas à direita são proibidas.

```json
  [
    {
        "id": 1,
        "nome": "Super Mario World",
        "plataformas": ["Wii", "New Nintendo 3DS", "Wii U", "Super Nintendo Entertainment System (SNES)"],
        "ativo": true,
        "Empresa": "Nintendo EAD",
        "imagem": "https://images.igdb.com/igdb/image/upload/t_cover_big/co23jy.jpg"
    },
    {
        "id": 2,
        "nome": "Angry Birds Fight!",
        "plataformas": ["Android"],
        "ativo": false,
        "Empresa": "Rovio Entertainment",
        "imagem": "https://images.igdb.com/igdb/image/upload/t_cover_big/myewkwhbaxeg5fugaaj9.jpg"
    }
  ]
```

MDN: [JSON](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/JSON)

---

## Spoiler alert!!!
> Na proxima semana vamos aprender requisições a APIs, então trouxe para vocês alguns materias e artigos para já nos familiarizarmos com o assunto. Divirtam-se!

- [Protocolo HTTP, API e REST de forma resumida](https://medium.com/@luanacm/protocolo-http-api-e-rest-de-forma-resumida-36a5494f3da4)
- [O que é API?](https://medium.com/@sampaioaanaluiza/o-que-%C3%A9-api-f507b643f50c)
- [Usando fetch API](https://medium.com/bruno-pulis/usando-fetch-api-ad0650f13a25)
- [Promises: Uma abordagem simples](https://medium.com/@dellean.santos/promises-uma-abordagem-simples-b0c8331fa077)
- [Async e Await: Melhorando funções assíncronas](https://medium.com/@peretta.breno/async-e-await-melhorando-fun%C3%A7%C3%B5es-ass%C3%ADncronas-847bbbdd7a07)

## Aqui meus contatos, vamos nos conectar na redes suas maravilhosas !
- [Linkedin](https://www.linkedin.com/in/alessandrizes/)
- [Github](https://github.com/alessandrizes)
- [Twitter](https://twitter.com/alessandrizes)
- [Instagram](https://www.instagram.com/alessandrizes)
- Email: alessandrizes@gmail.com
