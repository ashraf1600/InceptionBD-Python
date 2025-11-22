# Python Dictionary - বাংলায় A থেকে Z পর্যন্ত সম্পূর্ণ গাইড

আমি Python Dictionary সম্পর্কে বাংলায় বিস্তারিত ব্যাখ্যা করছি:

## Dictionary কী?

Dictionary হলো Python এর একটি ডেটা স্ট্রাকচার যেখানে **key-value pair** আকারে ডেটা সংরক্ষণ করা হয়। এটি curly braces `{}` দিয়ে তৈরি করা হয়।

## মূল বৈশিষ্ট্য:

- **Unordered** (Python 3.7+ এ insertion order মেইনটেইন করে)
- **Mutable** (পরিবর্তনযোগ্য)
- **Key unique** হতে হবে
- **Value duplicate** হতে পারে

## Dictionary তৈরি করা:

```python
# খালি dictionary
empty_dict = {}
empty_dict2 = dict()

# ডেটা সহ dictionary
student = {
    "name": "রহিম",
    "age": 20,
    "city": "ঢাকা"
}

# dict() constructor দিয়ে
person = dict(name="করিম", age=25)
```

## ডেটা অ্যাক্সেস করা:

```python
student = {"name": "রহিম", "age": 20, "city": "ঢাকা"}

# Square bracket দিয়ে
print(student["name"])  # রহিম

# get() method দিয়ে (নিরাপদ)
print(student.get("age"))  # 20
print(student.get("phone", "পাওয়া যায়নি"))  # phone না থাকলে default value
```

## ডেটা যোগ/পরিবর্তন করা:

```python
student = {"name": "রহিম", "age": 20}

# নতুন key-value যোগ করা
student["city"] = "ঢাকা"

# বিদ্যমান value পরিবর্তন
student["age"] = 21

# update() দিয়ে একাধিক যোগ/পরিবর্তন
student.update({"phone": "01711111111", "email": "rahim@mail.com"})
```

## ডেটা মুছে ফেলা:

```python
student = {"name": "রহিম", "age": 20, "city": "ঢাকা"}

# নির্দিষ্ট key মুছে ফেলা
del student["city"]

# pop() দিয়ে মুছে value return পাওয়া
age = student.pop("age")

# popitem() - শেষ item মুছে ফেলা
last_item = student.popitem()

# clear() - সব ডেটা মুছে ফেলা
student.clear()
```

## গুরুত্বপূর্ণ Methods:

```python
student = {"name": "রহিম", "age": 20, "city": "ঢাকা"}

# keys() - সব keys পাওয়া
keys = student.keys()  # dict_keys(['name', 'age', 'city'])

# values() - সব values পাওয়া
values = student.values()  # dict_values(['রহিম', 20, 'ঢাকা'])

# items() - সব key-value pairs পাওয়া
items = student.items()  # dict_items([('name', 'রহিম'), ('age', 20), ('city', 'ঢাকা')])

# copy() - dictionary কপি করা
new_student = student.copy()

# fromkeys() - keys থেকে নতুন dictionary তৈরি
keys = ["a", "b", "c"]
new_dict = dict.fromkeys(keys, 0)  # {'a': 0, 'b': 0, 'c': 0}

# setdefault() - key থাকলে value return, না থাকলে set করে
student.setdefault("grade", "A")
```

## Dictionary Looping:

```python
student = {"name": "রহিম", "age": 20, "city": "ঢাকা"}

# শুধু keys loop
for key in student:
    print(key)

# keys() দিয়ে
for key in student.keys():
    print(key)

# values() দিয়ে
for value in student.values():
    print(value)

# items() দিয়ে key-value উভয়
for key, value in student.items():
    print(f"{key}: {value}")
```

## Nested Dictionary:

```python
school = {
    "class_10": {
        "student1": {"name": "রহিম", "roll": 1},
        "student2": {"name": "করিম", "roll": 2}
    },
    "class_9": {
        "student1": {"name": "সালমা", "roll": 1}
    }
}

# অ্যাক্সেস করা
print(school["class_10"]["student1"]["name"])  # রহিম
```

## Dictionary Comprehension:

```python
# সংখ্যা এবং তার বর্গ
squares = {x: x**2 for x in range(1, 6)}
# {1: 1, 2: 4, 3: 9, 4: 16, 5: 25}

# শর্ত সহ
even_squares = {x: x**2 for x in range(1, 11) if x % 2 == 0}
# {2: 4, 4: 16, 6: 36, 8: 64, 10: 100}
```

## Key Existence Check:

```python
student = {"name": "রহিম", "age": 20}

# in operator
if "name" in student:
    print("name আছে")

if "phone" not in student:
    print("phone নেই")
```

## Dictionary Merge:

```python
dict1 = {"a": 1, "b": 2}
dict2 = {"c": 3, "d": 4}

# Python 3.9+ এ | operator
merged = dict1 | dict2

# update() দিয়ে
dict1.update(dict2)

# ** unpacking দিয়ে
merged = {**dict1, **dict2}
```

## Sorting Dictionary:

```python
student = {"name": "রহিম", "age": 20, "city": "ঢাকা"}

# Key অনুযায়ী sort
sorted_by_key = dict(sorted(student.items()))

# Value অনুযায়ী sort
data = {"a": 3, "b": 1, "c": 2}
sorted_by_value = dict(sorted(data.items(), key=lambda item: item[1]))
```

## Common Use Cases:

```python
# 1. Counting occurrences
text = "hello world"
char_count = {}
for char in text:
    char_count[char] = char_count.get(char, 0) + 1

# 2. Grouping data
students = [
    {"name": "রহিম", "class": 10},
    {"name": "করিম", "class": 9},
    {"name": "সালমা", "class": 10}
]
grouped = {}
for student in students:
    cls = student["class"]
    if cls not in grouped:
        grouped[cls] = []
    grouped[cls].append(student)

# 3. Default values
config = {"debug": True}
mode = config.get("mode", "production")  # default value
```

## বিশেষ টিপস:

1. **Key হিসেবে immutable types** ব্যবহার করুন (string, number, tuple)
2. **List বা dictionary key হতে পারে না**
3. **get() method ব্যবহার করুন** KeyError এড়াতে
4. **Dictionary comprehension** কোড সংক্ষিপ্ত করতে
5. **defaultdict** বা **Counter** (collections module) জটিল কাজে
