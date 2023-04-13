# TypeScript


## Os principais motivos para se utilizar TypeScript
- Tipagem de variáveis e componentes
- Maior facilidade na visualização de erros
- IDE mais inteligente, nos auxiliando no desenvolvimento




## Dicas de utilização do TypeScript
- Crie types para as props dos componentes
- Em funções que utilizam o event é necessário informar qual o tipo desse event e por qual elemento ele foi disparado. Ex: FormEvent, ChangeEvent<HTMLTextAreaElement>, InvalidEvent<HTMLTextAreaElement>,
- Tipagem em funções:
	- Funções sem retorno devem ser do tipo void
- Podemos definir tipagens com propriedades opcionais. Para isso é necessário informar com o ?. Ex: ```{ isOptional?: boolean; }```



## Extensão de interfaces ( herdando propriedades HTML nos components React )
- Faz com que seja possível usar as propriedades de um elemento HTML em um componente React, sem que seja necessário informar as propriedades uma a uma via props.
Ex: 
interface ComponentProps extends ImgHTMLAttributes<HTMLImageElement>
		ComponentProps(...props){<img {...props} />}
		Neste exemplo o ComponentProps irá herdar todas as propriedades que uma img html possui 
		E quando alguem inserir no elemento ComponentProps uma propriedade ela será automatica passada para o ComponentProps por causa do rest operator <img {...props} />
	


























































