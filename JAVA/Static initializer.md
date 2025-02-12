### [[java]] [[類別]] [[static initializer]]

#### **Static initializer**的執行順序在建構子前

```java
　 static { //Static initializer
		System.out.println("In Static，Aage = " + age);
		age += 1; // 再將 age 加 1
	}

public StaticInitializer(){ //建構子
	System.out.println("In Cunstructor，Aage = " + age);
}
```

#### 再建立一次物件，**Static Initializer** 不會執行第二次

```java
public static void main(String[] args) {

	new StaticInitializer(); // 建立物件
	new StaticInitializer(); // Static Initializer不會執行第二次
}
```