code-as-documentation
=====================

Structuring code is hard. Lets spend some time figuring out a good way.


Python Community Guidelines
=====================
http://legacy.python.org/dev/peps/pep-0008/

http://legacy.python.org/dev/peps/pep-0257/

Examples
=====================
```python
# Build and return a list
def firstn(n):
    num, nums = 0, []
    while num < n:
        nums.append(num)
        num += 1
    return nums

sum_of_first_n = sum(firstn(1000000))
```

```python
# Using the generator pattern (an iterable)
class firstn(object):
    def __init__(self, n):
        self.n = n
        self.num, self.nums = 0, []

    def __iter__(self):
        return self

    # Python 3 compatibility
    def __next__(self):
        return self.next()

    def next(self):
        if self.num < self.n:
            cur, self.num = self.num, self.num+1
            return cur
        else:
            raise StopIteration()

sum_of_first_n = sum(firstn(1000000))
```

```python
# a generator that yields items instead of returning a list
def firstn(n):
    num = 0
    while num < n:
        yield num
        num += 1

sum_of_first_n = sum(firstn(1000000))
```

Tutorial
=====================
http://blog.miguelgrinberg.com/post/video-streaming-with-flask


Questions?
=====================
anthony@blar.do
