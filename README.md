# Fundamentos do Go
Esse texto vai apresentar minhas observações sobre a linguagem Go. 
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

É algo parecido com a definição de acesso que temos no Java, com `public` e `private`, por exemplo. No Go, utilizamos a primeira letra do método/atributo para indicar se ele pode ou não ser utilizado fora do pacote.

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
