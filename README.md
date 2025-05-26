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
