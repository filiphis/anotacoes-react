# Conceitos React

## JSX
- É a junção de Javascript + XML
- É uma sintaxe que o React utiliza para podermos criar nossa interface de forma declarativa
- Arquivos JSX devem ser uma função e retornarem um HTML. **Ex:** 

```JSX
() => (<html></html>)
```


<!-- className
	É utilizado como substituto da class no html -->



## Componentes
- São pedaços menores de nossa interface que são criados com o objetivo de futuramente serem reutilizados/reaproveitados.
- São funções e retornam um JSX/HTML




## Propriedades / props
- Com propriedades o mesmo componente pode ter **variações e/ou valores** diferentes.

Ex:  
```JSX
<Card name="Gustavo" /> <Card name="Rafa" />  <Card name="Luiz" /> 
```

- Os atributos/valores passados para um componente são recebidas como parâmetro deste componente através da propriedade **props**. 

Podemos utilizar os valores diretamente através da propriedade props:

```JSX
  function Card(props){
    return(
      <p>{props.name}</p>
    )
  }
```


Ou podemos utilizar a desestruturação do objeto pegando diretamente suas propriedades. Ex:

```JSX
  function Card({name}){
    return(
      <p>{name}</p>
    )
  }
```


- Também é possível enviar funções pelas propriedades


## Estado
- São variáveis que são monitoradas pelo componente, ou seja, quando houver alguma mudança o componente saberá e irá se renderizar novamente.

- Para utilizar o useState é necessário importa-lo:

```JSX
import useState from 'react'
```

#### O estado possui dois valores:
  1. Guardar o valor atual da variável.
  2. Alterar o valor da variável.

```JSX
const [valorAtual, setNovoValor] = useState('Valor inicial da variável');
```

- valorAtual = É responsável por guardar o valor atual da variável.
- setNovoValor = É uma função que tem a responsabilidade de atualizar o valorAtual.

Dê preferência para alterar o valor de um estado utilizando o padrão de Closure:
```JSX
const [valorAtual, setNovoValor] = useState	(0)

function handleFunc(){
  setNovoValor((state) => {state + 1})
  setNovoValor((state) => {state + 1})
}
```

## Hooks
- Os Hooks são funções especiais do React que permitem controlarmos o estado e o ciclo de vida dos componentes.
- Geralmente os Hooks começam com a palavra **use**.
- useState		=	Armazenar estado e conectar com a interface.
- useEffect		=	É executado UMA VEZ antes do componente ser renderizado ou quando as variáveis na [DEPENDENCIA] (2º parâmetro) forem alteradas.
- Pode existir mais de 1 useEffect no mesmo componente, com uma callback diferente para cada estado/variável.

Exemplo de useEffect:

```JSX
  useEffect(callbackFunction, [dependencia01, dependencia02, etc...]);
```



## Imutabilidade e Programação declarativa
- Nunca altere um estado, sempre crie um novo!
- O conteúdo não deve ser alterado, e sim, substituído.
- Substituir todo o conteúdo é mais performático!


## React e Formulários
- Utilize um estado para armazenar cada campo de um formulário.

Acessando elementos de um Formulário:
```js
  event.target.inputName
```



## Comunicação entre componentes
- É possível manipular o estado de elementos no componente pai, passando props para os componentes filhos.
- Pode ser passado como props tanto o state, como o setState().
- Para o setState é recomendado criar uma função no componente pai que utiliza o setState e repassar a função criada para o componente filho.

Por exemplo:

```JSX
const [comments, setComments] = useState([])

function deleteComment(comment) {
  const newComments = setComments(...);
}

<ComponenteFilho onDeleteComment={deleteComment} />
```

E no componente filho após receber a função onDeleteComment nas Props é possível utiliza-lá.



## Renderização de componentes
- Existem 3 momentos em que um componente é renderizado novamente no React:
  - Quando o estado é alterado.
  - Quando alguma Prop é alterada.
  - Quando o componente pai é renderizado novamente, o filho também é.


## Closures



## Key em listas no REACT
- É muito importante utilizar keys, elas devem ter valores únicos.
- Não é recomendado utilizar o índice de Arrays como key, a recomendação é realmente utilizar um ID com valor único.



















































