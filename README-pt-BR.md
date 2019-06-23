# **Lista de perguntas sobre JavaScript (avançadas)**
Eu publico diariamente perguntas sobre JavaScript de múltipla escolha no meu [Instagram](https://www.instagram.com/theavocoder), que também postarei aqui!

Do básico ao avançado: teste o quão bem você conhece JavaScript, atualize um pouco seu conhecimento ou prepare-se para sua entrevista de codificação! 💪 🚀 **update**: Eu atualizo este repo semanalmente com novas perguntas. Última atualização: **21 de junho**

As respostas estão nas seções recolhidas abaixo das perguntas, basta clicar nelas para expandi-las. Boa sorte

- [中文版本](./README-zh_CN.md)
- [Português](./README-pt_BR.md)
- [Русский](./README_ru-RU.md)  
- [Western Balkan](./README-bs_BS.md)  
- [Deutsch](./README-de_DE.md)  
- [Tiếng Việt](./README-vi.md)  
- [日本語](./README-ja_JA.md)  
- [Українська мова](./README-ua_UA.md)  

---

###### 1. Qual é a saída?

```javascript
function sayHi() {
  console.log(name);
  console.log(age);
  var name = "Lydia";
  let age = 21;
}

sayHi();
```

- A: `Lydia` and `undefined`
- B: `Lydia` and `ReferenceError`
- C: `ReferenceError` and `21`
- D: `undefined` and `ReferenceError`

<details><summary><b>Resposta</b></summary>
<p>

#### Resposta: D

Dentro da função, primeiro declaramos a variável `name` com a palavra-chave` var`. Isto significa que a variável é içada (o espaço de memória é configurado durante a fase de criação) com o valor padrão de `undefined`, até chegarmos na linha onde definimos a variável. Nós ainda não definimos a variável na linha onde tentamos registrar a variável `name`, então ela ainda mantém o valor de` undefined`.

Variáveis ​​com a palavra-chave `let` (e` const`) são hasteadas, mas ao contrário de `var`, não é <i> inicializado </ i>. Eles não estão acessíveis antes da linha que declaramos (inicializamos). Isso é chamado de "zona morta temporal". Quando tentamos acessar as variáveis ​​antes que elas sejam declaradas, o JavaScript lança um `ReferenceError`.

</p>
</details>

---

###### 2. Qual é a saída?

```javascript
for (var i = 0; i < 3; i++) {
  setTimeout(() => console.log(i), 1);
}

for (let i = 0; i < 3; i++) {
  setTimeout(() => console.log(i), 1);
}
```

- A: `0 1 2` and `0 1 2`
- B: `0 1 2` and `3 3 3`
- C: `3 3 3` and `0 1 2`

<details><summary><b>Resposta</b></summary>
<p>

#### Resposta: C


Por causa da fila de eventos em JavaScript, a função de retorno de chamada `setTimeout` é chamada _after_ o loop foi executado. Como a variável `i` no primeiro loop foi declarada usando a palavra-chave` var`, esse valor era global. Durante o loop, nós incrementamos o valor de `i` por` 1` cada vez, usando o operador unário `++`. No momento em que a função de retorno de chamada `setTimeout` foi invocada,` i` foi igual a `3` no primeiro exemplo.

No segundo loop, a variável `i` foi declarada usando a palavra-chave` let`: variáveis ​​declaradas com a palavra-chave `let` (e` const`) têm escopo de bloco (um bloco é qualquer coisa entre `{}`). Durante cada iteração, o `i` terá um novo valor, e cada valor terá um escopo dentro do loop.

</p>
</details>
