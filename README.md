## 🧱 A**RRAYS**

Para realizar o array, você precisa de `[]`.

Chaves vazias também são arrays — não necessariamente apenas se você colocar informações dentro das chaves.

**Lembre-se que arrays são listas.**

---

## ⚙️ **Métodos**

Em um método, você inventa o nome do método e chama dentro dele os parâmetros que encaixam com o método.

**Exemplo:**

```ruby
def profile(name, age, living)
  puts "this is #{name}, they are #{age}, and they are #{living}"
end

```

Agora, para que o computador leia e retorne o valor correto, você precisa determinar o que vai dentro deste parâmetro.

**Exemplo:**

```ruby
profile("Maria", 30, "living")

```

Senão, vai imprimir exatamente `name`, `age` e `living` como palavras vazias, certo?

Ou até retornar erro de código.

---

Mas perceba que vai retornar “alive” e, se eu quisesse que retornasse se a pessoa está viva ou morta?

Poderia fazer:

```ruby
def profile(name, age, living)
  puts "this is #{name}, they are #{age}, and they are #{living}"
end

profile("Maria", 30, "living")

if (living == alive)
  return true
else
  return false
end

```

E assim vai.

---

Também daria para colocar, ao invés de `if (living == alive)`, algo como:

```ruby
puts "alive" if "true"
puts "dead" if "false"
puts "dead" if nil

```

Estamos usando a mesma função, mas essa última chama **IF INLINE**.

Dá para usar sempre que não precisar usar o `else` ou tiver pouca informação, deixando o código em uma linha apenas.

Perceba que no terminal o `false` e `nil` não vão retornar, pois o código será lido apenas com uma condição — a condição verdadeira.

Por isso, se você quer que imprima a falsa ou nula, é necessário usar o `if` com `else`.

---

## ❓ **Função Ternary**

A função **TERNARY** tem como estrutura:

```ruby
condicao ? codigo_que_sera_executado_quando_true : codigo_que_sera_executado_quando_false

```

**Exemplo real:**

```ruby
age >= 16 ? "You can vote!" : "You cannot vote!"

```

Ternários são usados para **economizar linha de código.**

---

Outro exemplo usando `if`:

```ruby
coin = ['heads', 'tails'].sample # vai sortear um ou outro

puts "head or tails?"
guess = gets.chomp.downcase

if (guess == coin)
  return "you won"
else
  return "you lost"
end

puts return

```

A ideia aqui é o usuário não saber — ele vai ter que chutar um ou outro e, se for a escolha do computador, ele vence.

É quase como loteria: não tem resultado predeterminado; o computador decide com o `.sample`.

Se você der a sorte de acertar o mesmo que o PC está pensando, ele emite o resultado de "venceu".

---

Com um ternário, o código ficaria:

```ruby
coin = ['heads', 'tails'].sample # vai sortear um ou outro

puts "head or tails?"
guess = gets.chomp.downcase

result = (guess == coin) ? "You won" : "You lost"

```

**Bem mais limpo!**

---

## 🔢 **Função CASE**

É bem parecida com `if / else / elsif`.

**Exemplo:**

```ruby
puts "welcome to le wagon, would you like to know more about data science, web or data analytics?"
route = gets.chomp.downcase

case route # (rota de infos, opções)
when "web"
  puts "xpto"
when "data science"
  puts "xpto1"
when "data analytics"
  puts "xpto2"
else
  puts "404 not found"
end

```

Perceba que executa a mesma função do `if else` e `elsif`.

---

## ⚙️ **Função AND (&&)**

Ele executa dois retornos quando **ambos** são verdade.

Se um for verdadeiro e o outro falso, ele vai retornar falso.

Só considera verdade se os dois dados são verdadeiros.

**Exemplos:**

```ruby
puts true && true   # vai retornar verdadeiro
puts true && false  # vai retornar falso
puts false && true  # vai retornar falso
puts false && false # vai retornar falso

```

Ele só vai retornar o primeiro como sendo verdadeiro, pois os demais têm dados falsos.

---

### Exemplo com dados numéricos:

```ruby
puts 10 > 5 && 5 > 10

```

Ele retorna **falso**, pois a segunda comparação é falsa.

Agora se eu colocar:

```ruby
puts 4 > 2 && 2 > 4

```

Ele retorna falso, pois o último dado era falso.

E assim vai: sempre que tiver algum dado falso, ele retorna falso, e sempre que ambos os dados forem verdadeiros, retorna verdadeiro.

---

## ⚡ **Função OR (||)**

Essa função retorna verdadeiro se **um dos dois dados é verdadeiro**, mesmo que o outro seja falso.

**Exemplos:**

```ruby
puts true || true   # retorna verdadeiro
puts true || false  # retorna verdadeiro
puts false || true  # retorna verdadeiro
puts false || false # retorna falso

```

---

### Usando na prática:

```ruby
puts "what time is it?"
hour = gets.chomp.to_i

if hour < 12
  puts "good morning"
elsif hour >= 12 && hour < 18
  puts "good afternoon"
else
  puts "good evening"
end

```

Sem o `&&`, ele não retornaria “good evening” pois o código ficaria redundante.

Menor que 12 é dia e maior que 12 é tarde, então mesmo que seja 18 ele retornaria “good afternoon” e não “good evening”.

Por isso a importância do `&&`.

Se eu colocasse `||`, ele retornaria “good afternoon” somente, pois é “um ou outro”.

---

### Exemplo de OR:

```ruby
puts "what time is it?"
hour = gets.chomp.to_i

if hour >= 9 && hour < 12 || hour >= 13 && hour < 18
  puts "le wagon is open"
else
  puts "le wagon is closed"
end

```

Ele vai reproduzir que o horário de abertura da Le Wagon é das 9 às 12 e das 13 às 18.

Entre 12 e 13 e acima de 18 ele retorna que está fechado.

---

## 🔁 **Função WHILE (enquanto)**

**Exemplo:**

```ruby
count = 0

while count <= 5
  puts count
  count = count + 1 # aqui ele vai imprimir o count e somar mais um número
end

```

Isso serve para dar um **looping** na condição.

O computador vai imprimir um número até o 5:

0, depois 1, depois 2, até 5.

Enquanto a contagem for até 5 ele vai imprimir, por isso não chega até 6, pois você incluiu a contagem menor ou igual a 5 (`<= 5`).

---

## ⏳ **Função UNTIL (até que)**

**Exemplo real:**

```ruby
puts "guess the price between 1 and 10"
price = rand(1..10) # o rand executa a função de sortear um número aleatório de 1 até 10
guess = gets.chomp.to_i

until (guess == price) # até que o usuário insira o número que o computador sorteou
  puts "try again"
  guess = gets.chomp.to_i
end

puts "you won"

```

Ou seja, assim que quebrar (`end`) o until, ele vai retornar que o usuário acertou.

E só quebra se o usuário acertar o número por acaso.

## 🔂 **Função FOR**

exemplo real:

```ruby
for number in [1, 2, 3, 4, 5]
  puts number
end

```

ou seja, **para os números da lista (array), imprima o número**

e aí ele vai executar no terminal:

`1, 2, 3, 4, 5`

---

também dá para adicionar mais um número, exemplo:

```ruby
for number in [1, 2, 3, 4, 5]
  puts number + 1
end

```

e aí ele vai executar no terminal:

`2, 3, 4, 5, 6`

> ele não traz o 1 porque o 1 foi adicionado de +1 e virou 2.
> 

---

também poderia ser string:

```ruby
for the_name in [Maria, Joao, Fabricio, roberto]
  puts the_name
end

```

---

## 🧱 **Agora falando de ARRAY**

Array é uma lista que guarda informações que você deseja.

exemplo de um array e funções:

```ruby
pink_floyd = ["Maria", "Jose", "Joao", "Jesus"]

print pink_floyd
print pink_floyd.count

```

aqui ele vai retornar os nomes exatamente como estão, inclusive com aspas e chaves,

e depois trazer a contagem dos dados dentro dessa array, como imprimiria:

```
["Maria", "Jose", "Joao", "Jesus"]
4

```

---

mas se eu quisesse adicionar um nome dentro dessa mesma array, como fazer?

```ruby
pink_floyd.push("Joana")
print pink_floyd
print pink_floyd.size/count

```

vai retornar:

```
["Maria", "Jose", "Joao", "Jesus", "Joana"]
5

```

> para fazer a contagem, podemos usar count ou size, eles fazem a mesma coisa.
> 

---

agora se eu quiser deletar Joana ou qualquer outro nome da array?

eu poderia executar:

```ruby
print pink_floyd[4]

```

> este número dentro das chaves remete-se à posição (index) do nome na lista,
> 
> 
> lembrando que dentro da array a posição começa por 0, então **Joana ocupa a quarta posição da lista e não a quinta.**
> 

depois:

```ruby
pink_floyd.delete_at(4) # delete_at (delete no index)
print pink_floyd

```

ele retornaria a lista de nomes sem o da Joana:

```
["Maria", "Jose", "Joao", "Jesus"]

```

---

agora se eu quisesse alterar alguma palavra ou incluir,

ou colocar em letra maiúscula, minúscula, enfim, executar uma transformação dentro dos nomes da array…

```ruby
pink_floyd[1] = "José Carreiro" # a posição 01 é do Jose, certo?
pink_floyd[3] = "Jesus Cristo"
print pink_floyd

```

vai retornar:

```
["Maria", "Jose Carreiro", "Joao", "Jesus Cristo"]

```

> e assim sucessivamente para qualquer alteração que eu queira fazer.
> 

---

agora se eu quiser deletar outro nome, também posso usar o comando `delete` ao invés do `delete_at`.

> a diferença é que no delete_at você determina o index que deseja apagar,
> 
> 
> já no `delete` você precisa colocar nos parênteses o **dado inteiro**.
> 

exemplo:

```ruby
pink_floyd.delete("Jose Carreiro")
print pink_floyd

```

> retornaria a lista sem o Jose.
> 
> 
> São dois métodos de delete que podem ser usados.
> 

---

vamos supor que eu queira adicionar um dado na lista existente — eu uso o **push**, certo?

exemplo:

```ruby
pink_floyd.push("Jose Carreiro")
print pink_floyd

```

mas em Ruby nós usamos também o **`<<`** que executa exatamente a mesma função e torna teu código mais limpo, com menos letras.

então poderia ser também:

```ruby
pink_floyd << "Jose Carreiro"
print pink_floyd

```

> e apesar do Jose ocupar a posição 01 do index, quando eu adiciono, ele vai pro final da fila,
> 
> 
> assim como qualquer dado que eu adicionar em um array existente.
> 

---

se eu quiser ordenar por ordem alfabética, poderia fazer:

```ruby
pink_floyd.sort
print pink_floyd

```

```
["Maria", "Jose Carreiro", "Joao", "Jesus Cristo"]

```

---

também tem o método **pop**:

```ruby
pink_floyd.pop
print pink_floyd

```

> ele elimina, deleta o último elemento/dado da sua lista.
> 
> 
> neste caso, ele traria a lista sem o último:
> 

```
["Maria", "Jose Carreiro", "Joao"]

```

---

## 🔁 **ITERAÇÃO SIGNIFICA PERCORRER A ARRAY / LISTA**

outra função:

### ➡️ **EACH DO**

ele percorre toda a array e traz a info que você inputar.

exemplo:

```ruby
pink_floyd.each do |member|
  puts "#{member} was a member of pink floyd"
end

```

ele retorna:

```
Maria was a member of pink floyd
Jose Carreiro was a member of Pink Floyd
...

```

> enfim, traz essa info de todos os dados do array.
> 
> 
> neste caso, como são membros, defini `|member|` pra ficar mais didático,
> 
> mas poderia ser qualquer nome representativo do que você está trabalhando na lista.
> 
> se fossem números, poderia ser `number` e não `member`, e por aí vai.
> 

---

agora segue um exemplo de **array vazio** que você irá criar sua lista no código e executar as funções juntas:

```ruby
shopping_list = []

shopping_list.push("monster", "chocolate")
shopping_list << "leite"

```

até aqui sua lista vai retornar:

```
["monster", "chocolate", "leite"]

```

---

quero remover o último?

```ruby
shopping_list.pop

```

vai trazer:

```
["monster", "chocolate"]

```

---

agora vou adicionar outra coisa:

```ruby
shopping_list << "agua"

```

a lista até agora:

```
["monster", "chocolate", "agua"]

```

---

```ruby
shopping_list.delete_at[0] # removi o elemento de index 0, que neste caso era monster
print shopping_list

```

```
["chocolate", "agua"]

```

---

pra ficar bonito, quero que a lista retorne fora das chaves e com letra maiúscula em cada palavra:

```ruby
puts ingredientes.capitalize
end

print shopping_list

shopping_list.each do |ingredientes|

```
