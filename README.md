# Boost C++11 Algorithms

## all_of

Algoritma, bir dizinin tüm öğelerini test eder ve hepsi bir özelliği paylaşıyorsa true değerini döndürür.

all_of_equal  dizideki her öğe, iletilen değere eşitse, true değerini döndürür.

```
c={ 0, 1, 2, 3, 14, 15 }

bool isOdd ( int i ) { return i % 2 == 1; }
bool lessThan10 ( int i ) { return i < 10; }

using boost::algorithm;
all_of ( c, isOdd ) --> false
all_of ( c.begin (), c.end (), lessThan10 ) --> false
all_of ( c.begin (), c.begin () + 3, lessThan10 ) --> true
all_of ( c.end (), c.end (), isOdd ) --> true  // empty range
all_of_equal ( c, 3 ) --> false
all_of_equal ( c.begin () + 3, c.begin () + 4, 3 ) --> true
all_of_equal ( c.begin (), c.begin (), 99 ) --> true  // empty range

```

## any_of

Dizideki herhangi bir öğe için yüklem true değerini döndürürse true değerini döndürür.

any_of_equal dizideki herhangi bir öğe, iletilen değere eşitse, true değerini döndürür.

```
c= { 0, 1, 2, 3, 14, 15 }

bool isOdd ( int i ) { return i % 2 == 1; }
bool lessThan10 ( int i ) { return i < 10; }

using boost::algorithm;
any_of ( c, isOdd ) --> true
any_of ( c.begin (), c.end (), lessThan10 ) --> true     //c.begin=0 ,c.end=15 , 15 10dan küçük değil ama herhangi birinin küçük olması yeterli şart o yüzden true
any_of ( c.begin () + 4, c.end (), lessThan10 ) --> false
any_of ( c.end (), c.end (), isOdd ) --> false  // empty range
any_of_equal ( c, 3 ) --> true
any_of_equal ( c.begin (), c.begin () + 3, 3 ) --> false
any_of_equal ( c.begin (), c.begin (), 99 ) --> false  // empty range


```


## one_of

Dizideki bir öğe için yüklem true değerini döndürürse true değerini döndürür.

one_of_equal dizideki bir öğe, iletilen değere eşitse, true değerini döndürür.


```
c={ 0, 1, 2, 3, 14, 15 }

bool isOdd ( int i ) { return i % 2 == 1; }
bool lessThan10 ( int i ) { return i < 10; }

using boost::algorithm;
one_of ( c, isOdd ) --> false                                  //birden fazla tek olduğu için false döner
one_of ( c.begin (), c.end (), lessThan10 ) --> false          //c.begin=0 ,c.end=15 , 15 10dan küçük değil o yüzden false
one_of ( c.begin () + 3, c.end (), lessThan10 ) --> true       // hepsinde bir tane şartı sağlayan olduğundan true
one_of ( c.end (), c.end (), isOdd ) --> false  // empty range
one_of_equal ( c, 3 ) --> true                                //şartı sağlayan bir tane var
one_of_equal ( c.begin (), c.begin () + 3, 3 ) --> false
one_of_equal ( c.begin (), c.begin (), 99 ) --> false  // empty range



```



## is_sorted

Bir dizinin bazı kriterlere göre tamamen sıralanıp sıralanmadığını belirler. Herhangi bir kriter belirtilmemişse dizinin azalıp azalmadığını kontrol eder.

## is_partitioned

--


## is_permutation

 Algoritma, bir dizinin ikincisinin bir permütasyonu olup olmadığını test eder; başka bir deyişle, muhtemelen farklı bir sırada tüm aynı üyeleri içerir.
 
```
 c1 = { 0, 1, 2, 3, 14, 15 },  c2 = { 15, 14, 3, 1, 2 }
 
 
 is_permutation ( c1.begin(),     c1.end (), c2.begin(), c2.end ()) --> false
is_permutation ( c1.begin() + 1, c1.end (), c2.begin(), c2.end ()) --> true

is_permutation ( c1.end (), c1.end (), c2.end(), c2.end ()) --> true  // all empty ranges are permutations of each other


```

## partition_point

. Bölümlenmiş bir dizi ve bir yüklem verildiğinde, algoritma bölüm noktasını bulur; yani, dizideki yüklemi karşılamayan ilk öğe.

```
c={ 0, 1, 2, 3, 14, 15 }

 lessThan10 ( int i ) { return i < 10; }
bool isOdd ( int i ) { return i % 2 == 1; }

partition_point ( c, lessThan10 ) --> c.begin () + 4  (pointing at 14)
partition_point ( c.begin (), c.end (), lessThan10 ) --> c.begin () + 4  (pointing at 14)
partition_point ( c.begin (), c.begin () + 3, lessThan10 ) -> c.begin () + 3 (end)
partition_point ( c.end (), c.end (), isOdd ) --> c.end ()  // empty range

```










