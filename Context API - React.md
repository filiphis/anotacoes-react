# Context API - React

O que é e para que serve o Context no React ?

- É uma forma de passar dados entre a árvore de componentes sem precisar passar props manualmente em cada nível
- É uma maneira de compartilhar informações entre vários componentes da aplicação de uma maneira mais simples
- É uma forma de compartilhar uma informação globalmente para toda a aplicação;

## Guias e Video Aulas

- Guia rápido no Alura:
  https://www.alura.com.br/artigos/prop-drilling-no-react-js

- Video Aula Rocketseat
  Ignite 2022 - Mod.02 >> Aula 31 - Entendendo contextos

## Creating a context

### Importando, Criando e exportando um Context

A primeira coisa a se fazer para criar um contexto é importar sua API para a utilização:

```jsx
import { createContext } from "react";
```

Depois criamos a tipagem que esse contexto deve possuir:

```JSX
  type PropsContextType = {
    contextProp1: string
    contextProp2: []
    myComponentFunc: () => void
    ...props
  }

  export const NameContext = createContext({} as PropsContextType)
```

### Utilizando o context em outros componentes

Para utilizar o contexto devemos criar um componente <NameContext.Provider>{children}</NameContext.Provider>, onde a prop children será um ReactNode que terá como filho todos os componentes (ou a aplicação toda: App) que irão utilizar os dados do provider.

#### No componente App:

```jsx
<NameContext.Provider>
  <App />
</NameContext.Provider>
```

#### Em outros componentes filhos do App:

```jsx
import { useContext } from "react";
const { myComponentFunc, contextProp1, ContextPro2, ...props } =
  useContext(NameContext);
```

## Exemplo simples de context:

```jsx
import { createContext, useContext } from "react";

export const TodoContext = createContext({
  ...(TipagemDoContext - Props),
});

function ComponentPai() {
  const [anyContent, setAnyContent] = useState("");
  return (
    <TodoContext.Provider value={{ anyContent, setAnyContent }}>
      <ComponentFilho />
    </TodoContext.Provider>
  );
}

function ComponentFilho() {
  return <ComponentNeto />;
}

function ComponentNeto() {
  const { anyContent } = useContext(TodoContext);
  return <Title>anyContent</Title>;
}
```
