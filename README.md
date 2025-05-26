# PostgreSQL

PostgreSQL একটি শক্তিশালী open-source রিলেশনাল ডাটাবেস ম্যানেজমেন্ট সিস্টেম (RDBMS)। PostgreSQL এর মাদ্ধমে ডাটা স্টোর, রিট্রিভ এবং ম্যানেজ এর মতো কাজ গুলো করা যায়। JSON, array এর মতো অ্যাডভান্সড ডাটা টাইপ গুলো এটি সাপোর্ট করে। উদাহরণ:

```sql
-- টেবিল তৈরী করা

CREATE TABLE employees (
    id SERIAL PRIMARY KEY,
    "name" TEXT NOT NULL,
    department TEXT,
    salary NUMERIC
);
```

# Primary Key and Foreign Key concepts in PostgreSQL

### Primary Key

Primary Key হলো এমন একটি column বা column এর সমষ্টি যা প্রতিটি row বা record কে unique ভাবে চিহ্নিত করে। এটি NULL হতে পারে না এবং duplicate value গ্রহণ করে না। উদাহরণ:

```sql
CREATE TABLE employees (
    id SERIAL PRIMARY KEY,
    "name" TEXT NOT NULL,
    department TEXT,
    salary NUMERIC
);
```

এখানে id হলো Primary Key, যা প্রতিটি employee কে unique ভাবে চিহ্নিত করবে।

### Foreign Key

Foreign Key হলো এমন একটি column যা অন্য একটি টেবিলের Primary Key এর সাথে সম্পর্ক (relationship) স্থাপন করে। এটি ডেটার integrity বজায় রাখে। উদাহরণ:

```
CREATE TABLE courses (
    course_id SERIAL PRIMARY KEY,
    course_name TEXT
);

CREATE TABLE enrollments (
    enrollment_id SERIAL PRIMARY KEY,
    course_id INT REFERENCES courses(course_id)
);
```

এখানে:
course_id একটি Foreign Key, যা courses টেবিলের course_id কে রেফার করে।

# Difference between VARCHAR and CHAR data types

VARCHAR এবং CHAR উভয়ই ডাটা store করার জন্য বেবহার করা হয়। CHAR বেবহার করা হয় যখন fixed length এর ডাটা store করা হয়। যদি নির্ধারিত length এর চেয়ে ছোট input দেওয়া হয় তাহলে এটি বাকি জায়গাটুকু space দিয়ে fill up করে দেয়। উদাহরণ:

```sql
CREATE TABLE example_char (
    code CHAR(5)
);
```

এখানে যদি 'AB' insert করা হয় তাহলে এটি 'AB ' store করবে। variable length এর ডাটা এর জন্য এটি slow.

VARCHAR variable length এর character store করে। উদাহরণ:

```sql
CREATE TABLE example_varchar (
    name VARCHAR(5)
);
```

এখানে যদি 'AB' insert করা হয় তাহলে exactly 'AB'-ই store করবে।

# The purpose of the WHERE clause in a SELECT statement

PostgreSQL এ কোনো একটা specific condition এ এক বা একাধিক record কে filter করার জন্য WHERE clause বেবহার করা হয়। উদাহরণ:

```sql
SELECT name, salary
FROM employees
WHERE department = 'HR';
```

এই query শুধু মাত্র 'HR' department এর row গুলোকেই return করবে।

# LIMIT and OFFSET clauses

### LIMIT

LIMIT ক্লজ ব্যবহার করে একটি নির্দিষ্ট সংখ্যক রেকর্ড রিটার্ন করা যায়। উদাহরণ:

```sql
SELECT * FROM employees
LIMIT 5;
```

এই কুয়েরি শুধুমাত্র প্রথম ৫টি রেকর্ড রিটার্ন করবে।

### OFFSET

OFFSET ক্লজ ব্যবহার করে কতটি রেকর্ড স্কিপ করা হবে তা নির্ধারণ করা যায়। এটি সাধারণত LIMIT এর সাথে ব্যবহার হয়। উদাহরণ:

```sql
SELECT * FROM employees
OFFSET 5 LIMIT 5;
```

এটি প্রথম ৫টি রেকর্ড স্কিপ করে, পরের ৫টি রেকর্ড রিটার্ন করবে (অর্থাৎ 6 থেকে 10 নম্বর পর্যন্ত)।
