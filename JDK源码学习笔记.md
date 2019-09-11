        
        
# JDK源码学习（JDK1.8）  <优先级1-4逐级递减>
author: wty 2019.9.9<hr/>
## 1.java.lang包
### 1) Object 1 
    方法有：
    wait()、notify()、notifyAll()、wait(timeout)、wait(timeout,nanos)、hashCode()、equals()、clone()、toString()、registry..()、getClass()、finalize()
#### wait：
    Object中有三个wait方法，无参为平时用的方法，内部调用的是单参的wait方法；双参函数nanos为纳秒，nanos>0则timout++
#### registry..()：
    该方法为Object方法静态代码块中调用的方法
#### clone():
    使用后，两个对象==为false，getClass()为true
#### toString()：
> getClass().getName()+"@"+Integer.toHexString(hashCode());//类名@16进制的Hash值
#### finalize(): 待深入
    当对象的引用为0时，执行清理；在不可撤销的丢弃前，进行清理操作。
    例如：输入输出对象的finalize方法，在彻底回收前，进行连接的关闭
#### 其他均为native方法
### 2) String 1 
#### 成员变量：
    char[] value , int hash
#### 常用方法：
##### String():
>   return "".value;
##### String(char[]或int[]或StringBuffer或StringBuilder):
    char[]内部调用Arrays.copyof()->内部调用System.arraycopy();
    int[]内部调用的是Character的校验方法及转换
    StringBuffer和StringBuilder与char[]一模一样，唯一的区别是StringBuffer加了同步
##### String(byte[]):可选参数编码名、编码对象。
    内部调用StringEncoding字符串编码类中的编码方法，不指定则用默认(utf-8(先)、ISO-8859-1(后))
#### checkBounds():
    校验offset+count是否小于length，否则报异常。
#### charAt(index):
> return value[index];
#### getBytes():可选参数编码名、编码对象。
#### compareTo(String):
    有一个长度为零，返回另一个长度；
    如果长度相等不为零，返回第一个不同字符的差，如都相同，返回长度差。
#### hashCode(): -> h = 31 * h + val[i];

### 3) AbstractStringBuilder 1
    主要方法有：
     char[] value、int count、扩容：翻倍，不够取所需最小
### 4) StringBuffer 1 
    继承AbstractStringBuilder、synchronized方法保证线程安全、char[] toStringCache
### 5) StringBuilder 1 继承AbstractStringBuilder
### 6) Boolean 2 
### 7) Byte 2
### 8) Double 2
### 9) Float 2
### 10) Integer 2
### 11) Long 2
### 12) Short 2
### 13) Thread 2
### 14) ThreadLocal 2
### 15) Enum 3
### 16) Throwable 3
### 17) Error 3
### 18) Exception 3
### 19) Class 4
### 20) ClassLoader 4
### 21) Compiler 4
### 22) System 4
### 23) Package 4
### 24) Void 4
## 2.java.util
    1) AbstractList 1
    2) AbstractMap 1
    3) AbstractSet 1
    4) ArrayList 1 Object[] elementData、int size、默认大小10、扩容：1.5倍，不够取所需最小
    5) LinkedList 1 Node {E item, Node prev, Node next}、int size、Node first、Node last、linkFirst(), linkLast(), linkBefore(), unLinkFirst(), unLinkLast(), unLink(), indexOf()
    6) HashMap 1 Node{int hash, K key, V value, Node next}、默认容量16，负载因子0.75f、int size, modCount, threshold, float loadFactor、Node[] table、Set entrySet、put():根据key算hash，根据容量和hash算index，table[index]没有直接添加到数组中，table[index]有，若index位置同一个key则更新，否则遍历next是否有，有则更新，无则新增，最后根据thread与size判断是否扩容。注：扩容时容量翻倍，重新算hash复制到新数组、get()类似 注：先比较hash，若相等在比较equals
    7) Hashtable 1
    8) HashSet 1
    9) LinkedHashMap 1
    10) LinkedHashSet 1
    11) TreeMap 1
    12) TreeSet 1
    13) Vector 2
    14) Queue 2
    15) Stack 2
    16) SortedMap 2
    17) SortedSet 2
    18) Collections 3
    19) Arrays 3
    20) Comparator 3
    21) Iterator 3
    22) Base64 4
    23) Date 4
    24) EventListener 4
    25) Random 4
    26) SubList 4
    27) Timer 4
    28) UUID 4
    29) WeakHashMap 4
## 3.java.util.concurrent
    1) ConcurrentHashMap 1
    2) Executor 2
    3) AbstractExecutorService 2
    4) ExecutorService 2
    5) ThreadPoolExecutor 2
    6) BlockingQueue 2
    7）AbstractQueuedSynchronizer 2
    8）CountDownLatch 2
    9) FutureTask 2
    10）Semaphore 2
    11）CyclicBarrier 2
    13）CopyOnWriteArrayList 3
    14）SynchronousQueue 3
    15）BlockingDeque 3
    16) Callable 4
## 4.java.util.concurrent.atomic
    1) AtomicBoolean 2
    2) AtomicInteger 2
    3) AtomicLong 2
    4) AtomicReference 3
## 5.java.lang.reflect
    1) Field 2
    2) Method 2
6.java.lang.annotatin
    1) Annotation 3
    2) Target 3
    3) Inherited 3
    4) Retention 3
    5) Documented 4
    6) ElementType 4
    7) Native 4
    8) Repeatable 4
7.java.util.concurrent.locks
    1) Lock 2
    2) Condition 2
    3) ReentrantLock 2
    4) ReentrantReadWriteLock 2
8.java.io
    1) File 3
    2) InputStream   3
    3) OutputStream  3
    4) Reader  4
    5) Writer  4
9.java.nio
    1) Buffer 3
    2) ByteBuffer 4
    3) CharBuffer 4
    4) DoubleBuffer 4
    5) FloatBuffer 4
    6) IntBuffer 4
    7) LongBuffer 4
    8) ShortBuffer 4
10.java.sql
    1) Connection 3
    2) Driver 3
    3) DriverManager 3
    4) JDBCType 3
    5) ResultSet 4
    6) Statement 4
11.java.net
    1) Socket 3
    2) ServerSocket 3
    3) URI 4
    4) URL 4
    5) URLEncoder 4
