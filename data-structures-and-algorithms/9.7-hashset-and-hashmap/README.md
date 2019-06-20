# 9.7 HashSet & HashMap

## 1. What is Hash?

### a. Hash Value

Hash 是根据文件的内容的数据通过逻辑运算得到的数值，不同的文件（即使是相同的文件名）得到的Hash值也是不同的，所以Hash值就成了每一个文件在电驴\(eMule\)里的身份证。这是 通过随机数生成的。其生成的密钥很难再现。

### b. Hash Function

Hash Function性质：如果两个Hash值（散列值）是不相同的（根据同一函数），那么这两个Hash值的原始输入也是不相同的。这个疼醒是Hash函数具有确定性的结果。

### c. Hash Algorithm \(e.g. MD5\)

Hash Algorithm：是一种凑够任意文件中创造小的数字“指纹”的方法。这是一种以较短的信息来保证文件唯一性的标志，这种标志与文件的每一个字节都相关，而且难以找到你想规律。因此，当原有文件发生改变时，其标志值也会发生改变，从而高速文件使用者当前的文件已经不是你所需求的文件。

特点：

* 正向快速：给定铭文和Hash算法，在有限时间和有限资源内能计算出Hash值
* 逆向困难：给定（若干）Hash值，在有限时间内很难（基本不可能）逆推出明文
* 输入敏感：原始输入信息修改一点信息，产生的额Hash值看起来应该都大不相同
* 冲突避免：很难找到两段内容不同的明文，是的它们的Hash值一致（发生冲突）。

### d. Hash in Java

| 数据类型 | 查找 | 添加/删除 | 空间 |  |
| :--- | :--- | :--- | :--- | :--- |
| ArrayList | O\(1\) | O\(1\) | O\(N\) | O\(N\) |
| LinkedList | O\(N\) | O\(N\) | O\(1\) | O\(N\) |
| HashMap | O\(N/Bucket\_size\) | O\(N/Bucket\_size\) | O\(N/Bucket\_size\) | O\(N\) |

由上表可以看出HashMap整体上性能都非常不错，但是不稳定，为O\(N/Buckets\)，N就是数组中没有发生碰撞的元素，Buckets是因碰撞产生的链表

{% hint style="info" %}
但是实际上，发生碰撞的情况非常少，所以N/Bucket\_size约等于1
{% endhint %}

## 2. HashMap & HashSet

| **HashMap** | **HashSet** |
| :--- | :--- |
| HashMap实现了Map接口 | HashSet实现了Set接口 |
| HashMap储存键值对 | HashSet仅仅存储对象 |
| 使用put\(\)方法将元素放入map中 | 使用add\(\)方法将元素放入set中 |
| HashMap中使用键对象来计算hashcode的值 | HashSet使用成员对象来计算hashcode的值，对于两个对象来说hashcode可能相同，所以equals\(\)方法用来判断对象的相等性，如果两个对象不同的话，那么返回false |
| HashMap比较快，因为是使用唯一的键来获取对象 | HashSet较HashMap来说比较慢 |

## 3. HashMap & HashTable

他们两者的主要区别其实就是Table全局加了线程同步保护

* HashTable线程更加安全，代价就是因为它粗暴的添加了同步锁，所以会有性能损失
* 其实有更好的concurrentHashMap可以代替HashTable，一个是方法级，一个是Class级

