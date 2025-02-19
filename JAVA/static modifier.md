### [[java]]　

#### 方法前面沒有 `static` 字樣，表示使用前必須重新分配記憶體 (要用 `new`)

example:
```java
public class Ex04 {
	public static void main(String[] args) {
	
		int[] source = {55, 66 , 80, 117, 6};
		Ex04 ss = new Ex04(); //<-------------就是這裡要加 [ new ]
		
		System.out.println(Arrays.toString(source) );
		System.out.print("Max: " + ss.max(source) );
		System.out.println("Min: " + min(source) );//有宣告static所以不用實體化
	}

	int max( int[] source ) {
		int result = source[0];
	
		for( int tmp : source) {
			if( tmp > result ) {
				result = tmp;
			}
		}
		return result;
	}
	static int min( int[] source ) {
		int result = source[0];
		for( int tmp : source) {
			if( tmp < result ) {
				result = tmp;
			}
		}
		return result;
	}
}
```

