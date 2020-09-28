---
layout: post
date: 2020-09-27 19:20
title:  "Monotone Stack"
description: monotone stack in C++
comments: true
category: 
- docs
- help
tags:
- stack
- monotone
- C++
---



> What is monotonous increase stack?

The elements in the an monotonous increase stack keeps an increasing order.

> The typical paradigm for monotonous increase stack:
{% highlight ruby linenos %}
for(int i = 0; i < A.size(); i++){
  while(!in_stk.empty() && in_stk.top() > A[i]){
    in_stk.pop();
  }
  in_stk.push(A[i]);
}
{% endhighlight %}
<!--more-->

> What can monotonous increase stack do?

(1) find the previous less element of each element in a vector with O(n) time:

- What is the previous less element of an element?
For example:
[3, 7, 8, 4]
The previous less element of 7 is 3.
The previous less element of 8 is 7.
The previous less element of 4 is 3.
There is no previous less element for 3.

For simplicity of notation, we use abbreviation PLE to denote Previous Less Element.

- C++ code (by slitghly modifying the paradigm):
Instead of directly pushing the element itself, here for simplicity, we push the index.
We do some record when the index is pushed into the stack.

{% highlight ruby linenos %}
vector<int> previous_less(A.size(), -1);
for(int i = 0; i < A.size(); i++){
  while(!in_stk.empty() && A[in_stk.top()] > A[i]){
    in_stk.pop();
  }
  previous_less[i] = in_stk.empty()? -1: in_stk.top();
  in_stk.push(i);
}
{% endhighlight %}

(2) find the next less element of each element in a vector with O(n) time:

- What is the next less element of an element?
For example:
[3, 7, 8, 4]
The next less element of 8 is 4.
The next less element of 7 is 4.
There is no next less element for 3 and 4.

For simplicity of notation, we use abbreviation NLE to denote Next Less Element.

- C++ code (by slighly modifying the paradigm):
We do some record when the index is poped out from the stack.

{% highlight ruby linenos %}
// next_less[i] = j means A[j] is the next less element of A[i].
// next_less[i] = -1 means there is no next less element of A[i].
vector<int> previous_less(A.size(), -1);
for(int i = 0; i < A.size(); i++){
  while(!in_stk.empty() && A[in_stk.top()] > A[i]){
    auto x = in_stk.top(); in_stk.pop();
    next_less[x] = i;
  }
  in_stk.push(i);
}
{% endhighlight %}


### Where we use monotone stack in leetcode
- 1130. Minimum Cost Tree From Leaf Values
- 907. Sum of Subarray Minimums
- 901. Online Stock Span
- 856. Score of Parentheses
- 503. Next Greater Element II
- 496. Next Greater Element I
