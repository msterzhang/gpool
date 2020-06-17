# gpool
Golang控制线程数，防止创建无线线程。

### 代码用例:

```
package main

import (
	"fmt"
	"github.com/msterzhang/gpool"
)

func RunTest(i int,pool *gpool.Pool)  {
	fmt.Println(i)
	pool.Done()
}

func main()  {
	size:=2
	pool := gpool.New(size)
	for i:=1;i<=10;i++{
		pool.Add(1)
		go RunTest(i,pool)
	}
	pool.Wait()
}
```
### 结果输出：

```
2
1
4
3
5
7
8
9
6
10

Process finished with exit code 0
```
