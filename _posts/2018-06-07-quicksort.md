---
title:  "Быстрая сортировка"
date:   2018-06-07
categories: [Руководства]
tags: [Сортировки]
---

Примеры реализации быстрой сортировки.

<!--more-->

Пример реализации на языке Python:

{% highlight python %}
a = [6, 5, 3, 7, 8, 1, 9]

def qsort(l, r):
    global a 
    i = l
    j = r
    x = a[(i+j)//2]
    while i <= j:
        while a[i] < x:
            i+=1
        while a[j] > x:
            j-=1
        if i <= j:
            a[i], a[j] = a[j], a[i]
            i+=1
            j-=1
    if i < r:
        qsort(i, r)
    if j > l:
        qsort(l, j)

qsort(0, len(a)-1)
print(a) # [1, 3, 5, 6, 7, 8]
{% endhighlight %}

Пример реализации на языке C++:

{% highlight cpp %}
#include <bits/stdc++.h>
using namespace std;

// Требуется 11 стандарт для такого способа задания вектора
vector<int> a = {6, 5, 3, 7, 8, 1, 9};

void qsort(int l, int r) {
    int i = l;
    int j = r;
    int x = a[(i + j)/ 2];
    while ( i <= j) {
        while (a[i] < x)
            i++;
        while (a[j] > x)
            j--;
        if (i <= j) {
            swap(a[i], a[j]);
            i++; 
            j--;
        }
    }
    if (i < r) 
        qsort(i, r);
    if (j > l) 
        qsort(l, j);

}

int main() {
    qsort(0, a.size()-1);
    for (auto &i : a)
        cout << i << " "; // 1 3 5 6 7 8 9 
}
{% endhighlight %}

