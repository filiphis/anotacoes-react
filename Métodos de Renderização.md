# Métodos de Renderização

Existem algumas estratégias consolidadas pela comunidade para entregar conteúdo aos usuários através de páginas Web.

Não existe uma estratégia melhor ou pior, mas sim uma que mais se adapta a cada tipo de página web.

O que difere entre essas estratégias é: **Quando e Onde o Javascript é executado para gerar o HTML**

## Renderização no lado do CLIENTE

### CSR − Client Side Rendering

- Renderização no lado do cliente
- O Javascript usado para gerar o HTML é executado completamente no lado do cliente, ou seja, no browser.

#### Utilização no NEXT

### SPA − Single Page Application

- Renderização no lado do cliente
- O Javascript usado para gerar o HTML é executado completamente no lado do cliente, ou seja, no browser.
- **Melhor experiência ao usuário após o primeiro carregamento da página.**
- _Traz na primeira requisição o conteúdo necessário para permitir uma navegação praticamente instantânea._
- **SPAs também podem ser renderizadas no lado servidor.**
- Vantagens:
  - Interação sem precisar recarregar a página.
  - Carga no servidor reduzida.
- Desvantagens:
  - Performance pode ser imprevisível pois toda carga é processada no cliente.
  - Alguns indexadores não conseguem ler javascript, prejudicando o SEO da página.

#### Utilização no NEXT

## Renderização no lado do SERVIDOR

### SSR − Server Side Rendering

- Renderização no lado do servidor
- O Javascript usado para gerar o HTML é executado no lado do servidor **a cada requisição**.
- _Ótimo SEO, visto que a página é entregue já renderizada._
- Um SSR pode prover uma SPA.
- Desvantagens:
  - TTFB (Time To First Byte) alto, visto que o servidor precisa renderizar o conteúdo antes de enviar a resposta para o cliente.
  - Página apenas se torna interativa na finalização do carregamento, o que pode causar estranheza caso exista muita demora do momento da exibição da página até a finalização do carregamento.

#### Utilização no NEXT

- getServerSideProps()

### SSG − Static Site Generation

- O SSG se assemelha bastante ao SSR
- Renderização no lado do servidor
- O Javascript usado para gerar o HTML é executado no lado do servidor, porém isso acontece em **tempo de build**.
- _A página é gerada apenas uma vez e mantida no cache do servidor_.
- Todos os requests para essa página irão retornar exatamente o mesmo HTML.
- Vantagens:
  - **Melhor performance**.
  - _Possui os mesmos benefícios do SSR quanto ao SEO_.
  - **Boa para páginas onde o conteúdo não é dinâmico**.
- Desvantagens:
  - Não é uma boa opção para páginas dinâmicas ( conteúdo atualiza constantemente).

#### Utilização no NEXT

- getStaticProps()

- Por padrão todas as páginas do Next são geradas como SSG (estáticas em tempo de build).
- **Para casos onde _não_ é preciso acessar uma API**, não precisamos de nenhum passo extra.

- Se precisarmos acessar uma API é necessário utilizar a função _getStaticProps_.

- A função _getStaticProps_ é executada antes do build da página.

  Exemplo:

```tsx
export async function getStaticProps() {
  const res = await fetch("https://.../productId");
  const product = await res.json();

  return {
    props: {
      product,
    },
  };
}

function ProductDetails({ product }) {
  return <div>{product.name}</div>;
}
```

### ISR − Incremental Static Regeneration

- O SSG se assemelha bastante ao SSG
- Renderização no lado do servidor
- O Javascript usado para gerar o HTML é executado no servidor em tempo de _build_, **porém essa página é gerada novamente continuamente em um intervalo de tempo específico**.
- _É um SSG que realiza o build em um intervalo determinado_

#### Utilização no NEXT

- getStaticProps() + revalidate

## Utilizando NEXT

As páginas do NEXT podem ou não ser pré-renderizadas.
Existem dois tipos de pré-renderização:

1. Static Generation (SSG)

- getStaticProps()
- getStaticProps() + revalidate == ISR − Incremental Static Regeneration
- getStaticPaths() + getStaticProps() == Gerando páginas dinamicamente.

2. Server-side Rendering (SSR)

- getServerSideProps()
