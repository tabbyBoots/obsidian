### [[overlord]] [[java]]

#### 同一類別的方法有多重功能，且方法的名稱一樣。

#### 例如：
```java
static String cvrtString(String a) { //方法的名稱一樣，但功能不同

	char tmp;
	String result = "";

	for(int i=0; i < a.length(); i++) {	
		tmp = a.charAt(i);		
		if(tmp >= 97 ) {		
			tmp -= 32;		
		}else if(tmp <= 97 && tmp >= 65){		
			tmp +=32;	
		}	
		result += tmp;
		}
		return result;
	}

static char cvrtString(char a) { //方法的名稱一樣，但功能不同

	if(a > 97) {
		a -= 32;
	}else if(a < 97 && a > 64){
		a +=32;
	}
	return a;
}
```

