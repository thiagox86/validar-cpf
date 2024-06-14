## Regras para Validar um CPF

Pense no CPF como uma sequência de 11 números que seguem um padrão específico, algo como “###.###.###-##”, onde cada ‘#’ é um número. Agora, a parte interessante é como verificamos se um CPF é válido ou não.

Para fazer isso, pegamos os primeiros 9 números do CPF e fazemos um cálculo simples. Depois, verificamos se o resultado desse cálculo corresponde aos dois últimos números do CPF (aqueles depois do “-”).

Então, basicamente, a validação do CPF é como um pequeno jogo de quebra-cabeça onde usamos matemática para verificar se todas as peças se encaixam corretamente!

## Validando o Primeiro Dígito

Primeiramente multiplica-se os 9 primeiros dígitos pela sequência decrescente de números de 10 à 2 e soma os resultados. Assim:

> 4 * **10** + 5 * **9** + 4 * **8** + 9 * **7** + 9 * **6** + 5 * **5** + 5 * **4** + 5 * **3** + 0 * **2**

O resultado do nosso exemplo é:

> **29**4

O próximo passo da verificação também é simples, basta multiplicarmos esse resultado por 10 e dividirmos por 11.

> 294 * **10** / **11**

O resultado que nos interessa na verdade é o RESTO da divisão. Se ele for igual ao **primeiro dígito verificador** (primeiro dígito depois do ‘-‘), a primeira parte da validação está correta.

**Observação Importante:** Se o resto da divisão for igual a 10, nós o consideramos como 0.

Vamos conferir o primeiro dígito verificador do nosso exemplo:

> O resultado da divisão acima é ‘267’ e o RESTO é 3

Isso significa que o nosso CPF exemplo passou na validação do primeiro dígito.

## Validando o Segundo Dígito

A validação do segundo dígito é semelhante à primeira, porém vamos considerar os 9 primeiros dígitos, mais o primeiro dígito verificador, e vamos multiplicar esses 10 números pela sequencia decrescente de 11 a 2. Vejamos:  _45499555036_

> 4 * **11** + 5 * **10** + 4 * **9** + 9 * **8** + 9 * **7** + 5 * **6** + 5 * **5** + 5 * **4** + 0 * **3** + 3 * **2**

O resultado é:

> **346**

Seguindo o mesmo processo da primeira verificação, multiplicamos por 10 e dividimos por 11.

> 346 * **10** / **11**

Verificando o RESTO, como fizemos anteriormente, temos:

> O resultado da divisão é ‘314’ e o RESTO é 6

Verificamos, se o resto corresponde ao segundo dígito verificador.

Com essa verificação, constatamos que o CPF _454.995.550-36_  é válido.

## CPFs Conhecidos que são Inválidos

Você sabia que alguns CPFs podem passar na validação que mencionamos, mas ainda assim não são válidos? Isso acontece quando todos os dígitos do CPF são iguais, como “111.111.111-11” ou “222.222.222-22”. Mesmo que esses números sigam o formato correto e passem na verificação matemática, eles não são considerados CPFs válidos.

Então, em nosso algoritmo, vamos adicionar uma etapa extra. Antes de tudo, vamos verificar se todos os dígitos do CPF são iguais. Se forem, vamos considerar esse CPF como inválido, mesmo que ele passe nas outras verificações.

Assim, garantimos que nosso algoritmo está verificando os CPFs corretamente!

## Código Explicado

1.  **Estilo CSS**: O código CSS está definindo o estilo para um elemento de entrada e um botão dentro de um div com o id  `tr-div-cpf`. Ele define a largura, a margem inferior, a altura e o tamanho da fonte desses elementos.
2.  **HTML**: O código HTML cria um campo de entrada numérico e um botão. O campo de entrada aceita apenas números e chama a função  `apenasNumeros(event)`  a cada pressionamento de tecla para garantir isso. O botão, quando clicado, chama a função  `validaCPF()`.
3.  **JavaScript**: Existem três funções JavaScript aqui:
    -   `apenasNumeros(e)`: Esta função é chamada a cada pressionamento de tecla no campo de entrada. Ela verifica se a tecla pressionada é um número e, se não for, impede a entrada.
    -   `validaCPF()`: Esta função é chamada quando o botão é clicado. Ela primeiro verifica se o campo de entrada está vazio ou se o CPF inserido tem menos ou mais de 11 dígitos. Se qualquer uma dessas condições for verdadeira, ela exibe um alerta e limpa o campo de entrada. Se o CPF passar nessas verificações iniciais, a função então verifica se todos os dígitos do CPF são iguais. Se forem, ela considera o CPF inválido. Se não forem, ela realiza a validação matemática do CPF, verificando os dígitos verificadores.
    -   `limpaInput()`: Esta função simplesmente limpa o campo de entrada, definindo seu valor como uma string vazia.
