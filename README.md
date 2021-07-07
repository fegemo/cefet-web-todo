# Lista de Tarefas para Procrastinar 📓

Gerencie aquelas tarefas que você quer ~~não~~ fazer.

![Resultado final da atividade](https://fegemo.github.io/cefet-web/images/todo.webp)


## Atividade

Você deve fazer um sistema para cadastrar novas atividades que você ~~não~~
quer fazer. Fazendo isso, você vai treinar usar objetos em JavaScript e
criar elementos HTML dinamicamente.


### Exercício 0: Representar tarefas

No arquivo `tarefas.js`, crie um vetor de objetos chamado `tarefas` em que cada item
representa uma tarefa. Você pode criar objetos _ad-hoc_ ou usar algum tipo de "forma" (função construtora ou classe).

Cada tarefa deve ser descrita pelas propriedades:
1. `nome`: texto da tarefa
1. `categoria`: texto com nome da categoria, podendo ser `"lazer"`, `"compras"` ou `"estudos"`
1. `realizada`: booleano indicando se já foi cumprida

Já coloque duas tarefas _hard-coded_ no vetor tarefas, porque elas serão úteis no exercício seguinte.

<details>
  <summary>2 tarefas de exemplo...</summary>

  1. `'Comprar leite', compras', false`
  1. `'Escutar chimbinha', 'lazer', true`
</details>


### Exercício 1: Carregar **tarefas existentes**

Agora você deve percorrer o vetor `tarefas` e, para cada uma,
criar dinamicamente os elementos HTML referentes a ela e
adicioná-los à página (`#lista-tarefas`).

Há 2 abordagens:
- (a) criar uma função `insereTarefaNaPagina` (no
singular) que, recebe por parâmetro **01 objeto** com uma tarefa e
insere 01 elemento HTML `<li>` na lista de tarefas
(_i.e._, `ul#lista-tarefas`)
- (b) se estiver usando classes, criar um método `adicionaNaPagina(containerEl)`


O `<li>` que representa a tarefa deve ter uma classe `item-tarefa` para
que ele seja devidamente estilizado. Se a tarefa está `realizada` como
`true`, você deve colocar a classe `marcado` no
`<li class="item-tarefa">...</li>`, além da `item-tarefa`.

Em relação à categoria, adicione ao
`<li class="item-tarefa">` uma outra classe CSS com o nome `categoria-NOME`,
em que NOME pode ser `lazer`, `compras` ou `estudos`.


Depois de criar a função, **chame-a para cada objeto que está no vetor
`tarefas`**. Logo antes de popular o elemento HTML da lista com as tarefas,
não se esqueça de remover todos os filhos que estiverem lá.


### Exercício 2: Incluir uma **nova tarefa**

Quando o usuário clicar no botão `#incluir-nova-tarefa`, (a) crie um
novo objeto representando a nova tarefa, (b) coloque-a ao
final do vetor `tarefas` e, então, (c) chame a função que
a insere na página passando o objeto da nova tarefa como argumento.

Ao final dessa função, você deve **limpar o campo** onde o usuário digitou
a tarefa (_i.e._, `nova-tarefa-nome`).

Opcionalmente, você pode **"devolver o foco"** para esse mesmo controle.

<details>
  <summary>Puxar o foco para um campo...</summary>

  Isso é uma boa prática de Usabilidade que torna a página mais agradável quando
  o usuário vai digitar mais que 1 tarefa - assim que ele inclui uma, ele
  já está pronto para digitar a próxima.

  Todo elemento HTML que pode "ter o foco" tem um método `focus()` que
  podemos chamar assim:

  ```js
  // pede o elemento para "roubar o foco" - mover o cursor para dentro dele
  elemento.focus()
  ```
</details>


### Opcional 3: **Filtrar** por categoria

Faça com que, quando o usuário alterar o valor de 
`#filtro-de-categoria`, que os elementos HTML sejam 
atualizados para esmaecer aquelas que não possuem a 
categoria escolhida.

Há uma classe `.retido-no-filtro` que você pode injetar
a esses elementos, se quiser.


### Opcional 4: **Pressionar "Enter"** inclui a tarefa

Além do clique no botão, faça com que o pressionar da tecla "Enter",
quando o foco estiver no campo de texto (_i.e._, `nova-tarefa-nome`), também
insira a nova tarefa no vetor e na página.

Para isso, você pode usar o evento _keyup_ do controle e, dentro da _callback_,
perguntar qual `e.key` foi pressionada. Se `e.key === 'Enter'`, você pode
chamar a mesma função que registrou para o clique do botão.


### Opcional 5: **Concluir** uma tarefa

Faça com que um `click` em uma `.item-tarefa` coloque/remova a classe `marcado` e a defina como `realizada` (`true/false`).


## FAQ

1. Como posso criar novos elementos HTML na página?
   - [Slides da aula JS6 sobre criação de elementos][criando-elementos-dinamicamente]. Abordagens:
     1. Usando `document.createElement()`
     1. Usando templates + `innerHTML` ou criação de fragmento de DOM
1. Como posso criar um objeto?
  - [Slides sobre objetos ad-hoc][criando-objetos-adhoc]. Exemplo:
    ```js
    // forma literal
    let novoLivro = {
      titulo: 'O Pistoleiro',
      autor: 'Stephen King'
    };
    // usando operador 'new'
    let novoCarro = new Object();
    novoCarro.nome = 'Ka';
    novoCarro.marca = 'Ford';
    ```
  - [Slides sobre função construtora][criando-objetos-construtora]. Exemplo:
    ```js
    function Livro(titulo, autor) {
      this.titulo = titulo
      this.autor = autor
    }
    let novoLivro = new Livro('...', '...')
    ```
  - [Slides sobre classes][criando-objetos-classe]. Exemplo:
    ```js
    class Livro {
      constructor(titulo, autor) {
        this.titulo = titulo
        this.autor = autor
      }

      metodo1() {

      }
    }
    let novoLivro = new Livro('...', '...')
    ```
1. Como inserir um elemento ao final de um vetor?
   ```js
   const frutas = ['laranja', 'maçã'];
   frutas.push('kiwi');
   console.log(frutas);
   // laranja, maçã, kiwi
   ```
   - Veja os [slides sobre vetores][array] e de [métodos comuns de vetores][array-comuns]
1. Como colocar/tirar uma classe em um elemento HTML?
   ```js
   ovelhaEl.classList.add('raca-de-ovelha');
   ovelhaEl.classList.remove('raca-de-ovelha');
   ovelhaEl.classList.toggle('invisivel');
   ```
   - Veja os [slides da aula js2][classes]



[criando-elementos-dinamicamente]: https://fegemo.github.io/cefet-front-end/classes/js4/#criando-elementos-html-dinamicamente
[criando-objetos-adhoc]: https://fegemo.github.io/cefet-web/classes/js3/#criacao-de-objetos
[criando-objetos-construtora]: https://fegemo.github.io/cefet-web/classes/js3/#funcao-construtora
[criando-objetos-classe]: https://fegemo.github.io/cefet-web/classes/js5/#classes
[array]: https://fegemo.github.io/cefet-web/classes/js1/#vetores
[array-comuns]: https://fegemo.github.io/cefet-web/classes/js1/#metodos-comuns-de-vetores-1
[classes]: https://fegemo.github.io/cefet-web/classes/js2/#colocando-removendo-classes
