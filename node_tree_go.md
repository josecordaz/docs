
<details>
<summary>Example file</summary>

```go
package main

import (
	"fmt"
)

func d1() {
	for i := 3; i > 0; i-- {
		defer fmt.Print(i, " ")
	}
}

func d2() {
	for i := 3; i > 0; i-- {
		defer func() {
			fmt.Print(i, " ")
		}()
	}
	fmt.Println()
}

func d3() {
	for i := 3; i > 0; i-- {
		defer func(n int) {
			fmt.Println(n, " ")
		}(i)
	}
}

func main() {
	d1()
	d2()
	fmt.Println()
	d3()
	fmt.Println()
}

```
</details>


### This shows node tree

```shell
go tool compile -W main.go
```

<details>
<summary>Output</summary>

```shell
before d1
.   DCL l(8)
.   .   NAME-main.i a(true) g(1) l(8) x(0) class(PAUTO) f(1) tc(1) assigned used int

.   AS l(8) colas(true) tc(1)
.   .   NAME-main.i a(true) g(1) l(8) x(0) class(PAUTO) f(1) tc(1) assigned used int
.   .   LITERAL-3 l(8) tc(1) int

.   FOR l(8) tc(1)
.   .   GT l(8) tc(1) bool
.   .   .   NAME-main.i a(true) g(1) l(8) x(0) class(PAUTO) f(1) tc(1) assigned used int
.   .   .   LITERAL-0 l(8) tc(1) int
.   .   BLOCK l(8)
.   .   BLOCK-list
.   .   .   AS l(8) tc(1)
.   .   .   .   NAME-main..autotmp_2 a(true) l(8) x(0) class(PAUTO) esc(N) tc(1) assigned used int
.   .   .   .   NAME-main.i a(true) g(1) l(8) x(0) class(PAUTO) f(1) tc(1) assigned used int

.   .   .   AS l(8) tc(1) implicit(true) int
.   .   .   .   NAME-main.i a(true) g(1) l(8) x(0) class(PAUTO) f(1) tc(1) assigned used int
.   .   .   .   SUB l(8) tc(1) int
.   .   .   .   .   NAME-main..autotmp_2 a(true) l(8) x(0) class(PAUTO) esc(N) tc(1) assigned used int
.   .   .   .   .   LITERAL-1 l(8) tc(1) int

.   .   .   VARKILL l(8) tc(1)
.   .   .   .   NAME-main..autotmp_2 a(true) l(8) x(0) class(PAUTO) esc(N) tc(1) assigned used int
.   FOR-body
.   .   AS l(9) tc(1)
.   .   .   NAME-main..autotmp_1 a(true) l(9) x(0) class(PAUTO) esc(N) tc(1) assigned used int
.   .   .   NAME-main.i a(true) g(1) l(8) x(0) class(PAUTO) f(1) tc(1) assigned used int

.   .   DEFER l(9) tc(1)
.   .   .   CALLFUNC l(9) tc(1) STRUCT-(int, error)
.   .   .   .   NAME-fmt.Print a(true) l(4) x(0) class(PFUNC) tc(1) used FUNC-func(...interface {}) (int, error)
.   .   .   .   DDDARG l(9) esc(h) PTR64-*[2]interface {}
.   .   .   CALLFUNC-list
.   .   .   .   CONVIFACE l(9) esc(h) tc(1) implicit(true) INTER-interface {}
.   .   .   .   .   NAME-main..autotmp_1 a(true) l(9) x(0) class(PAUTO) esc(N) tc(1) assigned used int

.   .   .   .   CONVIFACE l(9) esc(h) tc(1) implicit(true) INTER-interface {}
.   .   .   .   .   NAME-main.statictmp_0 a(true) l(9) x(0) class(PEXTERN) f(1) tc(1) used string

.   .   VARKILL l(9) tc(1)
.   .   .   NAME-main..autotmp_1 a(true) l(9) x(0) class(PAUTO) esc(N) tc(1) assigned used int
after walk d1
.   DCL l(8)
.   .   NAME-main.i a(true) g(1) l(8) x(0) class(PAUTO) f(1) tc(1) assigned used int

.   AS l(8) colas(true) tc(1)
.   .   NAME-main.i a(true) g(1) l(8) x(0) class(PAUTO) f(1) tc(1) assigned used int
.   .   LITERAL-3 l(8) tc(1) int

.   FOR l(8) tc(1)
.   .   GT l(8) tc(1) bool
.   .   .   NAME-main.i a(true) g(1) l(8) x(0) class(PAUTO) f(1) tc(1) assigned used int
.   .   .   LITERAL-0 l(8) tc(1) int
.   .   BLOCK l(8)
.   .   BLOCK-list
.   .   .   AS l(8) tc(1)
.   .   .   .   NAME-main..autotmp_2 a(true) l(8) x(0) class(PAUTO) esc(N) tc(1) assigned used int
.   .   .   .   NAME-main.i a(true) g(1) l(8) x(0) class(PAUTO) f(1) tc(1) assigned used int

.   .   .   AS l(8) tc(1) implicit(true) int
.   .   .   .   NAME-main.i a(true) g(1) l(8) x(0) class(PAUTO) f(1) tc(1) assigned used int
.   .   .   .   SUB l(8) tc(1) int
.   .   .   .   .   NAME-main..autotmp_2 a(true) l(8) x(0) class(PAUTO) esc(N) tc(1) assigned used int
.   .   .   .   .   LITERAL-1 l(8) tc(1) int

.   .   .   VARKILL l(8) tc(1)
.   .   .   .   NAME-main..autotmp_2 a(true) l(8) x(0) class(PAUTO) esc(N) tc(1) assigned used int
.   FOR-body
.   .   AS l(9) tc(1)
.   .   .   NAME-main..autotmp_1 a(true) l(9) x(0) class(PAUTO) esc(N) tc(1) addrtaken assigned used int
.   .   .   NAME-main.i a(true) g(1) l(8) x(0) class(PAUTO) f(1) tc(1) assigned used int

.   .   DEFER-init
.   .   .   AS l(9) tc(1) hascall
.   .   .   .   NAME-main..autotmp_4 a(true) l(9) x(0) class(PAUTO) esc(N) tc(1) assigned used PTR64-*[2]interface {}
.   .   .   .   CALLFUNC l(9) tc(1) nonnil hascall PTR64-*[2]interface {}
.   .   .   .   .   NAME-runtime.newobject a(true) x(0) class(PFUNC) tc(1) used FUNC-func(*byte) *[2]interface {}
.   .   .   .   CALLFUNC-list
.   .   .   .   .   AS l(9) tc(1)
.   .   .   .   .   .   INDREGSP-SP a(true) l(9) x(0) tc(1) addrtaken main.__ PTR64-*byte
.   .   .   .   .   .   ADDR a(true) l(9) tc(1) PTR64-*uint8
.   .   .   .   .   .   .   NAME-type.[2]interface {} a(true) x(0) class(PEXTERN) tc(1) uint8

.   .   .   BLOCK l(9)
.   .   .   BLOCK-list
.   .   .   .   AS l(9) tc(1) hascall
.   .   .   .   .   NAME-main..autotmp_5 a(true) l(9) x(0) class(PAUTO) esc(N) tc(1) assigned used INTER-interface {}
.   .   .   .   .   CALLFUNC l(9) tc(1) hascall INTER-interface {}
.   .   .   .   .   .   NAME-runtime.convT2E64 a(true) x(0) class(PFUNC) tc(1) used FUNC-func(*byte, *int) interface {}
.   .   .   .   .   CALLFUNC-list
.   .   .   .   .   .   AS l(9) tc(1)
.   .   .   .   .   .   .   INDREGSP-SP a(true) l(9) x(0) tc(1) addrtaken main.__ PTR64-*byte
.   .   .   .   .   .   .   ADDR a(true) l(9) tc(1) PTR64-*uint8
.   .   .   .   .   .   .   .   NAME-type.int a(true) x(0) class(PEXTERN) tc(1) uint8

.   .   .   .   .   .   AS l(9) tc(1)
.   .   .   .   .   .   .   INDREGSP-SP a(true) l(9) x(8) tc(1) addrtaken main.__ PTR64-*int
.   .   .   .   .   .   .   ADDR l(9) tc(1) PTR64-*int
.   .   .   .   .   .   .   .   NAME-main..autotmp_1 a(true) l(9) x(0) class(PAUTO) esc(N) tc(1) addrtaken assigned used int

.   .   .   .   AS l(9) tc(1) hascall
.   .   .   .   .   INDEX l(9) tc(1) assigned bounded hascall INTER-interface {}
.   .   .   .   .   .   IND l(9) tc(1) implicit(true) assigned hascall ARRAY-[2]interface {}
.   .   .   .   .   .   .   NAME-main..autotmp_4 a(true) l(9) x(0) class(PAUTO) esc(N) tc(1) assigned used PTR64-*[2]interface {}
.   .   .   .   .   .   LITERAL-0 a(true) l(9) tc(1) int
.   .   .   .   .   NAME-main..autotmp_5 a(true) l(9) x(0) class(PAUTO) esc(N) tc(1) assigned used INTER-interface {}

.   .   .   .   VARKILL l(9) tc(1)
.   .   .   .   .   NAME-main..autotmp_5 a(true) l(9) x(0) class(PAUTO) esc(N) tc(1) assigned used INTER-interface {}

.   .   .   BLOCK l(9)
.   .   .   BLOCK-list
.   .   .   .   AS l(9) tc(1) hascall
.   .   .   .   .   INDEX l(9) tc(1) assigned bounded hascall INTER-interface {}
.   .   .   .   .   .   IND l(9) tc(1) implicit(true) assigned hascall ARRAY-[2]interface {}
.   .   .   .   .   .   .   NAME-main..autotmp_4 a(true) l(9) x(0) class(PAUTO) esc(N) tc(1) assigned used PTR64-*[2]interface {}
.   .   .   .   .   .   LITERAL-1 a(true) l(9) tc(1) int
.   .   .   .   .   EFACE l(9) tc(1) INTER-interface {}
.   .   .   .   .   .   ADDR a(true) l(9) tc(1) PTR64-*uint8
.   .   .   .   .   .   .   NAME-type.string a(true) x(0) class(PEXTERN) tc(1) uint8
.   .   .   .   .   .   ADDR l(9) tc(1) PTR64-*string
.   .   .   .   .   .   .   NAME-main.statictmp_0 a(true) l(9) x(0) class(PEXTERN) f(1) tc(1) addrtaken used string

.   .   .   BLOCK l(9)
.   .   .   BLOCK-list
.   .   .   .   AS l(9) tc(1) hascall
.   .   .   .   .   NAME-main..autotmp_3 a(true) l(9) x(0) class(PAUTO) esc(N) tc(1) assigned used SLICE-[]interface {}
.   .   .   .   .   SLICEARR l(9) tc(1) hascall SLICE-[]interface {}
.   .   .   .   .   .   NAME-main..autotmp_4 a(true) l(9) x(0) class(PAUTO) esc(N) tc(1) assigned used PTR64-*[2]interface {}
.   .   DEFER l(9) tc(1)
.   .   .   CALLFUNC l(9) tc(1) hascall STRUCT-(int, error)
.   .   .   .   NAME-fmt.Print a(true) l(4) x(0) class(PFUNC) tc(1) used FUNC-func(...interface {}) (int, error)
.   .   .   .   DDDARG l(9) esc(h) PTR64-*[2]interface {}
.   .   .   CALLFUNC-list
.   .   .   .   AS l(9) tc(1)
.   .   .   .   .   INDREGSP-SP a(true) l(9) x(16) tc(1) addrtaken main.__ SLICE-[]interface {}
.   .   .   .   .   NAME-main..autotmp_3 a(true) l(9) x(0) class(PAUTO) esc(N) tc(1) assigned used SLICE-[]interface {}

.   .   VARKILL l(9) tc(1)
.   .   .   NAME-main..autotmp_1 a(true) l(9) x(0) class(PAUTO) esc(N) tc(1) addrtaken assigned used int

before d2
.   DCL l(14)
.   .   NAME-main.i a(true) g(1) l(14) x(0) class(PAUTOHEAP) f(1) esc(h) tc(1) addrtaken assigned used int

.   AS l(14) colas(true) tc(1)
.   .   NAME-main.i a(true) g(1) l(14) x(0) class(PAUTOHEAP) f(1) esc(h) tc(1) addrtaken assigned used int
.   .   LITERAL-3 l(14) tc(1) int

.   FOR l(14) tc(1)
.   .   GT l(14) tc(1) bool
.   .   .   NAME-main.i a(true) g(1) l(14) x(0) class(PAUTOHEAP) f(1) esc(h) tc(1) addrtaken assigned used int
.   .   .   LITERAL-0 l(14) tc(1) int
.   .   BLOCK l(14)
.   .   BLOCK-list
.   .   .   AS l(14) tc(1)
.   .   .   .   NAME-main..autotmp_3 a(true) l(14) x(0) class(PAUTO) esc(N) tc(1) assigned used int
.   .   .   .   NAME-main.i a(true) g(1) l(14) x(0) class(PAUTOHEAP) f(1) esc(h) tc(1) addrtaken assigned used int

.   .   .   AS l(14) tc(1) implicit(true) int
.   .   .   .   NAME-main.i a(true) g(1) l(14) x(0) class(PAUTOHEAP) f(1) esc(h) tc(1) addrtaken assigned used int
.   .   .   .   SUB l(14) tc(1) int
.   .   .   .   .   NAME-main..autotmp_3 a(true) l(14) x(0) class(PAUTO) esc(N) tc(1) assigned used int
.   .   .   .   .   LITERAL-1 l(14) tc(1) int

.   .   .   VARKILL l(14) tc(1)
.   .   .   .   NAME-main..autotmp_3 a(true) l(14) x(0) class(PAUTO) esc(N) tc(1) assigned used int
.   FOR-body
.   .   DEFER l(15) tc(1)
.   .   .   CALLFUNC l(17) tc(1)
.   .   .   .   CLOSURE l(15) ff(1) esc(h) tc(1) main.d2.func1 FUNC-func()

.   CALLFUNC l(19) tc(1) STRUCT-(int, error)
.   .   NAME-fmt.Println a(true) l(4) x(0) class(PFUNC) tc(1) used FUNC-func(...interface {}) (int, error)
after walk d2
.   AS l(14) colas(true) tc(1) hascall
.   .   NAME-main.&i a(true) l(14) x(0) class(PAUTO) esc(N) tc(1) assigned nonnil used PTR64-*int
.   .   CALLFUNC l(14) tc(1) nonnil hascall PTR64-*int
.   .   .   NAME-runtime.newobject a(true) x(0) class(PFUNC) tc(1) used FUNC-func(*byte) *int
.   .   CALLFUNC-list
.   .   .   AS l(14) tc(1)
.   .   .   .   INDREGSP-SP a(true) l(14) x(0) tc(1) addrtaken main.__ PTR64-*byte
.   .   .   .   ADDR a(true) l(14) tc(1) PTR64-*uint8
.   .   .   .   .   NAME-type.int a(true) x(0) class(PEXTERN) tc(1) uint8

.   AS l(14) colas(true) tc(1) hascall
.   .   IND l(14) tc(1) hascall int
.   .   .   NAME-main.&i a(true) l(14) x(0) class(PAUTO) esc(N) tc(1) assigned nonnil used PTR64-*int
.   .   LITERAL-3 l(14) tc(1) int

.   FOR l(14) tc(1)
.   .   GT l(14) tc(1) hascall bool
.   .   .   IND l(14) tc(1) hascall int
.   .   .   .   NAME-main.&i a(true) l(14) x(0) class(PAUTO) esc(N) tc(1) assigned nonnil used PTR64-*int
.   .   .   LITERAL-0 l(14) tc(1) int
.   .   BLOCK l(14)
.   .   BLOCK-list
.   .   .   AS l(14) tc(1) hascall
.   .   .   .   NAME-main..autotmp_3 a(true) l(14) x(0) class(PAUTO) esc(N) tc(1) assigned used int
.   .   .   .   IND l(14) tc(1) hascall int
.   .   .   .   .   NAME-main.&i a(true) l(14) x(0) class(PAUTO) esc(N) tc(1) assigned nonnil used PTR64-*int

.   .   .   AS l(14) tc(1) implicit(true) hascall int
.   .   .   .   IND l(14) tc(1) hascall int
.   .   .   .   .   NAME-main.&i a(true) l(14) x(0) class(PAUTO) esc(N) tc(1) assigned nonnil used PTR64-*int
.   .   .   .   SUB l(14) tc(1) int
.   .   .   .   .   NAME-main..autotmp_3 a(true) l(14) x(0) class(PAUTO) esc(N) tc(1) assigned used int
.   .   .   .   .   LITERAL-1 l(14) tc(1) int

.   .   .   VARKILL l(14) tc(1)
.   .   .   .   NAME-main..autotmp_3 a(true) l(14) x(0) class(PAUTO) esc(N) tc(1) assigned used int
.   FOR-body
.   .   DEFER l(15) tc(1)
.   .   .   CALLFUNC l(17) tc(1) hascall STRUCT-()
.   .   .   .   NAME-main.d2.func1 a(true) l(15) x(0) class(PFUNC) f(1) tc(1) FUNC-func(*int)
.   .   .   CALLFUNC-list
.   .   .   .   AS l(17) tc(1) hascall
.   .   .   .   .   INDREGSP-SP a(true) l(17) x(16) tc(1) addrtaken main.__ PTR64-*int
.   .   .   .   .   ADDR l(15) tc(1) hascall PTR64-*int
.   .   .   .   .   .   IND l(15) tc(1) hascall int
.   .   .   .   .   .   .   NAME-main.&i a(true) l(14) x(0) class(PAUTO) esc(N) tc(1) assigned nonnil used PTR64-*int

.   CALLFUNC l(19) tc(1) hascall STRUCT-(int, error)
.   .   NAME-fmt.Println a(true) l(4) x(0) class(PFUNC) tc(1) used FUNC-func(...interface {}) (int, error)
.   CALLFUNC-list
.   .   AS l(19) tc(1)
.   .   .   INDREGSP-SP a(true) l(19) x(0) tc(1) addrtaken main.__ SLICE-[]interface {}
.   .   .   LITERAL-nil a(true) l(19) SLICE-[]interface {}

before d3
.   DCL l(23)
.   .   NAME-main.i a(true) g(1) l(23) x(0) class(PAUTO) f(1) tc(1) assigned used int

.   AS l(23) colas(true) tc(1)
.   .   NAME-main.i a(true) g(1) l(23) x(0) class(PAUTO) f(1) tc(1) assigned used int
.   .   LITERAL-3 l(23) tc(1) int

.   FOR l(23) tc(1)
.   .   GT l(23) tc(1) bool
.   .   .   NAME-main.i a(true) g(1) l(23) x(0) class(PAUTO) f(1) tc(1) assigned used int
.   .   .   LITERAL-0 l(23) tc(1) int
.   .   BLOCK l(23)
.   .   BLOCK-list
.   .   .   AS l(23) tc(1)
.   .   .   .   NAME-main..autotmp_2 a(true) l(23) x(0) class(PAUTO) esc(N) tc(1) assigned used int
.   .   .   .   NAME-main.i a(true) g(1) l(23) x(0) class(PAUTO) f(1) tc(1) assigned used int

.   .   .   AS l(23) tc(1) implicit(true) int
.   .   .   .   NAME-main.i a(true) g(1) l(23) x(0) class(PAUTO) f(1) tc(1) assigned used int
.   .   .   .   SUB l(23) tc(1) int
.   .   .   .   .   NAME-main..autotmp_2 a(true) l(23) x(0) class(PAUTO) esc(N) tc(1) assigned used int
.   .   .   .   .   LITERAL-1 l(23) tc(1) int

.   .   .   VARKILL l(23) tc(1)
.   .   .   .   NAME-main..autotmp_2 a(true) l(23) x(0) class(PAUTO) esc(N) tc(1) assigned used int
.   FOR-body
.   .   DEFER l(24) tc(1)
.   .   .   CALLFUNC l(26) tc(1)
.   .   .   .   CLOSURE l(24) ff(1) esc(h) tc(1) main.d3.func1 FUNC-func(int)
.   .   .   CALLFUNC-list
.   .   .   .   NAME-main.i a(true) g(1) l(23) x(0) class(PAUTO) f(1) tc(1) assigned used int
after walk d3
.   DCL l(23)
.   .   NAME-main.i a(true) g(1) l(23) x(0) class(PAUTO) f(1) tc(1) assigned used int

.   AS l(23) colas(true) tc(1)
.   .   NAME-main.i a(true) g(1) l(23) x(0) class(PAUTO) f(1) tc(1) assigned used int
.   .   LITERAL-3 l(23) tc(1) int

.   FOR l(23) tc(1)
.   .   GT l(23) tc(1) bool
.   .   .   NAME-main.i a(true) g(1) l(23) x(0) class(PAUTO) f(1) tc(1) assigned used int
.   .   .   LITERAL-0 l(23) tc(1) int
.   .   BLOCK l(23)
.   .   BLOCK-list
.   .   .   AS l(23) tc(1)
.   .   .   .   NAME-main..autotmp_2 a(true) l(23) x(0) class(PAUTO) esc(N) tc(1) assigned used int
.   .   .   .   NAME-main.i a(true) g(1) l(23) x(0) class(PAUTO) f(1) tc(1) assigned used int

.   .   .   AS l(23) tc(1) implicit(true) int
.   .   .   .   NAME-main.i a(true) g(1) l(23) x(0) class(PAUTO) f(1) tc(1) assigned used int
.   .   .   .   SUB l(23) tc(1) int
.   .   .   .   .   NAME-main..autotmp_2 a(true) l(23) x(0) class(PAUTO) esc(N) tc(1) assigned used int
.   .   .   .   .   LITERAL-1 l(23) tc(1) int

.   .   .   VARKILL l(23) tc(1)
.   .   .   .   NAME-main..autotmp_2 a(true) l(23) x(0) class(PAUTO) esc(N) tc(1) assigned used int
.   FOR-body
.   .   DEFER l(24) tc(1)
.   .   .   CALLFUNC l(26) tc(1) hascall STRUCT-()
.   .   .   .   NAME-main.d3.func1 a(true) l(24) x(0) class(PFUNC) f(1) tc(1) FUNC-func(int)
.   .   .   CALLFUNC-list
.   .   .   .   AS l(26) tc(1)
.   .   .   .   .   INDREGSP-SP a(true) l(26) x(16) tc(1) addrtaken main.__ int
.   .   .   .   .   NAME-main.i a(true) g(1) l(23) x(0) class(PAUTO) f(1) tc(1) assigned used int

before main
.   CALLFUNC l(31) tc(1)
.   .   NAME-main.d1 a(true) l(7) x(0) class(PFUNC) tc(1) used FUNC-func()

.   CALLFUNC l(32) tc(1)
.   .   NAME-main.d2 a(true) l(13) x(0) class(PFUNC) tc(1) used FUNC-func()

.   CALLFUNC l(33) tc(1) STRUCT-(int, error)
.   .   NAME-fmt.Println a(true) l(4) x(0) class(PFUNC) tc(1) used FUNC-func(...interface {}) (int, error)

.   CALLFUNC l(34) tc(1)
.   .   NAME-main.d3 a(true) l(22) x(0) class(PFUNC) tc(1) used FUNC-func()

.   CALLFUNC l(35) tc(1) STRUCT-(int, error)
.   .   NAME-fmt.Println a(true) l(4) x(0) class(PFUNC) tc(1) used FUNC-func(...interface {}) (int, error)
after walk main
.   CALLFUNC l(31) tc(1) hascall
.   .   NAME-main.d1 a(true) l(7) x(0) class(PFUNC) tc(1) used FUNC-func()

.   CALLFUNC l(32) tc(1) hascall
.   .   NAME-main.d2 a(true) l(13) x(0) class(PFUNC) tc(1) used FUNC-func()

.   CALLFUNC l(33) tc(1) hascall STRUCT-(int, error)
.   .   NAME-fmt.Println a(true) l(4) x(0) class(PFUNC) tc(1) used FUNC-func(...interface {}) (int, error)
.   CALLFUNC-list
.   .   AS l(33) tc(1)
.   .   .   INDREGSP-SP a(true) l(33) x(0) tc(1) addrtaken main.__ SLICE-[]interface {}
.   .   .   LITERAL-nil a(true) l(33) SLICE-[]interface {}

.   CALLFUNC l(34) tc(1) hascall
.   .   NAME-main.d3 a(true) l(22) x(0) class(PFUNC) tc(1) used FUNC-func()

.   CALLFUNC l(35) tc(1) hascall STRUCT-(int, error)
.   .   NAME-fmt.Println a(true) l(4) x(0) class(PFUNC) tc(1) used FUNC-func(...interface {}) (int, error)
.   CALLFUNC-list
.   .   AS l(35) tc(1)
.   .   .   INDREGSP-SP a(true) l(35) x(0) tc(1) addrtaken main.__ SLICE-[]interface {}
.   .   .   LITERAL-nil a(true) l(35) SLICE-[]interface {}

before d2.func1
.   AS l(16) tc(1)
.   .   NAME-main..autotmp_2 a(true) l(16) x(0) class(PAUTO) esc(N) tc(1) assigned used int
.   .   NAME-main.i l(16) x(0) class(PAUTOHEAP) f(2) tc(1) used int

.   CALLFUNC l(16) tc(1) STRUCT-(int, error)
.   .   NAME-fmt.Print a(true) l(4) x(0) class(PFUNC) tc(1) used FUNC-func(...interface {}) (int, error)
.   .   DDDARG l(16) esc(no) PTR64-*[2]interface {}
.   CALLFUNC-list
.   .   CONVIFACE l(16) esc(h) tc(1) implicit(true) INTER-interface {}
.   .   .   NAME-main..autotmp_2 a(true) l(16) x(0) class(PAUTO) esc(N) tc(1) assigned used int

.   .   CONVIFACE l(16) esc(h) tc(1) implicit(true) INTER-interface {}
.   .   .   NAME-main.statictmp_1 a(true) l(16) x(0) class(PEXTERN) f(2) tc(1) used string

.   VARKILL l(16) tc(1)
.   .   NAME-main..autotmp_2 a(true) l(16) x(0) class(PAUTO) esc(N) tc(1) assigned used int

.   VARKILL l(16) tc(1)
.   .   NAME-main..autotmp_1 a(true) l(16) x(0) class(PAUTO) esc(N) used ARRAY-[2]interface {}
after walk d2.func1
.   AS l(16) tc(1) hascall
.   .   NAME-main..autotmp_2 a(true) l(16) x(0) class(PAUTO) esc(N) tc(1) addrtaken assigned used int
.   .   IND l(16) tc(1) hascall int
.   .   .   NAME-main.&i a(true) l(15) x(0) class(PPARAM) tc(1) nonnil used PTR64-*int

.   CALLFUNC-init
.   .   AS l(16) tc(1)
.   .   .   NAME-main..autotmp_1 a(true) l(16) x(0) class(PAUTO) esc(N) tc(1) addrtaken assigned used ARRAY-[2]interface {}

.   .   AS l(16) tc(1)
.   .   .   NAME-main..autotmp_4 a(true) l(16) x(0) class(PAUTO) esc(N) tc(1) assigned used PTR64-*[2]interface {}
.   .   .   ADDR l(16) tc(1) PTR64-*[2]interface {}
.   .   .   .   NAME-main..autotmp_1 a(true) l(16) x(0) class(PAUTO) esc(N) tc(1) addrtaken assigned used ARRAY-[2]interface {}

.   .   BLOCK l(16)
.   .   BLOCK-list
.   .   .   AS l(16) tc(1) hascall
.   .   .   .   NAME-main..autotmp_5 a(true) l(16) x(0) class(PAUTO) esc(N) tc(1) assigned used INTER-interface {}
.   .   .   .   CALLFUNC l(16) tc(1) hascall INTER-interface {}
.   .   .   .   .   NAME-runtime.convT2E64 a(true) x(0) class(PFUNC) tc(1) used FUNC-func(*byte, *int) interface {}
.   .   .   .   CALLFUNC-list
.   .   .   .   .   AS l(16) tc(1)
.   .   .   .   .   .   INDREGSP-SP a(true) l(16) x(0) tc(1) addrtaken main.__ PTR64-*byte
.   .   .   .   .   .   ADDR a(true) l(16) tc(1) PTR64-*uint8
.   .   .   .   .   .   .   NAME-type.int a(true) x(0) class(PEXTERN) tc(1) uint8

.   .   .   .   .   AS l(16) tc(1)
.   .   .   .   .   .   INDREGSP-SP a(true) l(16) x(8) tc(1) addrtaken main.__ PTR64-*int
.   .   .   .   .   .   ADDR l(16) tc(1) PTR64-*int
.   .   .   .   .   .   .   NAME-main..autotmp_2 a(true) l(16) x(0) class(PAUTO) esc(N) tc(1) addrtaken assigned used int

.   .   .   AS l(16) tc(1) hascall
.   .   .   .   INDEX l(16) tc(1) assigned bounded hascall INTER-interface {}
.   .   .   .   .   IND l(16) tc(1) implicit(true) assigned hascall ARRAY-[2]interface {}
.   .   .   .   .   .   NAME-main..autotmp_4 a(true) l(16) x(0) class(PAUTO) esc(N) tc(1) assigned used PTR64-*[2]interface {}
.   .   .   .   .   LITERAL-0 a(true) l(16) tc(1) int
.   .   .   .   NAME-main..autotmp_5 a(true) l(16) x(0) class(PAUTO) esc(N) tc(1) assigned used INTER-interface {}

.   .   .   VARKILL l(16) tc(1)
.   .   .   .   NAME-main..autotmp_5 a(true) l(16) x(0) class(PAUTO) esc(N) tc(1) assigned used INTER-interface {}

.   .   BLOCK l(16)
.   .   BLOCK-list
.   .   .   AS l(16) tc(1) hascall
.   .   .   .   INDEX l(16) tc(1) assigned bounded hascall INTER-interface {}
.   .   .   .   .   IND l(16) tc(1) implicit(true) assigned hascall ARRAY-[2]interface {}
.   .   .   .   .   .   NAME-main..autotmp_4 a(true) l(16) x(0) class(PAUTO) esc(N) tc(1) assigned used PTR64-*[2]interface {}
.   .   .   .   .   LITERAL-1 a(true) l(16) tc(1) int
.   .   .   .   EFACE l(16) tc(1) INTER-interface {}
.   .   .   .   .   ADDR a(true) l(16) tc(1) PTR64-*uint8
.   .   .   .   .   .   NAME-type.string a(true) x(0) class(PEXTERN) tc(1) uint8
.   .   .   .   .   ADDR l(16) tc(1) PTR64-*string
.   .   .   .   .   .   NAME-main.statictmp_1 a(true) l(16) x(0) class(PEXTERN) f(2) tc(1) addrtaken used string

.   .   BLOCK l(16)
.   .   BLOCK-list
.   .   .   AS l(16) tc(1) hascall
.   .   .   .   NAME-main..autotmp_3 a(true) l(16) x(0) class(PAUTO) esc(N) tc(1) assigned used SLICE-[]interface {}
.   .   .   .   SLICEARR l(16) tc(1) hascall SLICE-[]interface {}
.   .   .   .   .   NAME-main..autotmp_4 a(true) l(16) x(0) class(PAUTO) esc(N) tc(1) assigned used PTR64-*[2]interface {}
.   CALLFUNC l(16) tc(1) hascall STRUCT-(int, error)
.   .   NAME-fmt.Print a(true) l(4) x(0) class(PFUNC) tc(1) used FUNC-func(...interface {}) (int, error)
.   .   DDDARG l(16) esc(no) PTR64-*[2]interface {}
.   CALLFUNC-list
.   .   AS l(16) tc(1)
.   .   .   INDREGSP-SP a(true) l(16) x(0) tc(1) addrtaken main.__ SLICE-[]interface {}
.   .   .   NAME-main..autotmp_3 a(true) l(16) x(0) class(PAUTO) esc(N) tc(1) assigned used SLICE-[]interface {}

.   VARKILL l(16) tc(1)
.   .   NAME-main..autotmp_2 a(true) l(16) x(0) class(PAUTO) esc(N) tc(1) addrtaken assigned used int

.   VARKILL l(16) tc(1)
.   .   NAME-main..autotmp_1 a(true) l(16) x(0) class(PAUTO) esc(N) tc(1) addrtaken assigned used ARRAY-[2]interface {}

before d3.func1
.   AS l(25) tc(1)
.   .   NAME-main..autotmp_2 a(true) l(25) x(0) class(PAUTO) esc(N) tc(1) assigned used int
.   .   NAME-main.n a(true) g(1) l(24) x(0) class(PPARAM) f(2) tc(1) used int

.   CALLFUNC l(25) tc(1) STRUCT-(int, error)
.   .   NAME-fmt.Println a(true) l(4) x(0) class(PFUNC) tc(1) used FUNC-func(...interface {}) (int, error)
.   .   DDDARG l(25) esc(no) PTR64-*[2]interface {}
.   CALLFUNC-list
.   .   CONVIFACE l(25) esc(h) tc(1) implicit(true) INTER-interface {}
.   .   .   NAME-main..autotmp_2 a(true) l(25) x(0) class(PAUTO) esc(N) tc(1) assigned used int

.   .   CONVIFACE l(25) esc(h) tc(1) implicit(true) INTER-interface {}
.   .   .   NAME-main.statictmp_2 a(true) l(25) x(0) class(PEXTERN) f(2) tc(1) used string

.   VARKILL l(25) tc(1)
.   .   NAME-main..autotmp_2 a(true) l(25) x(0) class(PAUTO) esc(N) tc(1) assigned used int

.   VARKILL l(25) tc(1)
.   .   NAME-main..autotmp_1 a(true) l(25) x(0) class(PAUTO) esc(N) used ARRAY-[2]interface {}
after walk d3.func1
.   AS l(25) tc(1)
.   .   NAME-main..autotmp_2 a(true) l(25) x(0) class(PAUTO) esc(N) tc(1) addrtaken assigned used int
.   .   NAME-main.n a(true) g(1) l(24) x(0) class(PPARAM) f(2) tc(1) used int

.   CALLFUNC-init
.   .   AS l(25) tc(1)
.   .   .   NAME-main..autotmp_1 a(true) l(25) x(0) class(PAUTO) esc(N) tc(1) addrtaken assigned used ARRAY-[2]interface {}

.   .   AS l(25) tc(1)
.   .   .   NAME-main..autotmp_4 a(true) l(25) x(0) class(PAUTO) esc(N) tc(1) assigned used PTR64-*[2]interface {}
.   .   .   ADDR l(25) tc(1) PTR64-*[2]interface {}
.   .   .   .   NAME-main..autotmp_1 a(true) l(25) x(0) class(PAUTO) esc(N) tc(1) addrtaken assigned used ARRAY-[2]interface {}

.   .   BLOCK l(25)
.   .   BLOCK-list
.   .   .   AS l(25) tc(1) hascall
.   .   .   .   NAME-main..autotmp_5 a(true) l(25) x(0) class(PAUTO) esc(N) tc(1) assigned used INTER-interface {}
.   .   .   .   CALLFUNC l(25) tc(1) hascall INTER-interface {}
.   .   .   .   .   NAME-runtime.convT2E64 a(true) x(0) class(PFUNC) tc(1) used FUNC-func(*byte, *int) interface {}
.   .   .   .   CALLFUNC-list
.   .   .   .   .   AS l(25) tc(1)
.   .   .   .   .   .   INDREGSP-SP a(true) l(25) x(0) tc(1) addrtaken main.__ PTR64-*byte
.   .   .   .   .   .   ADDR a(true) l(25) tc(1) PTR64-*uint8
.   .   .   .   .   .   .   NAME-type.int a(true) x(0) class(PEXTERN) tc(1) uint8

.   .   .   .   .   AS l(25) tc(1)
.   .   .   .   .   .   INDREGSP-SP a(true) l(25) x(8) tc(1) addrtaken main.__ PTR64-*int
.   .   .   .   .   .   ADDR l(25) tc(1) PTR64-*int
.   .   .   .   .   .   .   NAME-main..autotmp_2 a(true) l(25) x(0) class(PAUTO) esc(N) tc(1) addrtaken assigned used int

.   .   .   AS l(25) tc(1) hascall
.   .   .   .   INDEX l(25) tc(1) assigned bounded hascall INTER-interface {}
.   .   .   .   .   IND l(25) tc(1) implicit(true) assigned hascall ARRAY-[2]interface {}
.   .   .   .   .   .   NAME-main..autotmp_4 a(true) l(25) x(0) class(PAUTO) esc(N) tc(1) assigned used PTR64-*[2]interface {}
.   .   .   .   .   LITERAL-0 a(true) l(25) tc(1) int
.   .   .   .   NAME-main..autotmp_5 a(true) l(25) x(0) class(PAUTO) esc(N) tc(1) assigned used INTER-interface {}

.   .   .   VARKILL l(25) tc(1)
.   .   .   .   NAME-main..autotmp_5 a(true) l(25) x(0) class(PAUTO) esc(N) tc(1) assigned used INTER-interface {}

.   .   BLOCK l(25)
.   .   BLOCK-list
.   .   .   AS l(25) tc(1) hascall
.   .   .   .   INDEX l(25) tc(1) assigned bounded hascall INTER-interface {}
.   .   .   .   .   IND l(25) tc(1) implicit(true) assigned hascall ARRAY-[2]interface {}
.   .   .   .   .   .   NAME-main..autotmp_4 a(true) l(25) x(0) class(PAUTO) esc(N) tc(1) assigned used PTR64-*[2]interface {}
.   .   .   .   .   LITERAL-1 a(true) l(25) tc(1) int
.   .   .   .   EFACE l(25) tc(1) INTER-interface {}
.   .   .   .   .   ADDR a(true) l(25) tc(1) PTR64-*uint8
.   .   .   .   .   .   NAME-type.string a(true) x(0) class(PEXTERN) tc(1) uint8
.   .   .   .   .   ADDR l(25) tc(1) PTR64-*string
.   .   .   .   .   .   NAME-main.statictmp_2 a(true) l(25) x(0) class(PEXTERN) f(2) tc(1) addrtaken used string

.   .   BLOCK l(25)
.   .   BLOCK-list
.   .   .   AS l(25) tc(1) hascall
.   .   .   .   NAME-main..autotmp_3 a(true) l(25) x(0) class(PAUTO) esc(N) tc(1) assigned used SLICE-[]interface {}
.   .   .   .   SLICEARR l(25) tc(1) hascall SLICE-[]interface {}
.   .   .   .   .   NAME-main..autotmp_4 a(true) l(25) x(0) class(PAUTO) esc(N) tc(1) assigned used PTR64-*[2]interface {}
.   CALLFUNC l(25) tc(1) hascall STRUCT-(int, error)
.   .   NAME-fmt.Println a(true) l(4) x(0) class(PFUNC) tc(1) used FUNC-func(...interface {}) (int, error)
.   .   DDDARG l(25) esc(no) PTR64-*[2]interface {}
.   CALLFUNC-list
.   .   AS l(25) tc(1)
.   .   .   INDREGSP-SP a(true) l(25) x(0) tc(1) addrtaken main.__ SLICE-[]interface {}
.   .   .   NAME-main..autotmp_3 a(true) l(25) x(0) class(PAUTO) esc(N) tc(1) assigned used SLICE-[]interface {}

.   VARKILL l(25) tc(1)
.   .   NAME-main..autotmp_2 a(true) l(25) x(0) class(PAUTO) esc(N) tc(1) addrtaken assigned used int

.   VARKILL l(25) tc(1)
.   .   NAME-main..autotmp_1 a(true) l(25) x(0) class(PAUTO) esc(N) tc(1) addrtaken assigned used ARRAY-[2]interface {}

before init
.   IF l(1) tc(1)
.   .   GT l(1) tc(1) bool
.   .   .   NAME-main.initdone· a(true) l(1) x(0) class(PEXTERN) tc(1) assigned used uint8
.   .   .   LITERAL-1 a(true) l(1) tc(1) uint8
.   IF-body
.   .   RETURN l(1) tc(1)

.   IF l(1) tc(1)
.   .   EQ l(1) tc(1) bool
.   .   .   NAME-main.initdone· a(true) l(1) x(0) class(PEXTERN) tc(1) assigned used uint8
.   .   .   LITERAL-1 a(true) l(1) tc(1) uint8
.   IF-body
.   .   CALLFUNC l(1) tc(1)
.   .   .   NAME-runtime.throwinit a(true) x(0) class(PFUNC) tc(1) used FUNC-func()

.   AS l(1) tc(1)
.   .   NAME-main.initdone· a(true) l(1) x(0) class(PEXTERN) tc(1) assigned used uint8
.   .   LITERAL-1 a(true) l(1) tc(1) uint8

.   CALLFUNC l(1) tc(1)
.   .   NAME-fmt.init a(true) l(4) x(0) class(PFUNC) tc(1) used FUNC-func()

.   AS l(1) tc(1)
.   .   NAME-main.initdone· a(true) l(1) x(0) class(PEXTERN) tc(1) assigned used uint8
.   .   LITERAL-2 a(true) l(1) tc(1) uint8

.   RETURN l(1) tc(1)
after walk init
.   IF l(1) tc(1)
.   .   GT l(1) tc(1) bool
.   .   .   NAME-main.initdone· a(true) l(1) x(0) class(PEXTERN) tc(1) assigned used uint8
.   .   .   LITERAL-1 a(true) l(1) tc(1) uint8
.   IF-body
.   .   RETURN l(1) tc(1)

.   IF l(1) tc(1)
.   .   EQ l(1) tc(1) bool
.   .   .   NAME-main.initdone· a(true) l(1) x(0) class(PEXTERN) tc(1) assigned used uint8
.   .   .   LITERAL-1 a(true) l(1) tc(1) uint8
.   IF-body
.   .   CALLFUNC l(1) tc(1) hascall
.   .   .   NAME-runtime.throwinit a(true) x(0) class(PFUNC) tc(1) used FUNC-func()

.   AS l(1) tc(1)
.   .   NAME-main.initdone· a(true) l(1) x(0) class(PEXTERN) tc(1) assigned used uint8
.   .   LITERAL-1 a(true) l(1) tc(1) uint8

.   CALLFUNC l(1) tc(1) hascall
.   .   NAME-fmt.init a(true) l(4) x(0) class(PFUNC) tc(1) used FUNC-func()

.   AS l(1) tc(1)
.   .   NAME-main.initdone· a(true) l(1) x(0) class(PEXTERN) tc(1) assigned used uint8
.   .   LITERAL-2 a(true) l(1) tc(1) uint8

.   RETURN l(1) tc(1)

before type..hash.[2]interface {}
.   DCL l(1)
.   .   NAME-main.i a(true) g(4) l(1) x(0) class(PAUTO) f(1) tc(1) assigned used int

.   RANGE l(1) colas(true) tc(1) ARRAY-[2]interface {}
.   .   IND l(1) tc(1) ARRAY-[2]interface {}
.   .   .   NAME-main.p a(true) g(2) l(1) x(0) class(PPARAM) f(1) tc(1) used PTR64-*[2]interface {}
.   RANGE-list
.   .   NAME-main.i a(true) g(4) l(1) x(0) class(PAUTO) f(1) tc(1) assigned used int
.   RANGE-body
.   .   AS l(1) tc(1)
.   .   .   NAME-main.h a(true) g(3) l(1) x(8) class(PPARAM) f(1) tc(1) assigned used uintptr
.   .   .   CALLFUNC l(1) tc(1) uintptr
.   .   .   .   NAME-runtime.nilinterhash a(true) l(1) x(0) class(PFUNC) tc(1) used FUNC-func(*interface {}, uintptr) uintptr
.   .   .   CALLFUNC-list
.   .   .   .   ADDR l(1) tc(1) PTR64-*interface {}
.   .   .   .   .   INDEX l(1) tc(1) addrtaken bounded INTER-interface {}
.   .   .   .   .   .   IND l(1) tc(1) implicit(true) addrtaken ARRAY-[2]interface {}
.   .   .   .   .   .   .   NAME-main.p a(true) g(2) l(1) x(0) class(PPARAM) f(1) tc(1) used PTR64-*[2]interface {}
.   .   .   .   .   .   NAME-main.i a(true) g(4) l(1) x(0) class(PAUTO) f(1) tc(1) assigned used int

.   .   .   .   NAME-main.h a(true) g(3) l(1) x(8) class(PPARAM) f(1) tc(1) assigned used uintptr

.   RETURN l(1) tc(1)
.   RETURN-list
.   .   NAME-main.h a(true) g(3) l(1) x(8) class(PPARAM) f(1) tc(1) assigned used uintptr
after walk type..hash.[2]interface {}
.   DCL l(1)
.   .   NAME-main.i a(true) g(4) l(1) x(0) class(PAUTO) f(1) tc(1) assigned used int

.   FOR-init
.   .   AS l(1) tc(1)
.   .   .   NAME-main..autotmp_4 a(true) l(1) x(0) class(PAUTO) esc(N) tc(1) assigned used int

.   .   AS l(1) tc(1)
.   .   .   NAME-main..autotmp_5 a(true) l(1) x(0) class(PAUTO) esc(N) tc(1) assigned used int
.   .   .   LITERAL-2 a(true) x(0) tc(1) int
.   FOR l(1) colas(true) tc(1) ARRAY-[2]interface {}
.   .   LT l(1) tc(1) bool
.   .   .   NAME-main..autotmp_4 a(true) l(1) x(0) class(PAUTO) esc(N) tc(1) assigned used int
.   .   .   NAME-main..autotmp_5 a(true) l(1) x(0) class(PAUTO) esc(N) tc(1) assigned used int
.   .   AS l(1) tc(1)
.   .   .   NAME-main..autotmp_4 a(true) l(1) x(0) class(PAUTO) esc(N) tc(1) assigned used int
.   .   .   ADD l(1) tc(1) int
.   .   .   .   NAME-main..autotmp_4 a(true) l(1) x(0) class(PAUTO) esc(N) tc(1) assigned used int
.   .   .   .   LITERAL-1 a(true) l(1) tc(1) int
.   FOR-body
.   .   AS l(1) tc(1)
.   .   .   NAME-main.i a(true) g(4) l(1) x(0) class(PAUTO) f(1) tc(1) assigned used int
.   .   .   NAME-main..autotmp_4 a(true) l(1) x(0) class(PAUTO) esc(N) tc(1) assigned used int

.   .   AS l(1) tc(1) hascall
.   .   .   NAME-main.h a(true) g(3) l(1) x(8) class(PPARAM) f(1) tc(1) assigned used uintptr
.   .   .   CALLFUNC l(1) tc(1) hascall uintptr
.   .   .   .   NAME-runtime.nilinterhash a(true) l(1) x(0) class(PFUNC) tc(1) used FUNC-func(*interface {}, uintptr) uintptr
.   .   .   CALLFUNC-list
.   .   .   .   AS l(1) tc(1) hascall
.   .   .   .   .   INDREGSP-SP a(true) l(1) x(0) tc(1) addrtaken main.__ PTR64-*interface {}
.   .   .   .   .   ADDR l(1) tc(1) hascall PTR64-*interface {}
.   .   .   .   .   .   INDEX l(1) tc(1) addrtaken bounded hascall INTER-interface {}
.   .   .   .   .   .   .   IND l(1) tc(1) implicit(true) addrtaken hascall ARRAY-[2]interface {}
.   .   .   .   .   .   .   .   NAME-main.p a(true) g(2) l(1) x(0) class(PPARAM) f(1) tc(1) used PTR64-*[2]interface {}
.   .   .   .   .   .   .   NAME-main.i a(true) g(4) l(1) x(0) class(PAUTO) f(1) tc(1) assigned used int

.   .   .   .   AS l(1) tc(1)
.   .   .   .   .   INDREGSP-SP a(true) l(1) x(8) tc(1) addrtaken main.__ uintptr
.   .   .   .   .   NAME-main.h a(true) g(3) l(1) x(8) class(PPARAM) f(1) tc(1) assigned used uintptr

.   RETURN l(1) tc(1)
.   RETURN-list
.   .   AS l(1) tc(1)
.   .   .   NAME-main.~r2 a(true) g(1) l(1) x(16) class(PPARAMOUT) f(1) uintptr
.   .   .   NAME-main.h a(true) g(3) l(1) x(8) class(PPARAM) f(1) tc(1) assigned used uintptr
enter type..hash.[2]interface {}
.   AS l(1)
.   .   NAME-main.~r2 a(true) g(1) l(1) x(16) class(PPARAMOUT) f(1) uintptr

before type..eq.[2]interface {}
.   DCL l(1)
.   .   NAME-main.i a(true) g(4) l(1) x(0) class(PAUTO) f(1) tc(1) assigned used int

.   RANGE l(1) colas(true) tc(1) ARRAY-[2]interface {}
.   .   IND l(1) tc(1) ARRAY-[2]interface {}
.   .   .   NAME-main.p a(true) g(2) l(1) x(0) class(PPARAM) f(1) tc(1) used PTR64-*[2]interface {}
.   RANGE-list
.   .   NAME-main.i a(true) g(4) l(1) x(0) class(PAUTO) f(1) tc(1) assigned used int
.   RANGE-body
.   .   IF l(1) tc(1)
.   .   .   CMPIFACE l(1) tc(1) bool
.   .   .   .   INDEX l(1) tc(1) bounded INTER-interface {}
.   .   .   .   .   IND l(1) tc(1) implicit(true) ARRAY-[2]interface {}
.   .   .   .   .   .   NAME-main.p a(true) g(2) l(1) x(0) class(PPARAM) f(1) tc(1) used PTR64-*[2]interface {}
.   .   .   .   .   NAME-main.i a(true) g(4) l(1) x(0) class(PAUTO) f(1) tc(1) assigned used int
.   .   .   .   INDEX l(1) tc(1) bounded INTER-interface {}
.   .   .   .   .   IND l(1) tc(1) implicit(true) ARRAY-[2]interface {}
.   .   .   .   .   .   NAME-main.q a(true) g(3) l(1) x(8) class(PPARAM) f(1) tc(1) used PTR64-*[2]interface {}
.   .   .   .   .   NAME-main.i a(true) g(4) l(1) x(0) class(PAUTO) f(1) tc(1) assigned used int
.   .   IF-body
.   .   .   RETURN l(1) tc(1)
.   .   .   RETURN-list
.   .   .   .   LITERAL-false a(true) l(1) tc(1) bool

.   RETURN l(1) tc(1)
.   RETURN-list
.   .   LITERAL-true a(true) l(1) tc(1) bool
after walk type..eq.[2]interface {}
.   DCL l(1)
.   .   NAME-main.i a(true) g(4) l(1) x(0) class(PAUTO) f(1) tc(1) assigned used int

.   FOR-init
.   .   AS l(1) tc(1)
.   .   .   NAME-main..autotmp_4 a(true) l(1) x(0) class(PAUTO) esc(N) tc(1) assigned used int

.   .   AS l(1) tc(1)
.   .   .   NAME-main..autotmp_5 a(true) l(1) x(0) class(PAUTO) esc(N) tc(1) assigned used int
.   .   .   LITERAL-2 a(true) x(0) tc(1) int
.   FOR l(1) colas(true) tc(1) ARRAY-[2]interface {}
.   .   LT l(1) tc(1) bool
.   .   .   NAME-main..autotmp_4 a(true) l(1) x(0) class(PAUTO) esc(N) tc(1) assigned used int
.   .   .   NAME-main..autotmp_5 a(true) l(1) x(0) class(PAUTO) esc(N) tc(1) assigned used int
.   .   AS l(1) tc(1)
.   .   .   NAME-main..autotmp_4 a(true) l(1) x(0) class(PAUTO) esc(N) tc(1) assigned used int
.   .   .   ADD l(1) tc(1) int
.   .   .   .   NAME-main..autotmp_4 a(true) l(1) x(0) class(PAUTO) esc(N) tc(1) assigned used int
.   .   .   .   LITERAL-1 a(true) l(1) tc(1) int
.   FOR-body
.   .   AS l(1) tc(1)
.   .   .   NAME-main.i a(true) g(4) l(1) x(0) class(PAUTO) f(1) tc(1) assigned used int
.   .   .   NAME-main..autotmp_4 a(true) l(1) x(0) class(PAUTO) esc(N) tc(1) assigned used int

.   .   IF-init
.   .   .   AS l(1) tc(1) hascall
.   .   .   .   NAME-main..autotmp_6 a(true) l(1) x(0) class(PAUTO) esc(N) tc(1) assigned used INTER-interface {}
.   .   .   .   INDEX l(1) tc(1) bounded hascall INTER-interface {}
.   .   .   .   .   IND l(1) tc(1) implicit(true) hascall ARRAY-[2]interface {}
.   .   .   .   .   .   NAME-main.q a(true) g(3) l(1) x(8) class(PPARAM) f(1) tc(1) used PTR64-*[2]interface {}
.   .   .   .   .   NAME-main.i a(true) g(4) l(1) x(0) class(PAUTO) f(1) tc(1) assigned used int

.   .   .   AS l(1) tc(1) hascall
.   .   .   .   NAME-main..autotmp_7 a(true) l(1) x(0) class(PAUTO) esc(N) tc(1) assigned used INTER-interface {}
.   .   .   .   INDEX l(1) tc(1) bounded hascall INTER-interface {}
.   .   .   .   .   IND l(1) tc(1) implicit(true) hascall ARRAY-[2]interface {}
.   .   .   .   .   .   NAME-main.p a(true) g(2) l(1) x(0) class(PPARAM) f(1) tc(1) used PTR64-*[2]interface {}
.   .   .   .   .   NAME-main.i a(true) g(4) l(1) x(0) class(PAUTO) f(1) tc(1) assigned used int
.   .   IF l(1) tc(1)
.   .   .   OROR l(1) tc(1) hascall bool
.   .   .   .   NE l(1) tc(1) bool
.   .   .   .   .   ITAB l(1) tc(1) PTR64-*uintptr
.   .   .   .   .   .   NAME-main..autotmp_7 a(true) l(1) x(0) class(PAUTO) esc(N) tc(1) assigned used INTER-interface {}
.   .   .   .   .   ITAB l(1) tc(1) PTR64-*uintptr
.   .   .   .   .   .   NAME-main..autotmp_6 a(true) l(1) x(0) class(PAUTO) esc(N) tc(1) assigned used INTER-interface {}
.   .   .   .   NOT l(1) tc(1) hascall bool
.   .   .   .   .   CALLFUNC l(1) tc(1) hascall bool
.   .   .   .   .   .   NAME-runtime.efaceeq a(true) x(0) class(PFUNC) tc(1) used FUNC-func(*uintptr, unsafe.Pointer, unsafe.Pointer) bool
.   .   .   .   .   CALLFUNC-list
.   .   .   .   .   .   AS l(1) tc(1)
.   .   .   .   .   .   .   INDREGSP-SP a(true) l(1) x(0) tc(1) addrtaken main.__ PTR64-*uintptr
.   .   .   .   .   .   .   ITAB l(1) tc(1) PTR64-*uintptr
.   .   .   .   .   .   .   .   NAME-main..autotmp_7 a(true) l(1) x(0) class(PAUTO) esc(N) tc(1) assigned used INTER-interface {}

.   .   .   .   .   .   AS l(1) tc(1)
.   .   .   .   .   .   .   INDREGSP-SP a(true) l(1) x(8) tc(1) addrtaken main.__ TUNSAFEPTR-unsafe.Pointer
.   .   .   .   .   .   .   IDATA l(1) tc(1) TUNSAFEPTR-unsafe.Pointer
.   .   .   .   .   .   .   .   NAME-main..autotmp_7 a(true) l(1) x(0) class(PAUTO) esc(N) tc(1) assigned used INTER-interface {}

.   .   .   .   .   .   AS l(1) tc(1)
.   .   .   .   .   .   .   INDREGSP-SP a(true) l(1) x(16) tc(1) addrtaken main.__ TUNSAFEPTR-unsafe.Pointer
.   .   .   .   .   .   .   IDATA l(1) tc(1) TUNSAFEPTR-unsafe.Pointer
.   .   .   .   .   .   .   .   NAME-main..autotmp_6 a(true) l(1) x(0) class(PAUTO) esc(N) tc(1) assigned used INTER-interface {}
.   .   IF-body
.   .   .   RETURN l(1) tc(1)
.   .   .   RETURN-list
.   .   .   .   AS l(1) tc(1)
.   .   .   .   .   NAME-main.~r2 a(true) g(1) l(1) x(16) class(PPARAMOUT) f(1) bool
.   .   .   .   .   LITERAL-false a(true) l(1) tc(1) bool

.   RETURN l(1) tc(1)
.   RETURN-list
.   .   AS l(1) tc(1)
.   .   .   NAME-main.~r2 a(true) g(1) l(1) x(16) class(PPARAMOUT) f(1) bool
.   .   .   LITERAL-true a(true) l(1) tc(1) bool
enter type..eq.[2]interface {}
.   AS l(1)
.   .   NAME-main.~r2 a(true) g(1) l(1) x(16) class(PPARAMOUT) f(1) bool
```
</details>

### Adding filters

```shell
go tool compile -W main.go | grep before
```

<details>
<summary>Output</summary>

```
before d1
before d2
before d3
before main
before d2.func1
before d3.func1
before init
before type..hash.[2]interface {}
before type..eq.[2]interface {}
```
</details>