#RxJava学习

##amb
amb(Observable<? extends T> o1,Observable<? extends T> o2)  

发送第一个最先到达的Observable    

![amb](https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/amb.png)

##combineLatest
combineLatest(Observable<? extends T1> o1,Observable<? extends T2> o2,Func2<? super T1,? super T2,? extends R> combineFunction)

o1与o2结合生成新的Observable,结合的规则是o1发送时，检查o2上一个发送的内容，如果有内容，则通过combineFunction规则合并两个发送的内容，生成一个Observable并发送，如果o2还没发送，则o1不结合也不发送。o2反过来的规则也一样

![combineLatest](https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/combineLatest.png)

##concat
concat(Observable<? extends Observable<? extends T>> observables)  
  
连击多个observabale,按顺序发送

![concat](https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/concat.png)

##defer
public static <T> Observable<T> defer(Func0<Observable<T>> observableFactory)  
  
在创建Observable对象时不执行observableFactory的相关初始化代码，在subscribe时才执行  

![defer](https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/defer.png)

##empty
public static <T> Observable<T> empty()  
  
发送一个空的Observable  

![empty](https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/empty.png)

##error
public static <T> Observable<T> error(java.lang.Throwable exception) 
 
  
发送一个onError给subscriber  

![error](https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/error.png)

##from
public static <T> Observable<T> from(java.util.concurrent.Future<? extends T> future,Scheduler scheduler)  
  
将一个Feture类型发出，发出时先调用Feture的get方法返回发出的内容  
  
![from](https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/from.Future.s.png)
  
public static <T> Observable<T> from(java.lang.Iterable<? extends T> iterable)  

将一个Iterable及Array类型发出，依次将里面的Item发出  
  
![from](https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/from.png)

##fromCallable
public static <T> Observable<T> fromCallable(java.util.concurrent.Callable<? extends T> func)  
  
将Callable的get返回的结果发出  
  
![fromCallable](https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/fromCallable.png) 
  
##interval
public static Observable<java.lang.Long> interval(long interval,
java.util.concurrent.TimeUnit unit)  
  
每隔一段时间发出一段连续的数字  
  
![interval](https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/interval.png)

##just
public static <T> Observable<T> just(T t1,T t2)  
  
按照顺序发送1~n个对象  
  
![just](https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/just.m.png)  
  
##merge  
public static <T> Observable<T> merge(java.lang.Iterable<? extends Observable<? extends T>> sequences)  
  
将多个Observable和并成一个Observable发出，合并的规则是按照各个Observable发出的顺序进行合并，以最早结束的Observable作结束  
  
![merge](https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/merge.png)  
  
public static <T> Observable<T> merge(Observable<? extends Observable<? extends T>> source)  
  
将一个含有多个Observables的Observable中的所有的元素进行合并，依次发出合并的内容  
  
![merge](https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/merge.oo.png)
  
##mergeDelayError
public static <T> Observable<T> mergeDelayError(java.lang.Iterable<? extends Observable<? extends T>> sequences)  
  
merge过程中如果遇到error，暂不抛出，等到所有元素合并完才在最后抛出  
  
![mergeDelayError](https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/mergeDelayError.png)
  
##nest
public final Observable<Observable<T>> nest()  
  
将Observable<T>类型封装为Observable<Observable<T>>对象  
  
![nest](https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/nest.png)  
  
##never
public static <T> Observable<T> never()  
  
不发送任何东西  
  
![never](https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/never.png)  
  
##range
public static Observable<java.lang.Integer> range(int start,int count)  
  
从start开始发送，一直发送到start + count - 1  
  
![range](https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/range.png)  
  
##sequenceEqual  
public static <T> Observable<java.lang.Boolean> sequenceEqual(Observable<? extends T> first,Observable<? extends T> second)  
  
对比两个Observable中的Item,如果Item的个数及内容一样，就返回一个Observable<Boolean>为true的类型，否则返回false类型，返回的时机是遇到第一个不相等的元素  
  
![sequenceEqual](https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/sequenceEqual.png)  

##switchOnNext  
public static <T> Observable<T> switchOnNext(Observable<? extends Observable<? extends T>> sequenceOfSequences)  
  
连接2个及以上的Observable到一个Observable，连接的规则是后面的Observable开始发射后，前面的Observable后面的Item就不再发送  
  
![switchOnNext](https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/switchDo.png)  
  
##switchOnNextDelayError
public static <T> Observable<T> switchOnNextDelayError(Observable<? extends Observable<? extends T>> sequenceOfSequences)  
  
与switchOnNext一样，不过在中途遇到异常在结束后才抛出  
  
