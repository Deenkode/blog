---
title: "কিভাবে পোস্ট পাবলিশ করতে হয়?"
date: 2024-12-21
description: "দ্বীনকোড ব্লগে পোষ্ট পাবলিশ করার সহজ উপায়।"
author: "Sharafat Karim"
image: cover.png
tags:
    - guide
    - syntax
    - blog
categories:
    - syntax
    - tutorial
---

## ভুমিকা

আসসালামু আলাইকুম!

**দ্বীনকোড ব্লগে** আপনাকে স্বাগত' জানাচ্ছি। এই নিবন্ধতে আমাদের এই ব্লগে কিভাবে পোস্ট পাবলিশ করতে হয় সেই আলোচনা টি কিছুটা সহজ করে তুলে ধরার চেষ্টা করা হলো।
আর যারা এর আগেও `hugo` বা কোনো একটি *static site generator* প্ল্যাটফর্ম ব্যবহার করেছেন বা, গিটহাব নিয়ে বেশ ভালো ধারণা রাখেন, তারা ফাইল structure টি একটু
ভালো করে লক্ষ্য করলেই সহজে অনুসরণ করতে পারবেন কোনো গাইডলাইন অনুসরণ ছাড়া।

তাহলে শুরু করা যাক।

সবার বোধগম্যতার জন্য আমি বাংলায় যেসকল শব্দ ব্যবহার করেছি, তার মূল, পারিভাষিক ও সমার্থক শব্দ গুলো কয়েকটি নিচে দেয়া হলো,

| মূল শব্দ | পারিভাষিক বা, বিকল্প শব্দ |
| --- | --- |
| পোস্ট | নিবন্ধ |
| ডাইরেক্টরি | ফোল্ডার |
| অনুলিপি | কপি |
| ঐচ্ছিক | অপশনাল |

## যা যা প্রয়োজন

আপনার সিস্টেমে নিম্নলিখিত টুলগুলো ইন্সটল করা থাকতে হবে,

- git
- hugo (বাধ্যতামূলক নয়)
- পছন্দের যেকোনো একটা টেক্সট এডিটর

> এক্ষেত্রে `hugo` যদি ইন্সটল করা না থাকে, তাহলে আপনি সরাসরি আপনার পোস্ট ওয়েবসাইটে পাবলিশ করার পর দেখতে কেমন হবে সেটা ধরতে পারবেন না, পাবলিশ করা ব্যতীত। তবে শতভাগ কাজ করতে পারবেন কোনোরূপ সমস্যা ছাড়াই।

## পরিবেশ তৈরি

শূরুতেই, কাজের জন্য একটা পরিবেশ তৈরি করা যাক,

### ফোর্ক করা

আমাদের মূল গিটহাব রিপোজিটরি থেকে একটা ফোর্ক করতে হবে। আমাদের মূল গিটহাব রিপোজিটরি এখানে পাবেন,

- [দ্বীনকোড ব্লগ](https://github.com/Deenkode/blog)

এখান থেকে একটা ফোর্ক (fork) করে নিবো আমাদের নিজেদের অধীনে (***আপনার_নাম/deenkode-blog***)।

### ক্লোন করা

আমরা আমাদের ফোর্ক করা রিপোজিটরি থেকে একটা ক্লোন তৈরি করবো। এতে আমাদের পরিবেশে একটা অনুলিপি তৈরি হবে।
আমাদের রিপোজিটরিতে একটা সাব-মোডিউল আছে, তাই ক্লোনের সময় আমরা সাব-মোডিউলটি নিয়ে ক্লোন করবো,

```bash
git clone --recurse-submodules আপনার_নাম/deenkode-blog
```

## পর্যবেক্ষণ

এবার আমরা একটা নতুন ফোল্ডার পাবো, নিজেদের সিস্টেমে, যেখানে ক্লোন করেছি। যদি আমরা ফোল্ডারটি চালু করি, বেশ কিছু ফাইল ও ফোল্ডার দেখতে পাবো।

```
├── archetypes
├── assets
├── content
├── data
├── .git
├── .gitmodules (ফাইল)
├── .hugo_build.lock (ফাইল)
├── hugo.yaml (ফাইল)
├── i18n
├── layouts
├── public
├── resources
├── static
└── themes
```

> এখানে ফাইল বা ফোল্ডারের সংখ্যা আপনার সিস্টেমে কম বা বেশি হতে পারে। এতে চিন্তার কিছূ নেই।

এখন যদি আপনার সিস্টেমে `hugo` ইন্সটল করা থাকে, তাহলে আপনি এই পরিবেশে একটা লোকাল সার্ভার চালু করতে পারবেন।
ব্যাপারটি ঐচ্ছিক, চাইলে এড়িয়ে যেতেও পারেন।
একই ফোল্ডারে টার্মিনাল ওপেন করে নিচের কমান্ড টি দিলেই হবে,

```bash
hugo server serve -D
```

> আপনার terminal এর দিকে একটু লক্ষ করুন, যদি না কোনো এরর দেখা যায়।
> তাহলে আপনি আপনার ব্রাউজারে `http://localhost:1313` এ গিয়ে দেখতে পারবেন আপনার সাইট। <br>
> (টার্মিনালের আউটপুটেই দেখতে পারবেন উক্ত লিংক, ক্ষেত্রবিশেষে ভিন্ন হতে পারে)

### যদি কাজ না হয়?

প্রথমত নিশ্চিত করুন, আপনার `themes` ফোল্ডারে আপনার ব্যবহৃত থিমটি আছে কিনা। এটা খুবই গুরুত্বপূর্ণ। তাও কাজ না হলে, আমাদের কমিউনিটির সাথে যোগাযোগ করুন।

## আপনার নিজের একটা ফোল্ডার

### contents ফোল্ডার

চলুন এবার আমরা `content` ফোল্ডারে প্রবেশ করি। এখানে এরকম কিছূ একটা structure লক্ষ করবেন,

```
content
├── _index.md
├── page
│   ├── archives
│   │   └── index.md
│   ├── links
│   │   └── index.md
│   └── search
│       └── index.md
└── post
    ├── admin
    │   ├── markdown-syntax
    │   │   ├── cover.jpg
    │   │   └── index.md
    │   └── math-typesetting
    │       └── index.md
    └── sharafat
        └── how-to-post
            └── index.md
```

> এখান থেকে আমরা `post` ফোল্ডারে প্রবেশ করলাম। মূলত আমরা এই `post` এর ভেতরেই আমাদের কাজ করবো।

> এখানে উপরের স্টাকচারে আমরা admin, এবং কিছু user এর নামে কিছূ ফোল্ডার পাবো। মূলত সৌন্দর্য ও consistency অনুযায়ী সাজানোর উদ্যেশ্যে এবং একজনের সাথে যেনো আরেকজনের conflict
> না হয় তাই এভাবে সাজানো হয়েছে।

### নিজেকে যুক্ত করি

এখন আমরা নিজেকে যুক্ত করতে চাই এই সিস্টেমে। তাহলে আমরা মূলত এই `post` এর অধীনে নিজেদের নামে একটা ফোল্ডার তৈরি করে নিবো। তারপর আমাদের যা যা কাজ সব আমরা আমাদের নিজেদের
নামের ফোল্ডারে করবো, এতে করে আমাদের একজনের কাজের সাথে আরেকজনের কাজের কোনো conflict থাকবে না।

> এই কাজ কেবল একবারই করতে হবে আমাদের। চিন্তার কিছূ নেই।

যেমন, আমার নাম হলো `sharafat`, তাহলে আমি একটা ফোল্ডার তৈরি করবো `sharafat` নামে।

## নিজের প্রথম পোস্ট

পোষ্ট করার ক্ষেত্রে আমরা প্রতিটি নিবন্ধের জন্য আলাদা আলাদা করে ফোল্ডার তৈরি করবো।

উদাহারণস্বরূপ, আমি যদি একটা নতুন নিবন্ধ তৈরি করতে চাই, যেটার শিরোনাম হবে, My First Post, তাহলে `my-first-post` নামে একটা ফোল্ডার তৈরি করবো আমাদের নিজেদের নামের ফোল্ডারে। তার ভিতরে index.md ফাইলে আমরা মুলত নিবন্ধটি লিখবো।
তাহলে আমাদের ফাইলের structure হবে,

```markdown
content
├── _index.md
├── page
│   ├── archives
│   │   └── index.md
│   ├── links
│   │   └── index.md
│   └── search
│       └── index.md
└── post
    ├── admin
    │   ├── markdown-syntax
    │   │   ├── cover.jpg
    │   │   └── index.md
    │   └── math-typesetting
    │       └── index.md
    └── sharafat
        ├── how-to-post
        │   └── index.md
        └── my-first-post
            └── index.md
```

### ফাইলের ভেতর কি কি থাকবে?

#### হেডার বা মেটাডাটা

ফাইলের structure এমন হবে, যে, শূরুতে একটা হেডার থাকবে। এই হেডারে আমরা কিছু মেটাডাটা যুক্ত করবো। এই মেটাডাটা হলো আমাদের নিবন্ধের বিষয়ের কিছু মূল তথ্য।

```markdown
---
title: "আপনার টপিক"
author: "আপনার নাম"
date: 2023-09-07 (বর্তমান সময়, এরকম ফরম্যাটে)
image: cover.jpg (কভার পেজ যদি থাকে তাহলে একই ফোল্ডারে রেখে সেটার নাম)
description: কিছূটার বর্ণনা
tags:
    - tag 1
    - tag 2
    - tag 3
categories:
    - category 1
    - category 2
---
```

এখানে `tags` বা `category` চয়নের ক্ষেত্রে চাইলে আপনি আমাদের ব্লগের যেসব ট্যাগ ইতিমধ্যে ব্যবহুত হয়েছে সেসব ব্যবহার করলে সব পোস্ট একসাথে সর্ট করা যাবে।

> tag এবং categories এর মূল পার্থক্য হলো, category সাধারণত মূল বিষয়বস্তু এর মাধ্যমে শ্রেণীবিভাগ করে। অপরদিকে, tag সাধারণত একটি বিষয়বস্তু এর সাথে সম্পর্কিত কিছু বিষয় বা কাঠামো ব্যবহার করে যেমন, নির্দিষ্ট কিছু keyword যা মানুষ সার্চ ইঞ্জিনে সার্চ করার কাজে ব্যবহার করে।

> image এর ক্ষেত্রে আপনি আপনার পোস্টের জন্য একটা ছবি যুক্ত করতে পারবেন thumbnail হিসেবে। এটা একটা অপশনাল ব্যাপার। তাহলে সেই ছবিটি আপনাকে একই ফোল্ডারের অধীনে রাখতে হবে।

#### নিবন্ধের মুল অংশ

এখন আমরা আমাদের কাঙ্খিত নিবন্ধ লিখতে পারবো। নিবন্ধে আমরা সাজসজ্জার জন্য মার্কডাউন সিন্টেক্স ব্যবহার করতে পারবো। মার্কডাউন সিন্টেক্স হলো একটা সাধারণ টেক্সট ফরম্যাটিং ভাষা।
খুব সহজেই এটা নতুনরা আয়ত্ত করতে পারবে। এই সিনটেক্সের গাইডলাইন নিয়ে আমাদের কমিউনিটির আরো কিছু পোষ্ট আছে। চাইলে দেখে নিতে পারেন,

- [মার্কডাউন সিন্টেক্স গাইড - আমার ব্লগ থেকে](https://sharafat.pages.dev/markdown/)
- [মার্কডাউন সিন্টেক্স গাইড - মূল কোড রিপোতে পাবেন](https://Deencode.github.io/admin/markdown-syntax/)

> আপনি চাইলে অন্যদের দ্বারা লেখা নিবন্ধগুলোর সোর্স কোডও দেখতে পারবেন, এবং অনুপ্রেরণা নিতে পারবেন।

> এবার আপনি আপনার ফাইলটি সেভ করুন, এবং এইটুকুই! আপনার প্রথম পোস্ট তৈরি হয়ে গেছে, আপনাকে অভিনন্দন!

## পোস্ট পাবলিশ করা

### কমিট এবং পুশ

এবার বাকি কাজগুলো হলো আমাদেরকে আমাদের রিপোজিটরিতে একটি কমিট করে আপলোড করা। এটা খুবই সহজ।

```bash
git add .
git commit -m "আপনার মেসেজ"
git push origin main
```

### পুল রিকুয়েস্ট

এবার আমরা আমাদের রিপোজিটরিতে একটি পুল রিকুয়েস্ট করবো। পুল রিকোয়েস্ট টা হবে, আমাদের ফোর্ক করা রিপোজটিরে থেকে, দ্বীনকোড ব্লগের মূল রিপোজিটরিতে!

## সমাপ্তি

এতোক্ষণ ধরে ধৈর্যধারণ করে লেখাগুলো পড়ার জন্য আপনাকে ধণ্যবাদ। যেকোনো স্টেপ এ গিয়ে, কোনো সমস্যার সম্মুক্ষীণ হলে, আমাদের কমিউনিটির সাথে নিশ্চিন্তে যোগাযোগ করতে পারবেন।

> উপরোক্ত লেখাটি এখনো হয়তো অসম্পূর্ণ! আপনি চাইলেই অবদান রাখতে পারেন, এতে আমরা ঢের খুশি হবো।
