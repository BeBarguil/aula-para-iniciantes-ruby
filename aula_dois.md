# Métodos em Ruby - Guia Prático

Um guia completo sobre como criar e utilizar métodos em Ruby, com exemplos práticos e explicações detalhadas.

---

## 1. Exemplo de método: `replace`

```ruby
def replace(Maria, m, l)
  Maria.gsub(m, l)
end

puts replace("maria", "m", "l")
```

### Explicação

Na função, a palavra `replace` serve apenas para **nomenclatura** do que você irá executar. Ela poderia ser qualquer nome, pois é apenas a identificação do que será feito.

Logo após, coloco dentro de parênteses as letras que quero substituir uma pela outra. A primeira será substituída pela última — neste caso, o "m" será substituído pelo "l".

Repare que não precisei colocar aspas dentro dos parênteses, pois se trata apenas de um parâmetro para quem ler entender o que você quer executar. Esses parâmetros são apenas "palavras vazias", por assim dizer.

A partir daí, chamo de fato a função que vai executar aquela substituição. Sempre coloco o nome que deve ser referência da substituição junto da função, para o código ser lido corretamente. Essa é a lógica.

Neste caso, como a palavra a ser substituída é "maria", coloco `maria.gsub`, pois o `gsub` é a função que vai executar o código. Em seguida, coloco as letras que devem ser substituídas (exemplo: o `m` e o `l`). Aqui também não preciso colocar parênteses, e finalizo este método com `end`.

Sempre que o método é finalizado, é preciso usar o `puts` para imprimir o resultado da função que está sendo executada dentro do método.

---

## 2. Outros exemplos com funções diferentes

### Exemplo 1: `get_rid_of_surrounding_whitespaces`

```ruby
def get_rid_of_surrounding_whitespaces(string)
  string.strip
end

puts get_rid_of_surrounding_whitespaces("  get rid of surrounding whitespaces  ")
```

Aqui vai retornar a frase retirando os espaços após as aspas.

---

### Exemplo 2: `belongs_to?`

```ruby
def belongs_to?(full_string, substring)
  full_string.include?(substring)
end

puts belongs_to?("hey jude", "jude")
puts belongs_to?("hey jude", "joe")
```

Aqui você está pedindo para retornar verdadeiro ou falso se na palavra "hey jude" tem a palavra "jude" ou "joe". Veja que não é preciso explicar a resposta.

Em `def belongs_to?` você colocou dentro dos parênteses seus parâmetros: a primeira string principal (que é `"hey jude"`) e a substring, que é a segunda palavra a ser avaliada (`"jude"` ou `"joe"`).

Em Ruby, há alguns parâmetros obrigatórios e outros opcionais. Quando são obrigatórios, você precisa inputá-los corretamente, senão dá erro de sintaxe.

---

### Exemplo 3: `exactly_divide`

```ruby
def exactly_divide(dividend, divisor)
  13.0 / 4
end

puts exactly_divide(13, 4)
```

Perceba que, assim como nos outros códigos, defini parâmetros — `dividend` (dividendo) e `divisor`. Se colocasse algo como `"números"` ou `"número 1 e número 2"`, ele não aceitaria, mesmo que o resto estivesse certo.

A lógica é a mesma, mas com a exceção de que você precisa imputar a regra matemática como parâmetro.

> **Dica:** Para retornar decimal, é necessário que um dos números da fórmula tenha `.0`. Não precisa ser os dois — apenas um já faz o Ruby retornar um número "float" (decimal).

---

## 3. Erro comum: redefinir o mesmo método duas vezes

Se você quer que um número retorne verdadeiro ou falso se é divisível por 2, **não pode definir dois métodos com o mesmo nome**, pois o Ruby vai ignorar o primeiro e considerar o último.

### Exemplo incorreto

```ruby
def divisible_by_two?(divisor)
  if 6 % 2 == 0
    true
  else
    false
  end
end

def divisible_by_two?(divisor)
  if 7 % 2 == 0
    true
  else
    false
  end
end
```

Aqui ele retorna apenas o odd (7) e faltou o teste do primeiro. Isso aconteceu porque defini dois métodos com o mesmo nome e função (`divisible_by_two?`).

### Forma correta

```ruby
def divisible_by_two?(number)
  if number % 2 == 0
    true
  else
    false
  end
end

puts divisible_by_two?(6)
puts divisible_by_two?(7)
```

Perceba que aqui o parâmetro deixou de ser `divisor` porque não queria mais considerar apenas o que era divisível, mas também o que não era. Por isso, alterei para `number`, para que o código considerasse tanto a avaliação do número 6 quanto do 7.

---

## Resumo final e lógica geral

| Conceito | Descrição |
|----------|-----------|
| Nome do método | A palavra após `def` é apenas o nome do método e pode ser qualquer uma |
| Parâmetros | Os valores dentro dos parênteses são variáveis de entrada |
| Lógica | Dentro do método, você coloca a lógica que será executada |
| Finalização | O método termina com `end` |
| Impressão | Fora dele, você usa o `puts` para imprimir o resultado |
| Métodos com `?` | Retornam `true` ou `false` |
| Métodos com `!` | Alteram o valor original da variável |
| Nomes duplicados | Ruby não aceita métodos com nomes duplicados (o último sobrescreve) |

---

## Conclusão

Método em Ruby é uma forma organizada e reutilizável de escrever instruções. Você dá um nome (como `replace`), define parâmetros, escreve a lógica, e depois chama o método com `puts` para ver o resultado.

A chave é entender a função dos parâmetros e como o Ruby interpreta a execução — isso evita erros e deixa seu código claro e eficiente.
