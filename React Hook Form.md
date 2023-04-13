# React Hook Form - Trabalhando com formulários no React

O React Hook Form é uma biblioteca para trabalhar com formulários.

É uma biblioteca bem simples que facilita a manipulação de formulários e validação de erros.

## Estrutura inicial

```JSX
import { userForm } from 'react-hook-form'

const form {register, watch, handleSubmit, formState} = useForm()
```

### Register

- Faz com que o input seja observado pelo react hook form.

Exemplo de utilização:

```JSX
<input type='text' {...register('inputName')}>
```

### HandleSubmit

- handleSubmit(() => (submitActions)) >> É passado no método submit do formulário que será executado quando o form for submetido

### Watch

- watch('inputName') >> Transforma o input em um controled input, ou seja, toda alteração será vista/observada

### FormState

- formState >> Verifica o estado atual do formulário, se possui erros ou não

## Validando Formulários com Zod

yarn add zod
yarn add @hookform/resolvers

import \* as zod from 'zod'
import { zodResolver } from '@hookform/resolvers/zod'

const formValidationSchema = zod.object({
fild01: zod.string().min(1, 'message error min').max(180, 'message error > 180'),
filed02: zod.number().min(5).max(60)
})

const { register, watch, handleSubmit } = useForm({
resolver: zodResolver(formValidationSchema)
})

<input type="number" {...register('idade', { valueAsNumber: true })} />
