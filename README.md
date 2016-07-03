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
  
将多个Observable和并成一个Observable发出，合并的规则是按照各个Observable发出的顺序进行合并，中途遇到异常则直接抛出
  
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
  
##timer  
public static Observable<java.lang.Long> timer(long initialDelay,
                                          long period,
                                          java.util.concurrent.TimeUnit unit)  
  
每隔一段时间就发送一次元素，元素从0开始
  
![timer](https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/timer.p.png)  
  
public static Observable<java.lang.Long> timer(long delay,
                               java.util.concurrent.TimeUnit unit)  
  
延迟delay个时间间隔后发送一次Item  
  
![timer](https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/timer.png) 
  

##zip
public static <R> Observable<R> zip(java.lang.Iterable<? extends Observable<?>> ws,
                    FuncN<? extends R> zipFunction)  
  
将多个Observable通过zipFunction压缩成一个Observable

![zip](https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/zip.png)  
  
public static <R> Observable<R> zip(Observable<? extends Observable<?>> ws,
                    FuncN<? extends R> zipFunction)  
  
将一个发射多个Observable的Observable通过zipFunction压缩成一个只发送不是Observable类型的元素  
  
![zip](https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/zip.o.png)  
  
##all
public final Observable<java.lang.Boolean> all(Func1<? super T,java.lang.Boolean> predicate)  
  
将当前的Observable发出的元素通过predicate方法判断是否符合条件，返回Observable<java.lang.Boolean>类型，全部正确则为true，否则为false  
  
![all](https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/all.png)  
  
##ambWith  
public final Observable<T> ambWith(Observable<? extends T> t1)  
  
将当前的Observable与参数中的比较，返回先发射出的Observable  
  
![ambWith](https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/amb.png)

##buffer
public final <TClosing> Observable<java.util.List<T>> buffer(Func0<? extends Observable<? extends TClosing>> bufferClosingSelector)  
  
将一个发射多个元素的Observable拆分成多个发送元素List的Observable，拆分的方法由参数中bufferClosingSelector方法返回的Observable决定  
  
![buffer](https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/buffer1.png)  
  
public final Observable<java.util.List<T>> buffer(int count) 
  
将一个发射多个元素的Observable拆分成多个发送元素List的Observable，按照传入的数量进行拆分 
  
![buffer](https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/buffer3.png) 
  
public final Observable<java.util.List<T>> buffer(int count,
                                   int skip)  
  
将一个发射多个元素的Observable拆分成多个发送元素List的Observable，按照传入的数量进行拆分，每拆分一次，则跳过拆分开始后的第skip个元素  
  
![buffer](https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/buffer4.png)  
  
public final Observable<java.util.List<T>> buffer(long timespan,
                                   long timeshift,
                                   java.util.concurrent.TimeUnit unit)  
  
将一个发射多个元素的Observable拆分成多个发送元素List的Observable，按timespan的时间间隔进行拆分，拆分完后等待timeshift时间再进行下一次拆分，这段时间内发射的元素将会被抛弃,拆分的时间内没有元素则发送一个空List
  
![buffer](https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/buffer7.png)  
  
public final Observable<java.util.List<T>> buffer(long timespan,
                                   java.util.concurrent.TimeUnit unit,
                                   int count)  
  
将一个发射多个元素的Observable拆分成多个发送元素List的Observable，按timespan的时间间隔进行拆分，并且拆分后的最大个数限定为count个，如果当前元素超过两个，则超过的那元素则在下个timespan发射一个单独的List，如果timespan不满两个且上一个timespan没有剩下的元素，则在当前timespan开始时发射一个空的List。如果timespan不满两个且上一个timespan有剩下的元素，则在当前timespan结束时发射一个空的List。在所有timespan结束后也发一个空的List。
  
![buffer](https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/buffer6.png) 
  
public final <TOpening,TClosing> Observable<java.util.List<T>> buffer(Observable<? extends TOpening> bufferOpenings, Func1<? super TOpening,? extends Observable<? extends TClosing>> bufferClosingSelector)  
  
将一个发射多个元素的Observable拆分成多个发送元素List的Observable，拆分的开始由bufferOpenings的Observable决定，拆分的结束由bufferClosingSelector的Observable决定  
  
![buffer](https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/buffer2.png) 
  
public final <B> Observable<java.util.List<T>> buffer(Observable<B> boundary)  
  
将一个发射多个元素的Observable拆分成多个发送元素List的Observable，拆分的边界由boundary决定  
  
![buffer](https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/buffer2.png) 
  
##cache
public final Observable<T> cache()  
  
订阅前已经发送过的元素在订阅后也会发射  
  
![cache](https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/cache.png) 
  
##cast  
public final <R> Observable<R> cast(java.lang.Class<R> klass)  
  
将当前Observable的所有元素转化成指定的class类型  
  
![cast](https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/cast.png) 
  
##collect
public final <R> Observable<R> collect(Func0<R> stateFactory,
                        Action2<R,? super T> collector)
  
将发送的元素通过collector收集起来，与下一个发送的元素结合，最后发送一个集合  
  
![](https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/collect.png)  
  
##concatMap  
public final <R> Observable<R> concatMap(Func1<? super T,? extends Observable<? extends R>> func)  
  
将当前Observable中的元素通过func转化成Observable，并把转化后的每个Observable按照顺序发射到一个Observable中  
  
![concatMap](https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/concatMap.png)  
  
##concatWith
public final Observable<T> concatWith(Observable<? extends T> t1)  
  
将当前的Observable与参数中的Observable相连接  
  
![concatWith](https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/concat.png)  
  
##contains  
public final Observable<java.lang.Boolean> contains(java.lang.Object element)  
  
检查当前Observable中是否包含某元素  
  
![contains](https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/contains.png)  
  
  
  
