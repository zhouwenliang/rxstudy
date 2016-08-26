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
  
![collect](https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/collect.png)  
  
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
  
##count/countLong  
public final Observable<java.lang.Integer> count()  
  
返回Observable中的元素个数  
  
![count](https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/count.png) 
  
##debounce
public final <U> Observable<T> debounce(Func1<? super T,? extends Observable<U>> debounceSelector)  
  
当前Observable发出的元素都经过debounceSelector转化成一个Observable<U>类型，并根据转化后的U类型进行发送，如果转化后的Observable的生命周期有重叠，则前面那个Observable不发送  
  
![debounce](https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/debounce.f.png) 
  
public final Observable<T> debounce(long timeout,
                     java.util.concurrent.TimeUnit unit)  
  
过timeout时间后才发射元素，如果在timeout时间内有另外一个元素，则取消上一个的发送及timeout，重新发送一个timeount  
  
![debounce](https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/debounce.png) 
  
##defaultIfEmpty 
public final Observable<T> defaultIfEmpty(T defaultValue)  
  
如果当前Observable为empty的话，则发送一个默认值  
  
![defaultIfEmpty](https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/defaultIfEmpty.png) 
  
##delay
public final <U,V> Observable<T> delay(Func0<? extends Observable<U>> subscriptionDelay,
                        Func1<? super T,? extends Observable<V>> itemDelay)  
  
订阅这个Observable时延迟一段时间才生效，订阅延迟时间由subscriptionDelay发送的时间决定，Item的延迟由itemDelay发送的时间决定
  
![delay](https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/delay.oo.png) 
  
public final Observable<T> delay(long delay,
                  java.util.concurrent.TimeUnit unit)  
  
这个Observable的元素整体延迟delay个时间间隔发送  
 
![delay](https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/delay.png) 

##delaySubscription
public final <U> Observable<T> delaySubscription(Func0<? extends Observable<U>> subscriptionDelay)  
  
延迟订阅，调用调阅后等subscriptionDelay发送元素后才真正订阅  
  
![delaySubscription](https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/delaySubscription.o.png) 
  
##dematerialize  
public final <T2> Observable<T2> dematerialize() 
  
将当前Observable<Notification<T>>类型的Observable还原为对应的Observable<T>  
  
![dematerialize](https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/dematerialize.png) 
  
##distinct  
public final Observable<T> distinct()  
  
去掉当前Observable中的重复元素 
  
![distinct](https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/distinct.png) 
  
public final <U> Observable<T> distinct(Func1<? super T,? extends U> keySelector)  
  
每个元素都会经过keySelector返回一个Key，根据返回的Key是否相等进行过滤  
  
![distinct](https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/distinct.key.png) 
  
##distinctUntilChanged  
public final Observable<T> distinctUntilChanged()  
  
过滤重复过滤的元素  
  
![distinctUntilChanged](https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/distinctUntilChanged.png) 
  
public final <U> Observable<T> distinctUntilChanged(Func1<? super T,? extends U> keySelector)  
  
每个元素都会经过keySelector返回一个Key，过滤掉Key相等且连续的元素  
  
![distinctUntilChanged](https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/distinctUntilChanged.key.png) 
  
##doOnCompleted
public final Observable<T> doOnCompleted(Action0 onCompleted)  
  
在发送完所有元素后调用onCompleted方法  
  
![doOnCompleted](https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/doOnCompleted.png)

##doOnEach  
public final Observable<T> doOnEach(Action1<Notification<? super T>> onNotification) 
public final Observable<T> doOnEach(Observer<? super T> observer) 
  
对当前Observable的生命周期(onNext,onCompleted,onError)进行监听，作为参数调用onNotification 或 observer相对应的生命周期
  
![doOnEach](https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/doOnEach.png)
  
##doOnError  
public final Observable<T> doOnError(Action1<java.lang.Throwable> onError)  
  
在发送错误的时候调用onError方法  
  
![doOnError](https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/doOnError.png)  
  
#doOnNext
public final Observable<T> doOnNext(Action1<? super T> onNext)  
  
在发送每个元素的时候调用onNext方法  
  
![doOnNext](https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/doOnNext.png)  
  
##doOnSubscribe  
public final Observable<T> doOnSubscribe(Action0 subscribe)  
  
在当前Observable被subscrible的时候执行subscribe方法  
  
![doOnSubscribe](https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/doOnSubscribe.png) 
  
##doOnTerminate
public final Observable<T> doOnTerminate(Action0 onTerminate)  
  
当Observable在onCompleted的时候调用onTerminate方法  
  
![doOnTerminate](https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/doOnSubscribe.png) 
  
##doOnUnsubscribe  
public final Observable<T> doOnUnsubscribe(Action0 unsubscribe)  
  
在Observable被unsubscribe时调用unsubscribe方法  
  
![doOnUnsubscribe](https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/doOnUnsubscribe.png) 
  
##elementAt  
public final Observable<T> elementAt(int index)  
  
只发送index为参数中的index的的元素  
  
![elementAt](https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/elementAt.png) 
  
##elementAt
public final Observable<T> elementAtOrDefault(int index,
                               T defaultValue)  
  
发送index为参数中的index的的元素，若不存在则发送defaultValue  
  
![elementAtOrDefault](https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/elementAtOrDefault.png) 
  
##exists  
public final Observable<java.lang.Boolean> exists(Func1<? super T,java.lang.Boolean> predicate)  
  
通过predicate判断Observable中是否包含某个元素(或符合某个条件)，如果有则返回True的Observable，否则返回False的Observable  
  
![exists](https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/exists.png) 
  
##filter
public final Observable<T> filter(Func1<? super T,java.lang.Boolean> predicate)  
  
通过predicate过滤符合条件的元素  
  
![filter](https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/filter.png) 
  
##finallyDo
public final Observable<T> finallyDo(Action0 action)  
  
在onCompeleted之后执行action方法  
  
![finallyDo](https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/finallyDo.png) 
  
##doAfterTerminate  
public final Observable<T> doAfterTerminate(Action0 action)  
  
在onCompeleted之后执行action方法 
  
![doAfterTerminate](https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/finallyDo.png) 
  
##first  
public final Observable<T> first()  
  
只发送第一个元素  
  
![first](https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/first.png) 
  
public final Observable<T> first(Func1<? super T,java.lang.Boolean> predicate)  
  
只发送第一个符合predicate条件的元素
  
![first](https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/firstN.png) 
  
##firstOrDefault  
public final Observable<T> firstOrDefault(T defaultValue)  
  
发送一个元素，没有元素就发送默认值defaultValue  
  
![firstOrDefault](https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/firstOrDefault.png) 
  
##flatMap  
public final <R> Observable<R> flatMap(Func1<? super T,? extends Observable<? extends R>> func)  
  
将当前Observable中的每个元素通过func转化成Observable<? extends R>类型，并按顺序发出转化后的Observable中的每个元素  
  
![flatMap](https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/flatMap.png) 
  
##flatMapIterable  
public final <R> Observable<R> flatMapIterable(Func1<? super T,? extends java.lang.Iterable<? extends R>> collectionSelector)  
  
将当前Observable中的每个元素通过collectionSelector转化成Iterable对象，并依次发出Iterable中的元素  
  
![flatMapIterable](https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/mergeMapIterable.png) 
  
##groupBy  
public final <K> Observable<GroupedObservable<K,T>> groupBy(Func1<? super T,? extends K> keySelector)  
  
将当前Observable中具有相同特征的元素组合成一个Observable，是否有相同特征由keySelector决定  
  
![groupBy](https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/groupBy.png) 
  
##ignoreElements  
public final Observable<T> ignoreElements()  
  
忽略Observable中的所有元素  
  
![ignoreElements](https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/ignoreElements.png) 
  
##isEmpty
public final Observable<java.lang.Boolean> isEmpty()  
  
当前Observable中含有元素就返回true,否则返回false
  
![isEmpty](https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/isEmpty.png) 
  
##join  
public final <TRight,TLeftDuration,TRightDuration,R> Observable<R> join(Observable<TRight> right,
                                                         Func1<T,Observable<TLeftDuration>> leftDurationSelector,
                                                         Func1<TRight,Observable<TRightDuration>> rightDurationSelector,
                                                         Func2<T,TRight,R> resultSelector)  
  
当前Observable与另外一个Observable融合  
  
![join](https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/join_.png) 
  
##last  
public final Observable<T> last()  
  
返回Observable最后一个元素，如果没有，则抛出NoSuchElementException  
  
![last](https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/last.png) 
  
##lastOrDefault  
public final Observable<T> lastOrDefault(T defaultValue)  
  
返回Observable最后一个元素，如果没有，则返回defaultValue  
  
![lastOrDefault](https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/lastOrDefault.png)  
  
##limit  
public final Observable<T> limit(int count)  
  
限定Observable的元素个数  
  
![limit](https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/take.png) 
  
##map  
public final <R> Observable<R> map(Func1<? super T,? extends R> func)  
  
将Observable发送的元素作类型转换  
  
![map](https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/map.png) 
  
##materialize  
public final Observable<Notification<T>> materialize()  
  
将Observable中的元素转化成Notification<T>类型发射  
  
![materialize](https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/materialize.png) 