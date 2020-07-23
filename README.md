# Fundamentos do GO

Esse texto vai apresentar minhas observações sobre a linguagem Go. 

Go é uma linguagem de programação de código aberto que facilita a criação de software simples, confiável e eficiente. Toda a sua especificação pode ser encontrada aqui [https://golang.org/ref/spec](https://golang.org/ref/spec). 

Levando em conta outras linguagens de programação como Java e C# que estão no mercado há muito tempo, o Go pode ser considerado uma linguagem "nova" que utiliza isso como benefício: A linguagem foi criada na "era dos processadores dual core" e foi otimizada para isso.

Para a criação do mesmo, utilizei a documentação presente em [Um tor por Go](https://go-tour-br.appspot.com/basics/3) e no curso [Web Development w/ Google’s Go (golang) Programming Language](https://www.udemy.com/course/go-programming-language)

### Importanto pacotes

```go
package main

import (
	"fmt"
	"math/rand"
)

func main() {
	fmt.Println("My favorite number is", rand.Intn(10))
}
```

Pontos importantes sobre a importação de pacotes:

- Por convenção, o nome do pacote é o mesmo que o último elemento do caminho de importação. Por exemplo, o pacote `math/rand` compreende arquivos que começam com package rand.

Os imports também podem ser feitos da seguinte maneira:

```go
import "fmt"
import "math"
```

Porém, a comunidade indica que é uma boa prática utilizar o modelo proposto no primeiro exemplo, denominado **consignado**.

### Utilizando métodos fora do pacote

É algo parecido com a definição de acesso que temos no Java, com `public` e `private`, por exemplo. No GO, utilizamos a primeira letra do método/atributo para indicar se ele pode ou não ser utilizado fora do pacote.

O exemplo abaixo retornará um erro:

```go
package main

import (
	"fmt"
	"math"
)

func main() {
	fmt.Println(math.pi)
}
```

Altere pi para Pi e rode novamente.

### Funções e Métodos

Funções e métodos são amplamente utilizados no Go para fornecer abstrações e facilitar a leitura e raciocínio de nossos programas.

Uma função é declarada especificando os tipos dos argumentos, os valores de retorno e o corpo da função:

```go
type Car struct {
	Name string
	Color string
}

// Uma função para criar uma nova instância de um Car (carro)
func NewCar(name string, color string) *Car {
    return &Person {
       Name: name,
       Color: color,
    }
}
```

Um método, por outro lado, é declarado especificando adicionalmente o "receptor" (que em termos de OOP seria a "classe" que possui o método):

```go
// Verifica se um carro é azul um fusca azul
func (p *Person) isBlueFusca() bool {
    return p.Name == "Fusca" && p.Color == "Azul"
}
```

Para executar os dois métodos, temos:

```go
myNewCar := NewCar("Fusca", "Azul")
fmt.Println(myNewCar.isBlueFusca())
```

Uma sacada interessante do Go é permitir que você retorne mais de um atributo a partir de sua `func`.

```go
func invert(x string, y string) (string, string) {
    // esse exemplo é muito ruim. Mas deu para sacar as possibilidades, certo?
    return y, x
}

func main() {
    x, y := invert("hello", "world")
    fmt.Println(x, y)
}
```

Outro ponto que vai te ajudar a manter um código mais limpo e objetivo é permitir que você nomeie os atributos de retorno na declaração de sua `func`.

```go
func getAccountInfo(accountCode int) (name string, email string) {
    // getName && getEmail / account
    name = account.name
    email = account.email
    return
}
```

### Declarando uma variável

Usado em diversas linguagens, como no Kotlin, o `var` permite que você declare uma ou mais variaveis por linha.

```go
var score int
// Declara um int

var neymar, messi, bigrobot bool
// Declara 3 boleanos
```

Você também pode atribuir um valor ao criar uma variável - não que isso seja uma particularidade do Go.

```go
var i, j int = 1, 2
```

Eu particularmente não acho que declarar várias variáveis em uma linha seja uma boa abordagem para o seu código do dia a dia. Economizar linhas não significa manter um código limpo e muitas vezes pode ser um tiro no pé.

Dentro de uma `func` você ainda pode optar pela abordagem *short variable declarations*.

```go
messiWorldCups:= 0
vampetaWorldCups:= 1

// Afinal, Messi não tem copa, quem tem copa é o Vampeta
```

Ao declarar uma variável sem atribuir o valor, seu valor padrão será "zero" e não null - atenção aos amigos javeiros.

```go
0 para tipos numéricos,
false para tipos boleanos, e
"" (string vazia) para strings.
```

### Declarando uma constante

Similar a uma variável, a constante pode ser declarada dentro e fora de uma `func`. Use a palavra-chave `const` e defina seu nome e valor.

```go
const FlatEarthIsReal = false //
```
