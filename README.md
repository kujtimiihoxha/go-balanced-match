# Go balanced match
This is a go implementation of [balanced-match](https://github.com/juliangruber/balanced-match)

### Usage 
```go
package main

import (
	"github.com/kujtimiihoxha/go-balanced-match"
	"fmt"
	"regexp"
)

func main() {
	v:= goblma.Balanced("{","}","pre{in{nested}}post")
	fmt.Println(v) //=> { Start:3, End:14, Pre:"pre", Body:"in{nested}" Post:"post"}

	v= goblma.Balanced("{","}","pre{first}between{second}post")
	fmt.Println(v) //=> { Start:3, End:9, Pre:"pre", Body:"first" Post:"between{second}post"}

	//Regex example
	regStart := regexp.MustCompile(`\s+\{\s+`)
	regEnd := regexp.MustCompile(`\s+\}\s+`)
	v= goblma.Balanced(regStart,regEnd,"pre  {   in{nest}   }  post")
	fmt.Println(v) //=> { Start:3, End:17, Pre:"pre", Body:"in{nested}" Post:"post"}


}
```