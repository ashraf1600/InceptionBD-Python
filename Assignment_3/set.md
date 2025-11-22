# Python এ Sets - সম্পূর্ণ গাইড (A to Z)

## Set কি?

Set হলো Python এর একটি **unordered** (ক্রমহীন) এবং **mutable** (পরিবর্তনশীল) collection যা **unique** (অনন্য) elements রাখে। এটি গাণিতিক Set theory এর উপর ভিত্তি করে তৈরি।

## Set তৈরি করা

```python
# Curly braces দিয়ে
my_set = {1, 2, 3, 4, 5}

# set() constructor দিয়ে
another_set = set([1, 2, 3, 4, 5])

# String থেকে set
char_set = set("hello")  # {'h', 'e', 'l', 'o'}

# খালি set (⚠️ {} দিলে dictionary হবে!)
empty_set = set()  # ✅ সঠিক
# empty_dict = {}  # এটি dictionary

# Mixed data types
mixed_set = {1, "hello", 3.14, True}

# ⚠️ Duplicate automatically remove হয়
numbers = {1, 2, 2, 3, 3, 3}
print(numbers)  # {1, 2, 3}
```

## Set এর বৈশিষ্ট্য

### ১. Unordered (ক্রমহীন)
```python
my_set = {3, 1, 4, 2}
print(my_set)  # Output random order এ আসতে পারে
# Indexing কাজ করে না!
# print(my_set[0])  # ❌ Error
```

### ২. Unique Elements (অনন্য উপাদান)
```python
fruits = {"আম", "কলা", "আম", "লিচু", "কলা"}
print(fruits)  # {'আম', 'কলা', 'লিচু'}
```

### ৩. Mutable (পরিবর্তনশীল)
```python
my_set = {1, 2, 3}
my_set.add(4)  # পরিবর্তন করা যায়
```

### ৪. শুধুমাত্র Immutable Elements রাখতে পারে
```python
# ✅ Valid
valid_set = {1, "hello", (1, 2), 3.14}

# ❌ Invalid (list, dict, set mutable)
# invalid_set = {1, [2, 3]}  # Error!
# invalid_set = {1, {2: 3}}  # Error!
```

## Set Methods

### ১. add() - একটি element যোগ করা
```python
fruits = {"আম", "কলা"}
fruits.add("লিচু")
print(fruits)  # {'আম', 'কলা', 'লিচু'}
```

### ২. update() - একাধিক elements যোগ করা
```python
fruits = {"আম", "কলা"}
fruits.update(["লিচু", "পেয়ারা"])
fruits.update({"জাম"}, ["আপেল"])
print(fruits)  # {'আম', 'কলা', 'লিচু', 'পেয়ারা', 'জাম', 'আপেল'}
```

### ৩. remove() - element মুছে ফেলা (না থাকলে Error)
```python
fruits = {"আম", "কলা", "লিচু"}
fruits.remove("কলা")
# fruits.remove("জাম")  # ❌ KeyError!
```

### ৪. discard() - element মুছে ফেলা (না থাকলেও Error নেই)
```python
fruits = {"আম", "কলা", "লিচু"}
fruits.discard("কলা")
fruits.discard("জাম")  # ✅ No Error
```

### ৫. pop() - Random element remove করে return করে
```python
fruits = {"আম", "কলা", "লিচু"}
removed = fruits.pop()
print(removed)  # Random একটি element
```

### ৬. clear() - সব elements মুছে ফেলা
```python
fruits = {"আম", "কলা", "লিচু"}
fruits.clear()
print(fruits)  # set()
```

### ৭. copy() - Set এর copy তৈরি
```python
fruits = {"আম", "কলা"}
fruits_copy = fruits.copy()
```

## Set Operations (গাণিতিক অপারেশন)

### ১. Union (মিলন) - সব elements একসাথে
```python
set1 = {1, 2, 3}
set2 = {3, 4, 5}

# Method 1: | operator
print(set1 | set2)  # {1, 2, 3, 4, 5}

# Method 2: union() method
print(set1.union(set2))  # {1, 2, 3, 4, 5}

# একাধিক sets
set3 = {5, 6, 7}
print(set1 | set2 | set3)  # {1, 2, 3, 4, 5, 6, 7}
```

### ২. Intersection (ছেদ) - Common elements
```python
set1 = {1, 2, 3, 4}
set2 = {3, 4, 5, 6}

# Method 1: & operator
print(set1 & set2)  # {3, 4}

# Method 2: intersection() method
print(set1.intersection(set2))  # {3, 4}

# একাধিক sets
set3 = {3, 7, 8}
print(set1 & set2 & set3)  # {3}
```

### ৩. Difference (পার্থক্য) - প্রথম set এ আছে কিন্তু দ্বিতীয়তে নেই
```python
set1 = {1, 2, 3, 4}
set2 = {3, 4, 5, 6}

# Method 1: - operator
print(set1 - set2)  # {1, 2}
print(set2 - set1)  # {5, 6}

# Method 2: difference() method
print(set1.difference(set2))  # {1, 2}
```

### ৪. Symmetric Difference (প্রতিসম পার্থক্য) - Common বাদে বাকি সব
```python
set1 = {1, 2, 3, 4}
set2 = {3, 4, 5, 6}

# Method 1: ^ operator
print(set1 ^ set2)  # {1, 2, 5, 6}

# Method 2: symmetric_difference() method
print(set1.symmetric_difference(set2))  # {1, 2, 5, 6}
```

## Update Operations (নিজের Set পরিবর্তন করা)

```python
set1 = {1, 2, 3}
set2 = {3, 4, 5}

# intersection_update() - নিজের set পরিবর্তন করে
set1.intersection_update(set2)
print(set1)  # {3}

# difference_update()
set1 = {1, 2, 3, 4}
set1.difference_update(set2)
print(set1)  # {1, 2}

# symmetric_difference_update()
set1 = {1, 2, 3}
set1.symmetric_difference_update(set2)
print(set1)  # {1, 2, 4, 5}
```

## Set Comparison (তুলনা)

### ১. Subset (উপসেট) - সব elements অন্য set এ আছে কিনা
```python
set1 = {1, 2}
set2 = {1, 2, 3, 4}

# Method 1: <= operator
print(set1 <= set2)  # True

# Method 2: issubset() method
print(set1.issubset(set2))  # True

# Proper subset (নিজের সমান নয়)
print(set1 < set2)  # True
```

### ২. Superset (অধিসেট) - সব elements ধারণ করে কিনা
```python
set1 = {1, 2, 3, 4}
set2 = {1, 2}

# Method 1: >= operator
print(set1 >= set2)  # True

# Method 2: issuperset() method
print(set1.issuperset(set2))  # True

# Proper superset
print(set1 > set2)  # True
```

### ৩. Disjoint (বিচ্ছিন্ন) - কোনো common element নেই
```python
set1 = {1, 2, 3}
set2 = {4, 5, 6}

print(set1.isdisjoint(set2))  # True

set3 = {3, 4, 5}
print(set1.isdisjoint(set3))  # False (3 common)
```

## Membership Testing

```python
fruits = {"আম", "কলা", "লিচু"}

print("আম" in fruits)      # True
print("জাম" in fruits)      # False
print("পেয়ারা" not in fruits)  # True
```

## Iteration (লুপ)

```python
fruits = {"আম", "কলা", "লিচু"}

# for loop
for fruit in fruits:
    print(fruit)

# List comprehension
squared = {x**2 for x in range(5)}
print(squared)  # {0, 1, 4, 9, 16}
```

## Set Comprehension

```python
# Basic
squares = {x**2 for x in range(6)}
print(squares)  # {0, 1, 4, 9, 16, 25}

# With condition
even_squares = {x**2 for x in range(10) if x % 2 == 0}
print(even_squares)  # {0, 4, 16, 36, 64}

# String থেকে unique vowels
text = "hello world"
vowels = {char for char in text if char in 'aeiou'}
print(vowels)  # {'e', 'o'}
```

## Built-in Functions

```python
my_set = {1, 2, 3, 4, 5}

len(my_set)      # 5 (দৈর্ঘ্য)
max(my_set)      # 5 (সর্বোচ্চ)
min(my_set)      # 1 (সর্বনিম্ন)
sum(my_set)      # 15 (যোগফল)
sorted(my_set)   # [1, 2, 3, 4, 5] (list return করে)

# any() এবং all()
print(any(my_set))   # True (যদি কোনো element True হয়)
print(all(my_set))   # True (যদি সব elements True হয়)
```

## Frozen Set (অপরিবর্তনীয় Set)

```python
# Immutable set
frozen = frozenset([1, 2, 3, 4])

# ✅ Read operations কাজ করবে
print(len(frozen))
print(2 in frozen)

# ❌ Modification operations কাজ করবে না
# frozen.add(5)     # Error!
# frozen.remove(1)  # Error!

# Dictionary এর key হিসেবে ব্যবহার করা যায়
my_dict = {frozen: "value"}  # ✅ কাজ করবে

# Set এর ভিতরে রাখা যায়
set_of_sets = {frozenset([1, 2]), frozenset([3, 4])}
```

## বাস্তব জীবনের উদাহরণ

### ১. Duplicate Remove করা
```python
numbers = [1, 2, 2, 3, 4, 4, 5]
unique_numbers = list(set(numbers))
print(unique_numbers)  # [1, 2, 3, 4, 5]
```

### ২. Common Elements খুঁজে বের করা
```python
class_a = {"রহিম", "করিম", "জামিল", "সালমা"}
class_b = {"করিম", "সালমা", "রুমানা", "তানিয়া"}

both_classes = class_a & class_b
print(both_classes)  # {'করিম', 'সালমা'}
```

### ৩. Unique Words Count
```python
text = "hello world hello python world"
words = text.split()
unique_words = set(words)
print(f"Total words: {len(words)}")  # 5
print(f"Unique words: {len(unique_words)}")  # 3
```

### ৪. Email Validation (Unique Emails)
```python
emails = ["test@gmail.com", "hello@yahoo.com", "test@gmail.com"]
unique_emails = set(emails)
print(len(unique_emails))  # 2
```

### ৫. Permission System
```python
admin_permissions = {"read", "write", "delete", "execute"}
user_permissions = {"read", "write"}

# User এর additional permissions দরকার
missing = admin_permissions - user_permissions
print(missing)  # {'delete', 'execute'}

# User কি admin?
is_admin = user_permissions >= admin_permissions
print(is_admin)  # False
```

## Set vs List vs Tuple vs Dictionary

| Feature | List | Tuple | Set | Dictionary |
|---------|------|-------|-----|------------|
| Ordered | ✅ | ✅ | ❌ | ❌ (Python 3.7+ এ ordered) |
| Mutable | ✅ | ❌ | ✅ | ✅ |
| Duplicates | ✅ | ✅ | ❌ | ❌ (keys) |
| Indexed | ✅ | ✅ | ❌ | ✅ (by key) |
| Syntax | `[]` | `()` | `{}` | `{k:v}` |
| Use Case | General | Fixed data | Unique items | Key-value |

## Performance Comparison

```python
import time

# List এ membership test
my_list = list(range(10000))
start = time.time()
9999 in my_list
print(f"List: {time.time() - start}")  # Slow (O(n))

# Set এ membership test
my_set = set(range(10000))
start = time.time()
9999 in my_set
print(f"Set: {time.time() - start}")  # Fast (O(1))
```

## Set এর সুবিধা

1. **দ্রুত Membership Testing**: O(1) complexity
2. **Automatic Duplicate Removal**: নিজে থেকে unique রাখে
3. **Mathematical Operations**: Union, intersection সহজেই করা যায়
4. **Memory Efficient**: Hash table ব্যবহার করে

## Set এর অসুবিধা

1. **Unordered**: কোনো ক্রম নেই 
2. **No Indexing**: Index দিয়ে access করা যায় না
3. **Limited Element Types**: শুধু immutable elements রাখা যায়
4. **No Duplicate Values**: Duplicate দরকার হলে ব্যবহার করা যায় না

## Important Tips

```python
# ⚠️ খালি set তৈরি
empty = set()  # ✅ সঠিক
# empty = {}   # ❌ এটি dictionary

# একটি মাত্র element
single = {5}  # ✅ Set
single = {5,} # ✅ এটাও set

# Set থেকে List
my_list = list(my_set)

# List থেকে Set
my_set = set(my_list)

# Set operations এ type mixing
set1 = {1, 2, 3}
# result = set1 | [4, 5]  # ❌ Error!
result = set1 | {4, 5}    # ✅ সঠিক
```
