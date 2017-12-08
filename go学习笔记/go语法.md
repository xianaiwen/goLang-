## 循环语句
		// 不需要括号
		for i := 0; i < 100; i++ {
			...
		}
		// 前置，后置为空 作为while使用
		a := 1
		for a<1000 {
			...
		}

## if语句
		//`if` 语句可以在条件之前执行一个简单的语句,由这个语句定义的变量的作用域仅在 if 范围之内
		if a := 111; a<11 {
			....
		} else {  // else 中可以使用 变量a
			return a
		}
		return a  // a undefined

## switch
		// case 后面自动加入break
		switch a: 1; a {
			case 1: 
				...
			case 2：
				...
		}

## defer 延迟
		defer func1 （） {}
		// 多个延时函数，栈顶先执行
		for i := 0; i < 10; i++ {
			defer fmt.Println(i)
		}
		// 9,8,7,6,5,4,3,2,1

## 结构体指针
		tpye A struct  {
			x int
			y int
		}
		p := &A
		//可省略* 同(*p).x
		p.x = 111

## 数组切片
		//capacity容量表示slice的首个下标在原始数组往后的个数
		var a = []int{1,2,3,4,5,6}
		a = a[:0] // lenth 6 capacity 6  a: []
		a = a[1,3] // 2 5 [2,3]
		a = a[2:] // 0 3 [] 

## map
		//map结构的0值为nil
		m:=make(map[string]int)
		m[key] = vlaue
		// 判断map结构中是否存在key， 不存在则v为类型0值(如： int 为0)，ok为false
		v, ok ：= m[key]

## 方法
		//在结构体上定义方法
		//通过结构体指针可以改变结构体
		// 采用结构体指针能避免每次调用方法进行数据拷贝
		func (v *a) b() int {
			...	
		}

## 接口
		