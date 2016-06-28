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