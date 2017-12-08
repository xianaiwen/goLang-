google 于 2011年 发布正式版Go1。  
效率与性能并存。

## 数据类型：  

**boolean**  

**数字类型**  
有符号： （int8, int16, int32, int64)  
无符号： （uint8, uint16, uint32, uint64）  
浮点：float32, float64, 实数和虚数(complex64, complex128)     **牛逼**  
int, uint(32位 或 64位)

## 变量声明（声明的变量必须使用）
- var a 默认值:（**int: 0，string: '', bool: false**）
- var a = 111
- var a int = 111
- a:= 111 (只能在函数内部出现)
- &a 获取变量a的内存地址
- 声明多个变量 var a,b,c
- 变量值交换 a,b = b,a 
- _,b = 5, 7 (表示只声明了 变量b， 5的值被抛弃)

## 常量声明
const a = 111;  

特殊常量 iota 初值为 0  (下一个const 出现 iota重置为 0)

		const (
			a = iota
			b
			c
		)
		a= 0, b=2, c=3

## 运算操作

 **位运算**  
	
- & , | , ^(异或)
- << n	(乘以2的n次方）
- &gt;&gt; n  (除以2的n次方)

## 函数
 		//返回多个值  
		func get(x, y string) (string, string) {
			return x, y
		}
		//方法
		type A struct {
			b int
		}
		func（c A）get() int {
			return c.b		
		}


## 数组  
		var a = [5]float32{100.0, 10.0, 1.0, 2.0, 3.0}
		var a = []float32{100.0, 10.0, 1.0, 2.0, 3.0}
		//多维数组
		var b = [3][4]int (3行4列)

## 指针
		//声明指针变量
		var p = *int
		var a = 20
		p = &a
		*p = 20
		空指针 nil

## 结构体（对象）  new操作
		type A strict {
			property1 string,
			property2 string,
			property3 bool,
		}
		
		var b A

## 切片（slice）
		//int类型，len= 3 （长度），cap=5（容量）
		var a = make([]int, 3, 5)
		//截取下标1到3
		var b = a[1:4]
		//添加元素2,3,4
		a.append(a,2,3,4)
		//复制a到c
		copy（c，a）
		
## range
		nums := []int{2, 3, 4}
		// 用于切片或map
		for index, num := range nums {
			Println(index + num)
		}

## map（键值对）
		// map[key_type]value_type
		var a = map[string]string{'a': 'b'}
		//delete 方法
		delete(a, 'a')

## 接口
		//定义接口
		type Phone interface {
			call()
		}
		//定义结构体
		type NokiaPhone struct {
		}
		//定义方法
		func (nokiaPhone NokiaPhone) call() {
			println(1)
		}
		type IPhone struct {
		}
		
		func (iPhone IPhone) call() {
		    fmt.Println("I am iPhone, I can call you!")
		}
		func main() {
			var phone Phone
			phone = new(NokiaPhone)
			phone.call()
			phone = new(IPhone)
   			phone.call()	
		}

## 错误
		// 定义一个 DivideError 结构
		type DivideError struct {
		    dividee int
		    divider int
		}
		
		// 实现     `error` 接口（内置error接口）
		func (de *DivideError) Error() string {
		    strFormat := `
			    Cannot proceed, the divider is zero.
			    dividee: %d
			    divider: 0
			`
		    return fmt.Sprintf(strFormat, de.dividee)
		}
		
		// 定义 `int` 类型除法运算的函数
		func Divide(varDividee int, varDivider int) (result int, errorMsg string) {
		    if varDivider == 0 {
		        dData := DivideError{
		            dividee: varDividee,
		            divider: varDivider,
		        }
		        errorMsg = dData.Error()
		        return
		    } else {
		        return varDividee / varDivider, ""
		    }
		
		}
