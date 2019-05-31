
【第10次讨论主题：集合转数组】

1）ArrayList.toArray()推荐有参数，还是无参数，为什么？

推荐有参数。
无参数的方法是构造一个Object数组，然后进行数据拷贝，如果想将Object[] 转化为String[]，则会报错，转化只能取出每个元素再转化，
所有这个方法就不是那么方便了。而带参数的toArray方法，则是根据参数数组的类型，构造了一个对应类型的，虽然方法本身还是以Object
数组的形式返回结果，不过由于构造数组使用的ComponentType跟需要转型的ComponentType一致，就不会产生转型异常。	 

2）如果有参数，那么参数的数组长度是多少？给出分析的逻辑思考。

参数的长度最好和数组长度相等										         

如果传入长度不够，就new一个返回。注释：// Make a new array of a's runtime type, but my contents:	

如果长度相等则直接进行拷贝                                                  							        

如果长度大于的话，将第size位置为null        		        

if (a.length > size)
    a[size] = null;
