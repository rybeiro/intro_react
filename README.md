# intro_react
Material de apoio para consultas posteriores do conteúdo de Javascript e React

### IDE
- Visual Studio Code

### dica de Extensões
- Dracula oficial (tema)
- Code Runner (terminal integrado na ide)
- Material icons theme (icones de extensões de arquivos)

# Javascript básico para React
## Declaração de variáveis
### var
Declaração de Variável com _var_ é global que pode ser acessada e alterada independentemente de onde foi declarada. 
### let
A declaração de variável com _let_ permite a alteração do seu valor inicial, mas não permite a redeclaração nem acesso fora de seu bloco de origem.
### const
A declaração de variável como _const_ não permite a alteração do seu valor inicial, não permite a redeclaração nem acesso fora de seu bloco de origem.

# Função e Arrow function
## Função
```javascript
// Sintaxe para declarar uma função sem parâmetros
function saudacao(){
  return 'Bom dia'
}
// Sintaxe para declar uma função com parâmetros
function saudacao(nome){
  return `Bom dia, ${nome}`
}
// Para interpolar código javascript em uma string pastar envolve-la entre apostrofos.
```
## Arrow function
```javascript
// Sintaxe para declarar uma arrow function
// utilizada nas novas versões do javascript
const ola = () => {
  return "Bom dia"
}
// ou em uma linha
const ola = () => return "Bom dia"

// Sintaxe para declarar com 1 parâmetros

const ola = nome => return `Bom dia ${nome}`

// Sintaxe para delcar com 2 ou mais parâmetros
const ola = (nome, idade) => return `Bom dia ${nome}, você tem ${idade} de idade`
```

# Módulos
## Exportação
```javascript
// EXPORTAÇÃO PADRÃO
// pessoa.js
// objeto pessoa (é um módulo)
const pessoa = { nome: 'Fabio', idade:42 }
export default pessoa

// molde.js
// importação de módulo
import pessoa from './pessoa.js'
import p from './pessoa.js'

console.log(pessoa)
console.log(p)

// EXPORTAÇÃO MULTIPLA
// utils.js
const ola = nome => return `Ola ${nome}`

const idade = (ano_nasc) => return (2022 - ano_nasc)

export default { ola, idade }

// Podemos importar apenas uma função
// Importação unica
import { ola } from './utils.js'
console.log(ola('José Maria'))

// Importação multipla
import { ola, idade } from './utils.js'
console.log(ola('Maria'))
console.log(idade(1990))
```
# Classes, propriedades e métodos
## Classe
```javascript
// classe padrão ( Gato.js )
class Gato {
  nome = 'Felix'
  idade = 1

  som = () => return `${nome} faz: Miau miau`
}

let gatinho = new Gato
console.log(gatinho)
console.log(gatinho.som())

// classe com construtor ( Gato2.js )
class Gato {
  constructor(nome, idade){
    this.nome = nome
    this.idade = idade
  }

  som = () => return `${this.nome} faz: Miau miau`
}
let gatinho = new Gato('Guloso', 2)
console.log(gatinho)
console.log(gatinho.som())

// Herança
// Animal.js
class Animal {
  constructor(familia, habit){
    // propriedades
    this.familia = familia
    this.habitate = habit
  }
  // método
  habitate = () => return `é um animal ${this.habitate}`  
}

// Cachorro.js
class Cachorro extends Animal{
  constructor(nome, idade){
    super('Carnivoro', 'Domestico')
    // propriedades
    this.nome = nome
    this.idade = idade
  }
  // método
  latir = () => return `O ${this.nome} faz: au au`
}

let cachorro = new Cachorro('Belinha', 5)
console.log(cachorro)
```

# Operadores spreed e rest
## Spreed operator
```javascript
// trabalhando com arrays e objetos
// ARRAY
// definindo um array
const numeros = [1,2,3,4]
// copiando o array
const novo = numeros
// incluindo um novo elemnto no novo array
const novo.push(5)
// output
console.log(numeros)
console.log(novos)
// conclusão a copia com simbolo de atribuição ( = ) na verdade aponta para mesma instância da memória

// SPREED OPERATION com Array
// declarando o array
num = [1,2,3,4,5]
// criando uma copia em uma nova instância da memória
novo_num = [...num]
// incluindo um novo elemento
novo_num.push(6)
// output
console.log(num)
console.log(novo_num)

// OBJETOS
// definindo objeto
const felino = {
  nome: 'Felix',
  idade: 2
}
// copiando o objeto
const garfield = felino
// alterando o nome do garfield
garfield.nome = 'Max'

// output
console.log(felino)
console.log(garfield)
// mesmo problema, porque aponta para mesma instância de memória

// SPREED OPERATOR com objetos
const felino = { nome: 'felix', idade: 3 }

const max = { ...felino }
max.nome = 'sapeca'

console.log(felino)
console.log(max)

// incluindo novas propriedades

max = { ...max, raca: 'felinos', habitate: 'Domestico' }

console.log(felino)
console.log(max)

``` 
## rest Operator
Trata-se de um numero infinito de parametros
```javascript
// caso de uso comum
const soma = (n1, n2) => return n1 + n2
console.log(soma(1,2))

// caso de uso com rest operator

const soma = (...numeros) => numeros.reduce( (n1, n2) => a + b, 0)

console.log(soma(1,2,3))
console.log(1,2,3,4,5,7,9)
```

# Desistruturação
A desistruturação é utilizado para extrair elementos de um array e principalmente de objetos.
```javascript
// em Array
const frutas = ['banana','maça','laranja']
// desistrituração
let [fruta, fruta1] = frutas
console.log(fruta)
console.log(fruta1)
// output: banana 
// output: maça

// em Objetos
const pessoa = {nome: 'João', idade: 44, pais: 'Brasil', idioma: 'Português'}
// desistruturação
let { pais, idioma } = pessoa
console.log(pais)
console.log(idioma)

// exemplo com função
const localidade = pessoa => `${pessoa.nome} você mora no ${pessoa.pais}`
console.log(localidade(pessoa))

// exemplo mais direto e usual
const localidade = ({nome, pais}) => `${nome} você mora no ${pais}`
console.log(localidade(pessoa))
```