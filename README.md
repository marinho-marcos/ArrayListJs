# ArrayListJs

tutorial sobre manipulação de coleções em JavaScript utilizando três métodos muito importantes para trabalhar com listas: **map**, **filter** e **reduce**.  
A ideia é mostrar como cada um funciona e como podem ser usados

---

## 1. introdução

Arrays são estruturas fundamentais no JavaScript. as vezes precisamos transformar dados, filtrar informações ou calcular algum resultado a partir de uma lista.  
Os métodos `map()`, `filter()` e `reduce()` facilitam bastante esse processo, deixando o código mais limpo e mais fácil de manter.

Neste tutorial, vamos utilizar como exemplo uma lista de alunos e suas notas para demonstrar como esses métodos podem ser aplicados.

---

## 2. Estrutura básica dos métodos

### **map()**
percorre o array e retorna um novo array com os elementos modificados.  
obs: não altera o array original.

```js
let numeros = [1, 2, 3];
let dobrados = numeros.map(n => n * 2);
// [2, 4, 6]
```

---

### **filter()**
Retorna um novo array contendo apenas os elementos que passaram em um teste lógico.

```js
let numeros = [1, 2, 3, 4];
let pares = numeros.filter(n => n % 2 == 0);
// [2, 4]
```

---


### **reduce()**
Reduz o array a um único valor. ideal para somar números, calcular médias, contar elementos, etc.

```js
let numeros = [1, 2, 3, 4];
let soma = numeros.reduce((ac, n) => ac + n, 0);
// 10
```
obs: "ac" será nosso aculmulador, que começará em 0.

---


## 3. Exemplo prático com lista de alunos e suas notas

Vamos criar uma lista de alunos, cada um contendo nome, matrícula e notas.
Em seguida, vamos calcular a média individual de cada aluno e filtrar apenas os que tiverem média acima de 7.

```js
let alunos = [
  { nome: "ana", matricula: 101, notas: [8, 7, 9]},
  { nome: "bruno", matricula: 102, notas: [5, 6, 6]},
  { nome: "carla", matricula: 103, notas: [9, 8, 10]},
  { nome: "Diego", matricula: 104, notas: [7, 7, 8]},
  { nome: "eduarda", matricula: 105, notas: [6, 5, 7] }
];
```

---

### 3.1 Calculando a média de cada aluno utlizando map + reduce

```js
let alunosComMedia = alunos.map(aluno => {
  let soma = aluno.notas.reduce((total, n) => total + n, 0);
  let media = soma / aluno.notas.length;

  return { ...aluno, media };
});
// utilizamos o espalhamento na construção do novo obejto de aluno juntamente com sua media
```

---

### 3.2 Filtrando alunos com média maior que 7

```js
let aprovados = alunosComMedia.filter(aluno => aluno.media >= 7);
```
