# Ruby Notes

## IRB (Interactive Ruby) e Terminal

Para rodar seu código Ruby no terminal do VSCode:

```bash
ruby nome_do_arquivo.rb
```

Ou para modo interativo:

```bash
irb
```

---

## Printando no Terminal

Para printar use `puts`:

```ruby
puts "Hello World"
```

---

## Conversões

```ruby
motivation = "10".to_i  # Converte string para inteiro
```

---

## Comentários em Ruby

Use `#` para comentar uma linha:

```ruby
# Isso é um comentário
puts "Isso executa"
```

---

## Ruby é Orientado a Objetos

O objeto é a unidade básica do código. Objetos podem guardar informações, instruções, etc. Objetos semelhantes se agrupam em classes.

```ruby
puts 'le wagon'.class   # => String
777.class               # => Integer
3.14.class              # => Float
(1..100).class          # => Range
```

---

## Array

É um conjunto de objetos ou uma lista:

```ruby
["le wagon", 777, 3.14]
```

---

## Strings

String = texto

```ruby
print "I am".upcase      # => "I AM"
print "I am".downcase    # => "i am"
```

---

## Atribuição e Comparação

- `=` atribui valor à variável
- `==` compara valores

```ruby
nome = 'maria'              # atribui
print 'Maria' == 'Maria'    # => true
p nome == 'maria'           # => true
```

---

## Interpolação e Concatenação

Interpolação usa `#{ }` para executar código dentro de uma string:

```ruby
p "two: #{1 + 1}"   # => "two: 2"
```

Concatenação junta strings com `+`:

```ruby
p "two:" + " 2"     # => "two: 2"
```

---

## Conversão entre Tipos

```ruby
p "1984".to_i          # => 1984 (string para integer)
p 1984.to_s            # => "1984" (integer para string)
p "".to_i              # => 0
```

---

## Verificando Par ou Ímpar

```ruby
print 42.even?   # => true
print 42.odd?    # => false
```

Métodos com `?` retornam `true` ou `false` (boolean).

---

## Arredondamento com Float

```ruby
p 1.314.round   # => 1
p 1.618.round   # => 2
```

---

## Divisão em Ruby

```ruby
p 3 / 2       # => 1 (inteiros retornam inteiro)
p 3.0 / 2.0   # => 1.5 (floats retornam decimal)
```

---

## Range (Intervalos)

```ruby
p (1..10).to_a    # => [1,2,3,4,5,6,7,8,9,10] (inclui o 10)
p (1...10).to_a   # => [1,2,3,4,5,6,7,8,9] (exclui o 10)
```

---

## Mais sobre Arrays

```ruby
p ['zero', 'four', 'five', 'one'].size   # => 4
p [0, 4, 5, 1].sort                       # => [0, 1, 4, 5]
```

Mistura de tipos causa erro no `.sort`:

```ruby
p [0, 'four', 5, 'one'].sort   # => ERRO
```

---

## Índices de Array

Arrays começam no índice 0:

```ruby
arr = ['a', 'b', 'c']
arr[0]   # => 'a'
arr[1]   # => 'b'
arr[2]   # => 'c'
```

---

## Booleanos

- `true` e `false`
- Métodos com `?` retornam booleanos

---

## Variáveis

Guardam informações:

```ruby
age = 12
puts "you are #{age} years old"   # => "you are 12 years old"

age = age + 1   # ou age += 1
puts "you are #{age} years old"   # => "you are 13 years old"
```

---

## Métodos

Um pedaço de código reutilizável. Começa com `def`, termina com `end`:

```ruby
def say_hi(name)
  return "Hi " + name + "."
end

puts say_hi("eduardo")   # => "Hi eduardo."
puts say_hi("maria")     # => "Hi maria."
```

---

## Método com Nome e Sobrenome

```ruby
def says_hello(first_name, last_name)
  return "Hello #{first_name.capitalize} #{last_name.capitalize}!"
end

puts says_hello("john", "lennon")   # => "Hello John Lennon!"
```

---

## Número Aleatório

```ruby
def random_number
  return rand(100)   # número entre 0 e 99
end

puts random_number
```

---

## Parâmetros vs Argumentos

- **Parâmetros**: o que o método espera receber (`x`, `y`)
- **Argumentos**: valores passados (`20`, `35`)

```ruby
def add(x, y)
  return x + y
end

puts add(20, 35)   # => 55
```

---

## Boas Práticas

- Leia a documentação
- Nomeie bem seus métodos e variáveis
- Siga o padrão Ruby (snake_case)

Exemplo ruim:

```ruby
def method_X(firstParameter, secondParameter)
  # não é intuitivo
end
```

Exemplo bom:

```ruby
def calculate_total(price, quantity)
  return price * quantity
end
```

---

## Dividindo Strings com .split

```ruby
"All you need is code".split
# => ["All", "you", "need", "is", "code"]
```

O `.split` quebra a string onde tiver espaços e transforma em array.
