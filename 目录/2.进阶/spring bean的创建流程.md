spring bean的创建流程
1.首先是获取bean对象：getBean(),getBean()调用了doGetBean()。
2.doGetbean()首先调用getSingleBean()从spring容器中获取单例bean对象，若没有获取到调用createBean（），createBean()调用了doCreateBean()来创建bean对象。
3.doCreateBean()方法内主要执行了createBeanInstance(),populateBean(),initalizeBean()3个方法来进行bean实例的创建，属性依赖的注入，bean初始化来完成一个spring完整bean对象的创建。
4.createBeanInstance():创建bean实例（使用合适的实例化策略来创建新的实例：工厂方法，构造函数自动注入，简单初始化）。若满足循环依赖条件，将创建bean实例的ObjectFactory加入FactoryMap工厂容器中。（循环依赖条件：单例且允许循环依赖属性为true（默认为true） 且 当前bean处于创建中。
5.populateBean():依赖注入，即setXX(@Autowird的bean），为bean实例设置属性。
6.initalizeBean(): spring 对这个bean对象进行一些初始化操作:applyBeanPostProcessorsBeforeInitialization(初始化前置回调），invokeInitMethods(初始化方法），applyBeanPostProcessorsAfterInitialization(初始化后置回调）。init-method方法的执行。

7.循环依赖的处理。若有循环依赖会去从FactoryMap获取ObjectFactory, 从ObjectFactory获取bean
