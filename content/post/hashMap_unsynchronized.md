---
title: "HashMap为什么是线程不安全的"
date: 2020-05-20T11:00:07+08:00
draft: false
---

### HashMap注释

The HashMap  class is roughly equivalent to  Hashtable , except that it is  <font color="#FF0000"> unsynchronized </font> 
and permits nulls。

<br>

HashMap类与Hashtable大致等效，不同之处在于它是不同步的，并且允许为null。

### 为什么HashMap是线程不安全的
1. put操作会调用addEntry，多线程操作同一个键造成数据覆盖
```
void addEntry(int hash, K key, V value, int bucketIndex) {
	Entry<K,V> e = table[bucketIndex];
        table[bucketIndex] = new Entry<K,V>(hash, key, value, e);
        if (size++ >= threshold)
            resize(2 * table.length);
}
```
2. 删除键值对操作，多线程操作，键位置改变，造成数据丢失
```
final Entry<K,V> removeEntryForKey(Object key) {
        int hash = (key == null) ? 0 : hash(key.hashCode());
        int i = indexFor(hash, table.length);
        Entry<K,V> prev = table[i];
        Entry<K,V> e = prev;
 
        while (e != null) {
            Entry<K,V> next = e.next;
            Object k;
            if (e.hash == hash &&
                ((k = e.key) == key || (key != null && key.equals(k)))) {
                modCount++;
                size--;
                if (prev == e)
                    table[i] = next;
                else
                    prev.next = next;
                e.recordRemoval(this);
                return e;
            }
            prev = e;
            e = next;
        }
 
        return e;
}
```
3. addEntry中当加入新的键值对后键值对总数量超过门限值的时候会调用一个resize操作
扩容的时候可能会变成一个死循环链表，造成cpu占比100%

```
void resize(int newCapacity) {
        Entry[] oldTable = table;
        int oldCapacity = oldTable.length;
        if (oldCapacity == MAXIMUM_CAPACITY) {
            threshold = Integer.MAX_VALUE;
            return;
        }
 
        Entry[] newTable = new Entry[newCapacity];
        transfer(newTable);
        table = newTable;
        threshold = (int)(newCapacity * loadFactor);
}
```




