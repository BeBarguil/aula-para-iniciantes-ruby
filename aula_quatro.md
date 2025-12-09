## 📚 Iteração e Blocos em Ruby

### 🔁 O que é iteração?

**Iteração** é o processo de percorrer os elementos de uma lista (ou array) para executar alguma ação com cada um deles.

Um exemplo comum é o uso do método `.each` — ele percorre cada item de uma coleção e executa um bloco de código.

---

### 🧱 O que é um bloco?

Um **bloco** em Ruby é todo trecho de código que começa com uma palavra-chave e termina com `end`.

Por exemplo:

```ruby
if ... end
def ... end
each do ... end

```

Todos esses são **blocos de código** — e cada um tem início e fim bem definidos.

Isso é importante para entender o escopo das variáveis e o comportamento do Ruby.

---

### 📏 Métodos de contagem: `.size`, `.count` e `.length`

Esses três métodos executam **a mesma função**: contam quantos elementos existem dentro de um array.

Exemplo:

```ruby
pink_floyd = ['Maria', 'Jose', 'Joao', 'Jesus']

pink_floyd.count
pink_floyd.size
pink_floyd.length

```

Todos esses retornam:

```
4

```

---

### 🔢 Recapitulando o método Range

Quando você escreve:

```ruby
p (1..10)

```

O Ruby vai **mostrar exatamente o range** `(1..10)` — não a sequência de números.

Para transformá-lo em um array (ou seja, mostrar os números dentro do intervalo), é preciso fazer:

```ruby
p (1..10).to_a

```

Isso retornará:

```
[1,2,3,4,5,6,7,8,9]

```

Note que o último número (10) é **excluído** porque o operador de intervalo `..` vai até o limite anterior.

---

### 🎵 Exemplo prático com um array

```ruby
pink_floyd = ['Maria', 'Jose', 'Joao', 'Jesus']

for index in 0...5  # ou for index in 0...pink_floyd.size
  band_member = pink_floyd[index]
  puts "#{index + 1} - #{band_member}"
end

```

🔍 **Explicação:**

- `0...5` percorre do índice 0 até 4 (o último número é sempre excluído).
- `pink_floyd.size` conta automaticamente quantos elementos tem.
- O `+1` serve apenas para o layout: em vez de começar a contagem em 0, começa em 1.

🖥️ **Saída no terminal:**

```
1 - Maria
2 - Jose
3 - Joao
4 - Jesus

```

---

### 📌 Variáveis de escopo local: `|variavel|`

Quando queremos criar uma **variável que só existe dentro de um bloco**, usamos o símbolo **pipe** (`| |`).

Exemplo:

```ruby
pink_floyd.each do |band_member|
  p "#{band_member} was a member of Pink Floyd"
end

```

🖥️ **Saída:**

```
["Maria was a member of Pink Floyd", "Joao was a member of Pink Floyd", ...]

```

A variável `band_member` existe **somente dentro do bloco** — fora dele, ela deixa de existir.

---

### 📇 O método `each_with_index`

Quando precisamos, além do dado, também da posição dele dentro do array, usamos `each_with_index`.

Exemplo:

```ruby
pink_floyd = ['Maria', 'Jose', 'Joao', 'Jesus']

pink_floyd.each_with_index do |band_member, position|
  p "#{position + 1} - #{band_member}"
end

```

🖥️ **Saída:**

```
1 - Maria
2 - Jose
3 - Joao
4 - Jesus

```

Perceba que o `+1` novamente serve apenas para exibir de forma mais “bonita”.

---

### 🧠 O método `.map`

O `.map` é parecido com o `.each`, mas com uma diferença:

ele **retorna um novo array com as transformações** que você faz dentro do bloco.

Exemplo 1:

```ruby
pink_floyd = ['Maria', 'Jose', 'Joao', 'Jesus']

pink_floyd_upcased = pink_floyd.map do |band_member|
  band_member.upcase
end

puts pink_floyd_upcased

```

🖥️ **Saída:**

```
MARIA
JOSE
JOAO
JESUS

```

Exemplo 2:

```ruby
pink_floyd = ['Maria Carreiro', 'Joao Carreiro']

pink_floyd_names = pink_floyd.map do |band_member|
  band_member.split.first
end

puts pink_floyd_names

```

🖥️ **Saída:**

```
Maria
Joao

```

Aqui, o `.split.first` corta o nome e mantém apenas a primeira palavra.

---

### 🔤 Método `.start_with?`

Esse método verifica **se uma string começa com determinada letra ou conjunto de caracteres**.

Exemplo:

```ruby
pink_floyd = ['Maria', 'Joao', 'Jose', 'Jesus']

pink_floyd_names_with_j = pink_floyd.count do |personagem|
  personagem.start_with?('J')
end

puts pink_floyd_names_with_j

```

🖥️ **Saída:**

```
3

```

(Tem três nomes que começam com “J”: Joao, Jose, Jesus)

---

### 📋 Filtrando dados manualmente

Podemos também **armazenar somente os nomes que começam com “J”**:

```ruby
pink_floyd = ['Maria', 'Joao', 'Jose', 'Jesus']
pink_floyd_names_with_j = []

pink_floyd.each do |band_member|
  pink_floyd_names_with_j << band_member if band_member.start_with?('J')
end

puts pink_floyd_names_with_j

```

🖥️ **Saída:**

```
["Joao", "Jose", "Jesus"]

```

---

### ✅ Fazendo o mesmo com `.select`

Mais simples ainda:

```ruby
pink_floyd_names_with_j = pink_floyd.select do |band_member|
  band_member.start_with?('J')
end

puts pink_floyd_names_with_j

```

🖥️ **Saída:**

```
["Joao", "Jose", "Jesus"]

```

---

### 🚫 Método `.reject`

O `.reject` faz o oposto do `.select`: ele **remove** os itens que atendem à condição.

Exemplo:

```ruby
pink_floyd = ['Maria', 'Joao', 'Jose', 'Jesus']

pink_floyd_names_without_m = pink_floyd.reject do |band_member|
  band_member.start_with?('M')
end

puts pink_floyd_names_without_m

```

🖥️ **Saída:**

```
["Joao", "Jose", "Jesus"]

```

---

### 💡 Refatorando com chaves `{}`

Podemos deixar o código mais enxuto:

```ruby
pink_floyd_names_without_m = pink_floyd.reject { |band_member| band_member.start_with?('M') }

puts pink_floyd_names_without_m

```

Mesmo resultado, mas com código mais legível.

Aqui, usamos `{}` para delimitar o bloco no lugar de `do...end`.

---

### ⚙️ Falando sobre BLOCOS

Reforçando: **todo bloco começa e termina com um método** — geralmente algo seguido de `end`.

Por exemplo:

```ruby
if ... end
def ... end
each do ... end

```

Os blocos são destacados pela coloração no editor (mesma cor no início e no fim), o que ajuda a identificar onde começam e terminam.

---

### ⏱️ O método `yield`

O `yield` é uma ferramenta poderosa em Ruby.

Ele **cria uma pausa (ou barreira)** dentro de um método, permitindo que outro bloco seja executado **naquele ponto específico**.

Exemplo:

```ruby
def timer
  start_time = Time.now

  puts "----------------------"
  puts "Começando a contar quanto tempo leva para executar"

  yield  # ← Aqui é onde o bloco externo será executado

  end_time = Time.now
  puts "Esse método levou #{end_time - start_time} segundos para rodar"
  puts "----------------------"
end

timer do
  puts "Entrando no bloco..."
  sleep(15)
  puts "Saindo do bloco"
end

```

🖥️ **Saída no terminal:**

```
----------------------
Começando a contar quanto tempo leva para executar
Entrando no bloco...
Saindo do bloco
Esse método levou 15 segundos para rodar
----------------------

```

📘 **Explicação:**

- O `yield` marca **onde o segundo método (o bloco)** será executado.
- Tudo **abaixo do `yield`** roda **depois** que o bloco externo termina.
- O `Time` está em letra maiúscula porque é uma **classe Ruby**.

Em Ruby, se você tem um array de números, como por exemplo:

```ruby
numbers = [1, 2, 3, 4, 5]

```

você pode somar todos os elementos de forma **muito simples** usando o método `.sum`:

```ruby
numbers.sum

```

💡 **O que acontece aqui:**

- O Ruby percorre **cada elemento do array** `numbers`.
- Ele **adiciona todos os valores** juntos, gerando uma soma total.

🖥️ **Saída no terminal:**

```
15

```

✅ **Explicação passo a passo:**

1. O array contém `[1, 2, 3, 4, 5]`.
2. O método `.sum` pega cada número e vai somando:
    - 1 + 2 = 3
    - 3 + 3 = 6
    - 6 + 4 = 10
    - 10 + 5 = 15
3. O resultado final é `15`.
