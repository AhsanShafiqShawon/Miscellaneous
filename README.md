### Version Control

আমরা প্রতিনিয়ত যে কোড লিখি সেগুলোতে ভুল হয়, তাই আগের কোডে ফেরত যাওয়ার প্রয়োজন পড়ে। আবার অন্যের লেখা কোডের সাথে নিজের কোডের তুলনা করা লাগতে পারে। এই কাজগুলোকে Version Control বলে।

এই কাজগুলো আমরা ম্যানুয়ালি করতে গেলে অনেক সমস্যার মধ্যে পড়তাম। Version Control Software আমাদের এই কাজ সহজ করে দিয়েছে। দুই ধরনের Version Control Software রয়েছে। যথাঃ

১। One Step Version Control: এই সফটওয়্যারগুলো ক্লায়েন্ট (নিজের কম্পিউটার) থেকে সরাসরি সার্ভারে (অন্য কোন কম্পিউটার বা ডাটা সেন্টার) কোড পাঠিয়ে (Commit) দেয়। এ ধরনের সফটওয়্যারের সমস্যা হচ্ছে যে, কোন কারনে ইন্টারনেট না থাকলে মুশকিল হয়ে যায়। পুরনো দিনে এসব সফটওয়্যার ব্যবহার করা হত। উদাহরণ: SVN, CVS।

২। Two Step Version Control: অপরদিকে এই সফটওয়্যারগুলো কোডগুলোকে নিজের কাছেই জমা রাখে অর্থাৎ Commit করলে সেই কম্পিউটারেই থাকে। এরপর Sync (Pull/Push) করার মাধ্যমে সার্ভারে পাঠানো হয়। উদাহরণ: Git, Mercurial। Github হচ্ছে Git এর হোস্টিং।

### খুচরো জ্ঞান

Tortoisegit হচ্ছে একটা ক্লায়েন্ট এবং এর সার্ভার হচ্ছে Git। Repository এর মধ্যে মূলত Code এর Version History থাকে। Git এর অ্যাকাউন্টে লগ ইনে সমস্যা হলে Credential Manager এ গিয়ে মুছে দিয়ে আবার লগ ইন করতে হবে। নিজের কম্পিউটারে Repository ক্লোন করা হলে সেখানে .git নামে একটা ফোল্ডার তৈরি হয়, এটা খুব গুরুত্বপূর্ণ ফোল্ডার। এটা কোনভাবেও যেন মডিফাই না হয়।

http এবং https এর মধ্যে পার্থক্য হচ্ছে যে, ডাটা এনক্রিপশনের মাধ্যমে https তুলনামূলক বেশি নিরাপত্তা প্রদান করে।

পাবলিক কি এর এক্সটেনশন হচ্ছে .pem এবং প্রাইভেট কি এর এক্সটেনশন .ppk। SSH key অ্যাকাউন্ট স্পেসিফিক, প্রজেক্ট স্পেসিফিক না। SSH হচ্ছে https এর তুলনায় গতিশীল এবং বিশ্বস্ত।

MVC, API, Worker Service প্রতিটিই হচ্ছে startable project।

IIS, Apache, Nginx হচ্ছে Web Server।

### কনফ্লিক্ট কিভাবে দেখায়?

```
<<<<< Name of first file
Message from first file
========
Message from second file
>>>>> Name of second file
```

### Version Controlling

Master branch থেকে Develop branch বানানো হয়। Develop branch থেকে বিভিন্ন Feature branch বানানো হয়। Master branch কে ধরা হয় প্রোডাক্টের রিলিজ ভার্সনের মতো। Feature branch এ অসম্পূর্ণ কাজ কমিট দিয়ে বাড়ি চলে যাওয়া যায়, তবে Develop branch মোটামুটি স্ট্যাবল। তাই Feature branch ব্রোকেন অবস্থায় থাকতে পারে। Release branch টি প্রোডাক্ট ম্যানেজারের জন্য জরুরি। Develop branch থেকে Release branch বানানো হয়। যেহেতু Develop branch এ প্রতিনিয়ত কমিট আসতেই থাকে Feature branch থেকে তাই Develop branch থেকে প্রোডাক্টের ভার্সন রিলিজ মুশকিল। একারণে Release branch এর দরকার। প্রোডাক্টের পরবর্তী আপডেটে যদি ১০টা ফিচার রিলিজ করা হয় এবং এর মধ্যেই যদি Develop branch এ আরও নতুন নতুন ফিচার নিয়ে কাজ শুরু হয়ে যায় তাহলে ঝামেলা বেধে যাবে। এই কারণে Develop branch এর কোন একটি নির্দিষ্ট স্থান থেকে Release branch বানিয়ে নেয়া হয়।

Release branch এ যদি কোন বাগ ধরা পড়ে তাহলে সেটা ফিক্স করে আবার Develop branch এ কমিট করে দেয়া হয়। Release branch এ সবকিছু ঠিকঠাক থাকলে সেখান থেকে Master branch এ কমিট দিয়ে দেয়া হয়। এ থেকে প্রোডাক্টের একটা নতুন ভার্সন তৈরি হয়ে যায়। এখন দেখা গেল যে, প্রোডাক্টের নতুন ভার্সন ব্যবহার করতে গিয়ে ব্যবহারকারীর চোখে কোন বাগ ধরা পড়লো, তখন সেই ভার্সনটা Hotfix branch এ দিয়ে দেয়া হয় এবং সেটা সেখানে ফিক্স করে দিয়ে পুনরায় Master branch এবং Develop branch এ দেয়া হয়।

### বিভিন্ন ধরনের আপডেট

```
v1.0	মেজর আপডেট
v1.2	ফিচার (মাইনর) আপডেট
v1.2.1	বাগ ফিক্সিং (প্যাচ বা বিল্ড)
```

### Language Integrated Query (LINQ)

যেকান প্রকারের ইন মেমরি কালেকশনের উপর (অ্যারে, লিস্ট ইত্যাদি) LINQ ব্যবহার করা হয়। LINQ ব্যবহারের জন্য IQueryable যুক্ত করতে হয়। ভিন্ন ধরনের কালেকশনের মধ্যেও LINQ ব্যবহার করা যায়। IEnumerable ব্যবহার করা হয় কোন লিস্টে ইটারেট করার জন্য, এটা ব্যবহার করে কোয়েরি করা যায় না।

```
from object in dataSource
where condition
select object
```

এখানে মাঝের লাইনটায় বিভিন্ন অপারেশনের সিনট্যাক্স বসতে পারে, যেমন জয়েন, কোয়েরি ইত্যাদি।

### Delegates and Events

আমরা সাধারণত প্রোগ্রামিং ল্যাঙ্গুয়েজে ভ্যারিয়েবল ব্যবহার করি ডাটা ধরে স্টোর করার জন্য। অনেক সময় ভ্যারিয়েবলে লজিক বা মেথড স্টোর করারও দরকার পড়ে। এজন্য আমরা Delegates ব্যবহার করে থাকি। Delegates ডিক্লেয়ার করার জন্য মেথডের সিগনেচার লিখতে হয়। Delegates এর নতুন ফর্ম হচ্ছে Function-Action। এক্ষেত্রে মেথডের সিগনেচার লিখার দরকার পড়েনা। ভয়েড মেথডের ক্ষেত্রে Action লিখা লাগে এবং অ্যাঙ্গেল ব্র্যাকেটের মধ্যে প্যারামিটারের ডাটা টাইপ লিখতে হয়। অন্যদিকে যে মেথডের রিটার্ন টাইপ আছে সেক্ষেত্রে Func লিখতে হয় এবং অ্যাঙ্গেল ব্র্যাকেটের মধ্যে প্যারামিটারের ডাটা টাইপ লিখতে হয় সাথে সবশেষে রিটার্ন টাইপ লিখতে হয়।

```
Events enable a class or object to notify other classes or objects when something of interest occurs.
The class that sends (or raises) the event is called the publisher and the classes that receive (or handle) the event are called subscribers.
```

### Colletions

Generic ও Non Generic টাইপের বেশ কিছু Collection আছে। যেমন: Generic এর মধ্যে রয়েছে List, Dictionary, HashSet, Stack, Queue, SortedList, SortedDictionary, SortedSet ইত্যাদি। আর Non Generic এর মধ্যে রয়েছে ArrayList, Stack, Queue, HashTable, SortedList, NameValueCollection ইত্যাদি। Generic ও Non Generic এর মধ্যে পার্থক্য হচ্ছে যে, Generic এ আমরা ডাটা টাইপ হিসেবে তথ্য রাখতে পারি কিন্তু Non Generic এ অবজেক্ট হিসেবে তথ্য রাখতে হয়।

Non Generic টাইপের Collection এর উপর দিয়ে iterate করার জন্য আমরা IEnumerable Interface ব্যবহার করে থাকি। আবার Non Generic টাইপের Collection এর সাইজ, enumerators ও synchronization methods ডিফাইন করার জন্য ICollection Interface ব্যবহার করা হয়।

An enumerator is an automaton that lists, possibly with repetitions, elements of some set S, which it is said to enumerate. So now what is automaton? An automaton is a relatively self-operating machine.

### Difference between IEnumerable and IEnumerator.

An IEnumerator is a thing that can enumerate: it has the Current property and the MoveNext and Reset methods (which in .NET code you probably won't call explicitly, though you could). An IEnumerable is a thing that can be enumerated...which simply means that it has a GetEnumerator method that returns an IEnumerator.

### Introduction to ASP.net MVC

Controller ক্লাসটা ASP.net ফ্রেমওয়ার্কের একটা ক্লাস। MVC একটা ডিজাইন প্যাটার্ন বা আর্কিটেকচার, আবার এটাকে ফ্রেমওয়ার্কও বলা হয়ে থাকে। Controller নেভিগেশনের সাথে জড়িত। কোন মডেল বা কোন ভিউ ব্যবহৃত হবে সেই নির্দেশনাও দেয় Controller। Controller কে কল করে রাউটার। Router হচ্ছে ফ্রেমওয়ার্কের প্রাইমারি ইলিমেন্ট। cshtml এক্সটেনশনের ফাইলকে রেজর ভিউ বলা হয়। এই ফাইলে C# ও html উভয় কোড লিখা যায়। C# এর কোড লিখতে হলে @ চিহ্ন দিয়ে শুরু করতে হয়।

Controller এর মেথডের যখন একাধিক রিটার্ন টাইপ থাকার সুযোগ থাকে তখন আমরা IActionResult ব্যবহার করি। এর মধ্যে কিছু রিটার্ন টাইপ হচ্ছে BadRequestResult (400), NotFoundResult (404), and OkObjectResult (200)। Views ফোল্ডারের Shared এ থাকা ফাইলগুলো সব জায়গা থেকে ব্যবহার করা যায়। Controller এর কোন মেথড যখন ভিউ রিটার্ন করে তখন সে Controller এর সেই (উক্ত মেথডের জন্য নির্দিষ্ট) ফোল্ডারের মধ্যে খোঁজে, সেখানে না পেলে Shared এর মধ্যে খোঁজে।

Shared এর মধ্যে Layout নামে একটা রেজর ভিউ থাকে, যেটা ওয়েবসাইটের কমন কোডগুলো ধারণ করে। আরেকটি বিষয় Shared এর ফাইলগুলোর (Partial) নাম লিখার একটা কনভেনশন আছে, সেটা হচ্ছে নামের আগে আন্ডারস্কোর দেয়া। মাল্টিপল Controller এ ব্যবহারের জন্য এই ফাইলগুলো Shared এর মধ্যে রাখা হয়। Layout এর মধ্যে RenderBody নামে একটা অংশ থাকে, সেখানে Page Specific কোড এসে বসে যায়। আবার RenderSection নামে আরেকটা অংশ থাকে, সেখানে Page Specific স্ক্রিপ্ট এসে বসে। কিছু reusable কোড যেটা আমরা বিভিন্ন জায়গায় ব্যবহার করতে চাই, আবার সেটা পেইজের অংশও না (যেমন- হেডার, ফুটার ইত্যাদি) সেগুলোকে Partial হিসেবে লিখে রাখা হয়।

Model একটা সাধারণ ক্লাস বা POCO ক্লাস। Controller এর মাধ্যমে View এ ডাটা পাস করার জন্য এবং View Controller এর মাধ্যমে ডাটা রিসিভ করার জন্য মূলত Model ক্লাস বানানো হয়। একটা View এ একটা Model ক্লাস ব্যবহার করা যাবে।

A plain old CLR object, or plain old class object (POCO) is a simple object created in the .NET Common Language Runtime (CLR) that is unencumbered by inheritance or attributes.

Attribute নামে আরেকটা ফিচার আছে, যেটা কোন মেথড কিভাবে এক্সিকিউট হবে সেটা নির্ধারণ করে দেয়। এগুলো মেথডের এক্সিকিউশনের আগেই কাজ করে এবং মেথডের উপর থার্ড ব্র্যাকেটের মধ্যে লিখে দিতে হয়।

এক টাইপের অ্যাকশনগুলোকে একত্রে করে আমরা একটা Controller এর মধ্যে নিয়ে আসি এবং এক টাইপের Controller কে একত্রে একটা Area এর মধ্যে নিয়ে আসি। Program.cs এ MapControllerRoute অংশে Area এর ম্যাপিং টা সব উপরে রাখতে হয়। ViewStart হচ্ছে এমন একটা রেজর ভিউ যেটা সব পেজের ডিফল্ট Layout হিসেবে কাজ করে।

### What is Tag and HTML Heplers?

Tag Helpers enable server-side code to participate in creating and rendering HTML elements in Razor files.

An HTML Helper is just a method that returns a HTML string. যেহেতু এটা একটা C# মেথড তাই রেজর ফাইলে লিখার সময় @ দিয়ে শুরু করতে হয়।

### Dependancy Injection

আমরা যখন একটা মেথডের মধ্যে আরেকটা মেথডকে কল করি, আবার তার মধ্যে আরেকটা মেথডকে কল করি তখন মেথডগুলোর মধ্যে strong dependancy তৈরি হয়ে যায়। এটা অবশ্যই ভালো ব্যাপার না। সবসময়ই চেষ্টা করতে হবে loosely coupled কোড লিখতে। এই বিষয়টা যে নীতি অনুসরণ করে বাস্তবায়ন করা হয় তাকে বলা হয় Dependancy Inversion Principle। আর এই নীতি অনুসরণের মাধ্যমে যে কাজটা করা হচ্ছে তাকে বলা হয় Dependancy Injection।

আমরা মূলত Interface তৈরির মাধ্যমে কাজটা করে থাকি। সরাসরি Class A এর মধ্যে Class B কে কল না করে, আমরা একটা Interface বানাই। এরপর সেই Interface যেসকল ক্লাস ইমপ্লিমেন্ট করে তাদেরকে প্রয়োজন অনুসারে Class A এর মধ্য ব্যবহার করি। এতে ক্লাস দুইটার মধ্যে সরাসরি কোন Dependancy থাকেনা। মাইক্রোসফট IoC Container (Inversion of Control) দিয়ে কাজটা করে।

IoC Container (a.k.a. DI Container) is a framework for implementing automatic dependency injection.

Model ক্লাসে আমরা Dependancy Injection করিনা কারণ এই ক্লাসের মাধ্যমে আমরা বিভিন্ন রকম ডাটা নিয়ে থাকি এবং এই ডাটা পরিবর্তন হতে থাকে বা পারে। একটা ক্লাস কাজ করতে গিয়ে যখন অন্য কোন ক্লাসের উপর নির্ভর করে শুধু তখনই Dependancy Injection করা হয়।

WebModule ক্লাসটা আমরা ব্যবহার করি Interface এর সাথে তার সংশ্লিষ্ট ক্লাসকে বাইন্ড করার জন্য। যাদেরকে বাইন্ড করা হয় তারা Dependancy Injection এর জন্য available হয়ে যায়।

### Logger

Serilog এ আমরা যে বিভিন্ন মিডিয়ামে লগ রাইট করি তাদেরকে Sink বলে। লগের বিভিন্ন লেভেল আছে যেমন, Fatal, Error, Debug, Information, Warning ইত্যাদি। Serilog মাইক্রোসফটের IoC এর সাথে মার্জ হয়ে গিয়ে একসাথে কাজ করে।

Program.cs এ builder দিয়ে app বানানোর পর বেশকিছু কনফিগারেশন করা লাগে, যেসব মেথড দিয়ে এইসব কনফিগারেশন করা হয় তাদেরকে middleware বলে।

### Functional Programming

Functional programming is a programming paradigm in which we try to bind everything in pure mathematical functions style. It is a declarative type of programming style. Its main focus is on “what to solve” in contrast to an imperative style where the main focus is “how to solve”. It uses expressions instead of statements. An expression is evaluated to produce a value whereas a statement is executed to assign variables.

### SQL Server

SQL Server হচ্ছে মূল সফটওয়্যার যেটা দিয়ে সার্ভারের কাজগুলো করা হয় এবং SQL Server Management Studio হচ্ছে সার্ভারের UI। এটা না থাকলে আমাদের কমান্ড লাইন দিয়ে কাজ করতে হতো। সার্ভার বলতে কখনো কখনো মেশিনকে বোঝানো হয় আবার কখনো সফটওয়্যারকেও বোঝানো হয়।

সার্ভারে কানেক্ট করতে গেলে কয়েক ধরনের Authentication দেখা যায়। এর মধ্যে Windows Authentication ব্যবহার করলে একই মেশিন বা নেটওয়ার্কের মধ্যে থাকলে Access পাবে। আর SQL Server Authentication ব্যবহার করলে যেকোন জায়গা থেকে Access পাবে। ডাটাবেজের টেবিলে একটা Primary Key রাখা গুড প্র্যাকটিস। ডাটাবেজ ব্যাকআপ নেয়ার সময় ফাইলের এক্সটেনশন হিসেবে .bak লিখতে হয়।

C# এ আমরা একটা মেথডের মধ্যে আরেকটা মেথডকে কল করে জটিল কাজ করতে পারি। ঠিক একইরকম সুবিধা পেতে ডাটাবেজে আমরা Stored Procedure ব্যবহার করে থাকি। ফাংশন বা মেথড ও Stored Procedure এর মধ্যে বেশকিছু পার্থক্য আছে যদিও কাজের দিক থেকে এদেরকে একইরকম মনে হতে পারে। এদের মধ্যে পার্থক্যগুলো নিম্নরূপ:
১। Functions can have only input parameters for it whereas Procedures can have input or output parameters.
২। Functions can be called from Procedure whereas Procedures cannot be called from a Function.
৩। The function must return a value but in Stored Procedure it is optional. Even a procedure can return zero or n values.

Stored Procedure এ (বা ডাটাবেজে অন্য কোন স্থানে) কোন কমেন্ট (Single Line) লিখতে চাইলে দুইটা হাইফেন (--) দিয়ে শুরু করতে হয়। মাল্টি লাইন কমেন্টের জন্য /*..*/ ব্যবহার করা হয়। কোন ভ্যারিয়েবল ডিক্লেয়ার করার জন্য @variableName datatype এভাবে লিখতে হয়। এর অর্থ হচ্ছে datatype পরে লিখতে হয়।

```
declare @count int;
Set @count = 0;
```

sql এ string লিখতে হয় single quotation দিয়ে। Dynamic SQL is a programming technique that enables you to build SQL statements dynamically at runtime. You can create more general purpose, flexible applications by using dynamic SQL because the full text of a SQL statement may be unknown at compilation। string জোড়া দেয়ার মাধ্যমে sql injection এর রিস্ক তৈরি হয়ে থাকে। এটা থেকে বাঁচার জন্য আমাদের খুব সতর্কভাবে dynamic SQL লিখতে হবে।

কোন ওয়েবসাইটে যেকোন লিস্ট (যেমন: কোন কনটেস্টের ranklist) দেখতে গিয়ে আমরা দেখি প্রতি পেইজে হয়তো ৫০ টা করে তথ্য দেখায়। আবার Next এ চাপ দিল পরের ৫০ টা দেখায়। Paging এর কনসেপ্টটা হচ্ছে যে, যখন আমরা যে পেইজে থাকবো তখন শুধু ওই পেইজের ডাটাগুলো তুলে নিয়ে আসবে সার্ভার থেকে।

### Bootstrap

Bootstrap is a free and open-source CSS framework directed at responsive, mobile-first front-end web development.

Bootstrap যেকোন পেজকে ১২টা অংশে বা কলামে ভাগ করে।

### Web Service ‍& Web API (Application Programming Interface)

মেশিনের সাথে মেশিনের যোগাযোগ স্থাপনের জন্য Web API ব্যবহার করা হয়। সফটওয়্যারের সাথে সফটওয়্যারের যোগাযোগ যেন ডেটার মাধ্যমে হয় সেজন্য Web Service ব্যবহার করা হয়। কিছু কিছু Web API কে Web Service বলা হয়। তাহলে প্রশ্ন হচ্ছে যে, Web API কখন Web Service হয়? মাইক্রোসফট তাদের ডটনেট ফ্রেমওয়ার্কের মধ্যে Web Service কে Web API নামে ব্র্যান্ডিং করছে।

Web services are XML-based information exchange systems that use the Internet for direct application-to-application interaction.

বেশিরভাগ Web Service আমাদের API দেয় কিছু ফাংশন এবং কমান্ডের সমন্বয়ে। এগুলো ব্যবহার করে আমরা আমাদের প্রয়োজনীয় তথ্য তুলে নিয়ে আসতে পারি। আরেকটি কথা মাথায় রাখতে হবে যে, সব Web Service ই API হতে পারে, কিন্তু সব API আবার Web Service হতে পারে না।

প্রধানত একটা নির্দিষ্ট Naming Convention মেনে API বানালে সেটাকে RESTful API বলা হয়। API এবং MVC এর মধ্যে গঠনগত তেমন কোন পার্থক্য নেই, শুধু API এর কোন View থাকেনা। মাইক্রোসফটের API বাই ডিফল্ট REST এর নিয়ম মেনে বানানো।

### অবজেক্ট ওরিয়েন্টেড ডিজাইন মূলনীতি

১। Single Responsibility Principle (SRP): একটা ক্লাসের একটাই কাজ থাকবে। আমরা যেন একটা ক্লাসের মধ্যেই প্রিন্ট করার কাজ, আবার মেইল পাঠানোর কাজ ইত্যাদি না করে বসি। আলাদা আলাদা কাজের জন্য আলাদা আলাদা ক্লাস থাকবে।

২। Open-Closed Principle (OCP): কোন কোড লেখা হয়ে গেলে যেন সেটা কেউ পরিবর্তন না করে। কিন্তু পরিবর্তনের প্রয়োজন হলে যেন সেটা করার একটা পথ থাকে। মূল ক্লাস অপরিবর্তিত থাকবে কিন্তু বাইরে থেকে Inheritance বা Composition এর মাধ্যমে প্রয়োজনীয় পরিবর্তন আনতে হবে। “A class should be closed for modification and open for extension”.

৩। Liskov Substitution Principle (LSP): যদি একটি ক্লাস থেকে অন্য একটি ক্লাসকে Inherit করা হয় তাহলে এমন হতে হবে যে, Parent Class ও সকল Child Class একইভাবে ব্যবহার করা যাবে। Parent Class ও সকল Child Class ব্যবহারের ক্ষেত্রে কোন বিশেষ নিয়ম পালনের বা চিন্তা করার প্রয়োজন পড়বে না। “Is a” Relation দিয়ে আমরা অনেক সময় এটা চেক করতে পারি তবে মনে রাখতে হবে, বাস্তব দুনিয়াতে “Is a” Relation যেভাবে কাজ করবে অবজেক্ট ওরিয়েন্টেড প্রোগ্রামিং এর দুনিয়াতে সেটা একইভাবে কাজ করবে এটা ভাবা ভুল হবে। কাজেই কোডে ব্যবহার করার সময় আমরা কোন কিছু মাথায় রেখে কোড করছি নাকি একইভাবে কোন চিন্তা ভাবনা ছাড়াই Parent Class ও সকল Child Class কে ব্যবহার করতে পারছি এটার দিকে বিশেষ নজর রাখতে হবে।

৪। Interface Segregation Principle (ISP): বড় Interface এর পরিবর্তে ছোট ছোট Interface তৈরি করতে হবে। Interface যেন আমাদের ক্লাসে নতুন বৈশিষ্ট্য যোগ করার কাজে ব্যবহার করা যায়। Interface একাধিক ক্লাসে ব্যবহার করা সম্ভব হয়। “No client should be forced to depend on methods it does not use”.

৫। Dependency Inversion Principle (DIP): কোডের মধ্যে Dependency দূর করার জন্য এটি ব্যবহার করা হয়। এমনভাবে আমরা দুইটি মডিউলকে ডিজাইন করবো যেন কেউ কারো উপর সরাসরি নির্ভর না করে বরং Interface এর উপর নির্ভর করে। “High-level modules should not depend on low-level modules. Both should depend on abstractions”. “Abstractions should not depend on details. Details should depend on abstractions.”

৬। Don’t Repeat Yourself (DRY): কখনও একই কোড বারবার ব্যবহার করা যাবেনা।

৭। Encapsulate what changes: hides implementation detail, helps in maintenance.

৮। Favor Composition over Inheritance: Code reuse without cost of inflexibility. আমরা যখন একটা ক্লাসকে অন্য কোন ক্লাসের মধ্যে ব্যবহার করি সেই বিষয়টাকে composition বলে। যেমন:

```
public class Car
{
	public double Speed { get; set; }
	public Engine Engine { get; set; } // Engine another class
}
```
৯। Programming for Interface: Helps in maintenance, improves flexibility.

১০। Delegation Principle: Don’t do all things by yourself, delegate it.

### What is JWT (JSON Web Token)?

JWT সাধারণত Authorization এর কাজে ব্যবহার করা হয়। আমরা যখন কোন ওয়েবসাইটে ইউজার নেম ও পাসওয়ার্ড দিয়ে লগ ইন করি, তখন Authentication এর মাধ্যমে সেই ইউজারকে ওয়েবসাইটে লগ ইন করতে দেয়া হয়। এই রিকোয়েস্ট টা সার্ভারে যায় এবং সেখান থেকে একটা সেশন আইডি কুকি হিসেবে সেই ইউজারকে দেয়া হয়। সেই ইউজার যখন ওই ওয়েবসাইটের অন্য কোন পেইজে যেতে চায় তখন তাকে পুনরায় লগ ইন করতে হয় না। উপরিউক্ত সেশন আইডির সাহায্যে তার Authorization এর কাজটা হয়ে যায়। এই একই কাজটাই JWT করে দেয় একটু অন্যভাবে। সার্ভারে আলাদা করে সেশন আইডি স্টোর করা লাগেনা, একটা JWT তৈরি করে দিয়ে দেয়া হয়। তার মাধ্যমেই পরবর্তীতে প্রয়োজন অনুযায়ী Authorization হয়ে যায়। JWT যে ওয়েবসাইট তৈরি করে দেয় তাকে বলে Issuer এবং যার জন্য তৈরি করে তাকে বলে Audience।

### Difference between MVC Controller and API Controller

MVC Controller একটা View রিটার্ন করে আর API Controller রিটার্ন করে বিভিন্ন স্ট্যাটাস (Ok, BadRequest ইত্যাদি)।

### What is CORS (Cross Origin Resource Sharing)?

CORS হচ্ছে এমন একটি পদ্ধতি যা চেক করে যে কোথা থেকে কোন নির্দিষ্ট API এ কল আসছে। কোন একটা নির্দিষ্ট URL থেকে রিকোয়েস্ট আসলে শুধুমাত্র API সেটা রিসিভ করবে, তা বাদে অন্য কোন URL থেকে রিকোয়েস্ট আসলে সেটা ডিনাইড হবে। এই বিষয়টা দেখভাল করে CORS।

### Worker Service

Worker Service এর আগের নাম হচ্ছে Windows Service, এর সাহায্যে আমরা ব্যাকগ্রাউন্ডে বিভিন্ন কাজ করতে পারি। এটা একটা ডট নেট প্রজেক্ট, এর মধ্যে Serilong, Autofac এর মতো ফ্রেমওয়ার্ক বা কনটেইনার ব্যবহার করা যায়। শিডিউলিং এর কাজ করা যায় এর সাহায্যে। ব্যাকগ্রাউন্ড সার্ভিসের কাজগুলোর জন্য সাধারণত কোন UI দরকার পড়েনা।

Worker Service কে Install করতে হলে প্রথমে এটাকে পাবলিশ করতে হবে। এটাকে আমরা যেকোন একটা ফোল্ডারে Publish করতে পারি। পাবলিশ যেখানে করবো সেই ফোল্ডারে অনেকগুলো ফাইলের সাথে সাথে একটা .exe ফাইল তৈরি হয়। এই ফাইলের নাম দিয়ে একটা কমান্ড রান করলে Worker Service টা Install হয়ে যায়।

### Docker

ভার্চুয়ালাইজেশনের জন্য Docker ব্যবহার করা হয়। কোন একটি নির্দিষ্ট অপারেটিং সিস্টেমের আন্ডারে বিভিন্ন ধরনের সিস্টেম ভ্যারিয়েবলের সমন্বয়ে তৈরি করা কোন একটি প্রজেক্ট, অন্য কোন সিস্টেমে গিয়ে হয়তো রান করবেনা। এই সমস্যা সমাধানের জন্য পূর্বে VMware, VM VirtualBox ইত্যাদি ব্যবহার করা হতো। কিন্তু এগুলো খুব বেশি রিসোর্স খেয়ে ফেলতো, তাই লাইটওয়েট আর্কিটেকচারে নির্মিত Docker খুব বেশি জনপ্রিয় হয়ে উঠেছে। ‍startable project কে ডকারাইজ করতে হয়। সেজন্য আমরা নিচের ধাপগুলো অনুসরণ করতে পারি। প্রথমে Docker File বানাতে হয়, এর মধ্যে আমরা বলে দিতে পারি কোন কোন ফোল্ডার এর মধ্যে থাকবে, কোন অপারেটিং সিস্টেমে এটা চলবে ইত্যাদি।

Docker File কে build করলে Docker Image তৈরি হয়। Docker Image কে রান করলে Docker Container তৈরি হয়।

Docker File ----- Docker Image ----- Docker Container

Docker Container এর মধ্যে আমরা প্রজেক্ট রান করতে পারি। ডকার ফাইলের নাম হয় Dockerfile এবং এর কোন এক্সটেনশন থাকেনা। Docker Compose File এ সব তথ্য দিয়ে দিলে কমান্ডের ঝামেলা থেকে রক্ষা পাওয়া যায়। এটা একটা yml ফাইল। এনভায়রনমেন্ট ভ্যারিয়েবলগুলো লিখার জন্য আমরা web.env ফাইল ব্যবহার করি।

### Testing

অটোমেটেড টেস্টিং এর মধ্যে রয়েছে সিস্টেম, ইন্টিগ্রেশন ও ইউনিট টেস্টিং। Unit testing এর জন্য আমরা NUnit ব্যবহার করবো। Test File এর মেথডগুলো অনেকটা এরকম হয়, OneTimeSetUp — SetUp — TearDown — OneTimeTearDown — Test (Arrange-Act-Assert)। Arrange অংশে ইনিশিয়ালাইজেশনের কাজ করা হয়, Act অংশে যে মেথডকে টেস্ট করা লাগবে সেটা কল করা হয় এবং Assert অংশে কোড চেক করা হয়। Unit test এর নিয়ম হচ্ছে আমরা যে মেথডটাকে টেস্ট করছি তার বাইরে কখনোই যাওয়া যাবেনা। তাই আমরাকে এমনভাবে টেস্ট লিখতে হবে যেন, টেস্টিং অবস্থায় থাকা মেথডের ডিপেনডেন্সিগুলো না থাকে।

ডিপেনডেন্সিগুলোকে মক করতে হয় এবং যাকে টেস্ট করতে হবে তাকে মক করতে হয় না। void method ঠিকমতো কাজ করছেনা কিনা বা কল হয়েছে কিনা সেটা বোঝার জন্য verifiable ব্যবহার করতে হয়। exception টেস্টিং এর জন্য Should ব্যবহার করা হয়।

ইন্টারফেস ব্যবহারের মাধ্যমে ডিপেনডেন্সি ইনজেকশন হয়ে থাকলে টেস্টিং এর জন্য কোড প্রস্তুত হয়ে থাকে। সাধারণত public method কে টেস্ট করা হয়, private বা protected method কে টেস্ট করা হয় না।

মোট কোডের কতটুকু অংশ টেস্ট করা হয়েছে সেটাকে কোড কভারেজ বলা হয়। DTO (Data Transfer Object) হচ্ছে একটা অবজেক্ট যেটা ডাটাকে এনক্যাপসুলেট করে অ্যাপ্লিকেশনের এক লেয়ার থেকে অন্য লেয়ারে পাঠানোর কাজ করে।

### Diagrams

Agile Process বলতে বোঝায় যে প্রক্রিয়ায় খুব দ্রুত ডেভেলপমেন্ট করা হয়। Backlog হচ্ছে অনেকটা লিস্টের মতো। কি কি কাজ আমরা করবো সেটা Backlog এ রাখা হয়। SCRUM হচ্ছে একটা Methodology। অনেকগুলো Sprint নিয়ে একটা প্রজেক্ট হতে পারে। বর্তমানে Agile Process এর জনপ্রিয়তার কারণে UML Diagram এর প্রয়োজনীয়তা ধীরে ধীরে কমে যাচ্ছে।

UML Diagram এর প্রথমটা হচ্ছে Use case diagram। এটা ব্যবহার করা হয় Requirement collection এর জন্য।

A use case diagram is a graphical depiction of a user’s possible interactions with a system. A use case diagram shows various use cases and different types of users (primary and secondary) the system has and will often be accompanied by other types of diagrams as well. The use cases are represented by either circles or ellipses.

Use case (feature) এর সাথে user (Actor) এর সম্পর্ক দেখানোর জন্য সরলরেখা ব্যবহার করা হয়। একটা ফিচার যদি অন্য একটা ফিচারের উপর নির্ভরশীল হয়, তাহলে তাদের মধ্যে include মেটাট্যাগ লাগানো হয়। কোন ফিচার অন্য কোন ফিচারকে অপশনালি এক্সটেন্ড করতে পারে, সেক্ষেত্রে extend মেটাট্যাগ লাগানো হয়। ফিচার থেকে ফিচারের সম্পর্ক বোঝানোর জন্য তীরচিহ্নসহ সরলরেখা ব্যবহার করা হয়।

Use case diagram এর পরের diagram টা হচ্ছে Class diagram, এটা কোডিং রিলেটেড। ক্লাসগুলোর মধ্যে সম্পর্ক বোঝানোর জন্য এই ডায়াগ্রাম ব্যবহার করা হয়। abstract class কে ইটালিকভাবে লিখা হয়। ইন্টারফেস বোঝানোর জন্য মেটাট্যাগের মধ্যে <<interface>> লিখা হয়। static class কে underlined করে লিখা হয়। ক্লাসের মধ্যে যোগ চিহ্ন দিয়ে বোঝানো হয় public method, আর বিয়োগ চিহ্ন দিয়ে private method বোঝানো হয়। হ্যাশ (#) চিহ্ন দিয়ে protected method কে বোঝানো হয়। কোন ক্লাস যদি কোন ইন্টারফেসকে ইমপ্লিমেন্ট করে তাহলে তাদের মধ্যে ডটেড অ্যারো দিয়ে সম্পর্ক বোঝানো হয়। আর যদি কোন ক্লাস অন্য কোন ক্লাস থেকে ইনহেরিটেড হয়, তাহলে তাদের মধ্যে সলিড অ্যারো দিয়ে সম্পর্কটা বোঝানো হয়। দুইটা ক্লাসের মধ্যে স্ট্রং সম্পর্ক থাকলে, তাদের মধ্যে ব্ল্যাক ডায়মন্ড দিয়ে সম্পর্ক বোঝানো হয়। এটাকে কম্পোজিশন বলা হয়। আর দুর্বল সম্পর্ক হলে সাদা ডায়মন্ড দিয়ে সম্পর্ক দেখানো হয়, এটাকে অ্যাগ্রিগেশন বলে। আর দুটি ক্লাসের মধ্যে সম্পর্ক বোঝা না গেলে তাদের মধ্যে দুই অ্যারোওয়ালা রেখা দেয়া যায়, এটাকে অ্যাসোসিয়েশন বলে। অরিজিনাল UML এ প্রপার্টির কোন অস্তিত্ব নাই। শুধু field এবং method রয়েছে, field গুলো হচ্ছে variable।

A code smell is any characteristic in the source code of a program that possibly indicates a deeper problem.

Class diagram এর পরের diagram টা হচ্ছে Sequence diagram, কোন ক্লাস কোন সিকোয়েন্সে রান করবে সেটা বোঝানোর জন্য এই ডায়াগ্রাম ব্যবহার করা হয়। এই ডায়াগ্রামে একটা টাইমলাইন থাকে। এটা দ্বারা বোঝানো হয়, কোন ক্লাস কখন শুরু হচ্ছে এবং কখন শেষ হচ্ছে।

### Creational Design Pattern

Design Pattern হচ্ছে একটা নির্দিষ্ট সমস্যার সমাধান। ক্লাস কিভাবে ডিজাইন করা যেতে পারে তার একটা দিকনির্দেশনা। একটা Design Pattern একটা কাজই করে, একাধিক কাজ করেনা। অর্থাৎ একটা সমস্যাই সমাধান করে। অনেক ধরনের Design Pattern আছে।

Creational বলতে অবজেক্ট তৈরি করার বিষয়টা বোঝাচ্ছে। new দিয়ে অবজেক্ট তৈরি করা যায়, কিন্তু এটা ভালো ব্যাপার না। অবজেক্ট তৈরি করার বিষয়টা যতটা abstract করা যায় ততই ভালো। তাই এই Design Pattern এর অবতারণা ঘটেছে। Creational Design Pattern এর মধ্যে একটা হচ্ছে Singleton Design Pattern। এই প্যাটার্নের ভাষ্য অনুযায়ী এর অবজেক্টের একটিমাত্র ইন্সট্যান্স তৈরি হবে। Constructor কে প্রাইভেট বানিয়ে কাজটা সহজেই করা যায়। এতে করে যে কেউ ইন্সট্যান্স তৈরি করতে পারবেনা।

Singleton is creational design pattern that lets you ensure that a class has only one instance, while providing a global access point to this instance.

লগারের ক্ষেত্রে আমরা Singleton Design Pattern ব্যবহার করে থাকি, কারণ লগার ফাইল সিস্টেম নিয়ে কাজ করে। ফাইল সিস্টেম, নেটওয়ার্ক, ডাটাবেজ এগুলো হেবি অবজেক্ট। এ ধরনের অবজেক্ট নিয়ে কাজ করার সময় খেয়াল রাখতে হবে যেন রিসোর্স খুব বেশি কনজিউম না হয়, তাই এই ব্যবস্থা।

এরপরের Creational Design Pattern হচ্ছে Prototype Design Pattern। বিভিন্ন গেমে অনেক সময় একই রকম অনেক ক্যারেক্টর থাকে। তাহলে কোন একটি ক্যারেক্টরকে যদি বানাতে গিয়ে আমার একটা অবজেক্ট প্রয়োজন পড়ে, হুবহু একই ক্যারেক্টার আরেকবার বানানোর জন্য আমাকে নতুন করে অবজেক্ট বানাতে হবে না। আগের অবজেক্টটাকেই কপি করে নিলেই হবে। এক্ষেত্রে আমরা যে প্যাটার্ন অনুরসরণ করি সেটাই Prototype Design Pattern।

Prototype is a creational design pattern that lets you copy existing objects without making your code dependent on their classes.

আবার কোন ফাইল কপি করতে চাইলেও আমরা এই প্যাটার্ন ব্যবহার করতে পারি। এই প্যাটার্ন ব্যবহারের সময় আমরা IClonable ইন্টারফেস ব্যবহার করলে আরও কিছু বাড়তি সুবিধা পেতে পারি।

এরপরের Creational Design Pattern হচ্ছে Builder Design Pattern। কোন জটিল বস্তু তৈরি করতে হলে আমরা সেটা ধাপে ধাপে করতে পারি। যেমন, যদি একটা গাড়ি বানাতে হয়, তাহলে কোন এক ধাপে হয়তো সেটাতে চাকা লাগাতে হবে, দরজা লাগাতে হবে, ইঞ্জিন লাগাতে হবে ইত্যাদি। এরকম পরিস্থিতিতে আমরা এই প্যাটার্ন ব্যবহার করি। মেথড চেইনিং এর মাধ্যমে কাজটা করা যেতে পারে।

Builder is a creational design pattern that lets you construct complex objects step by step. The pattern allows you to produce different types and representations of an object using the same construction code.

MVC প্রজেক্টের program ফাইলে এই প্যাটার্ন এবং মেথড চেইনিং এর ব্যবহার দেখা যায়।

এরপরের Creational Design Pattern হচ্ছে Factory Design Pattern। এই প্যাটার্ন ব্যবহার করে আমরা অবজেক্ট বানানোর বিষয়টি অ্যাবসট্র্যাক্ট করে ফেলতে পারি। বিল্ডার প্যাটার্নের সাথে এর পার্থক্য হচ্ছে এক্ষেত্রে অতটা জটিল কিছু বানানোর প্রয়োজন পড়েনা।

Factory method is creational design pattern that provides an interface for creating objects in a superclass, but allows subclasses to alter the type of objects that will be created.

এরপরের Creational Design Pattern হচ্ছে Abstract Factory Design Pattern। ফ্যাক্টরি সাধারণত প্রোডাক্ট তৈরি করে, যেটা আমরা Factory Design Pattern এর ক্ষেত্রে দেখেছি। আর Abstract Factory হচ্ছে ফ্যাক্টরি তৈরি করার ফ্যাক্টরি।

Abstract Factory is a creational design pattern that lets you produce families of related objects without specifying their concrete classes.

### AWS (Amazon Web Services)

EC2 (Elastic Compute Cloud) হচ্ছে সার্ভার তৈরি করার একটা ফিচার। Instances তৈরির মাধ্যমে আমরা windows/linux virtual machine বানাতে পারি।

দুইটা startable project কে একসাথে রান করা যায়, যেহেতু তারা আলাদা পোর্টে চলে তাই সমস্যা হয় না।

Shared hosting এ একটা ফিজিক্যাল সার্ভারের মধ্যে কিছু ফোল্ডার বানিয়ে বিভিন্নজনের মধ্যে দিয়ে দেয়া হয়। কোন একজন নির্দিষ্ট ইউজার যদি বেশি রিসোর্স নিয়ে নেয় তাহলে অন্য ইউজারের ভাগে কম পড়বে। Dedicated hosting এ একটা ফিজিক্যাল সার্ভার পুরোটাই একজনকে দিয়ে দেয়া হয়। এটা নষ্ট হয়ে যেতে পারে, নেটওয়ার্ক ডাউন হতে পারে। Cloud hosting এ হাজার হাজার ফিজিক্যাল সার্ভার দিয়ে রিসোর্স পুল বানানো থাকে। ইউজার ইচ্ছামতো কনফিগারেশনের ভার্চুয়াল মেশিন বানিয়ে কাজ করতে পারে। এই কাজটাই AWS এর EC2 থেকে Instance বানিয়ে করা যায়। Instance বানানোর সময় অনেককিছু কনফিগার করা লাগে। যেমন, কোন ধরনের হার্ড ড্রাইভ (কম খরচের জন্য gp2,) বা অপারেটিং সিস্টেম লাগবে (free tier eligible - t2.micro) ইত্যাদি। Instance বানানো হয়ে গেলে RDP Client এর মাধ্যমে Remote Desktop ডাউনলোড করে নিতে হয়। ফিজিক্যাল মেশিনে যেমন পেন ড্রাইভ লাগানো যায়, নেটওয়ার্ক বিচ্ছিন্ন করা যায় এ কাজগুলো ভার্চুয়াল মেশিনে করা যাবেনা, বাকি সবকিছুই করা যাবে। Security group টা ফায়ারওয়ালের মতো কাজ করে।

লিনাক্সের সার্ভারে var এর মধ্যে apache এর পেইজগুলো থাকে। একই কি দিয়ে একাধিক সার্ভার বানানো যায়। তবে প্রোডাকশন লেভেলে সাধারণত বানানো হয়না।

যখন মাল্টিপল সার্ভার থাকে তখন প্রেসার কমে যায়। একাধিক সার্ভারে একই ওয়েবসাইট থাকে, যখন ইউজার ওই নির্দিষ্ট URL এ হিট করে তখন আসলে ইউজার Load Balancer এ হিট করে। Load Balancer ইউজারকে তখন যেকোন একটা সার্ভারে নিয়ে যায়। এভাবে অন্য কোন ইউজার আসলে তাকে হয়তো দ্বিতীয় সার্ভারে নিয়ে যাবে, এভাবে প্রেসার কমে যায় সার্ভারের উপর। এভাবে যদি দশ হাজার ইউজারকে এরকম অ্যাভেলেইবল ৫ টা সার্ভারে ভাগ করে দেয়া হয়, তাহলে সামগ্রিক চাপ কমে যায়। এই বিষয়টাকে বলা হয় Horizontal Scaling।

সার্ভারের সংখ্যা না বাড়িয়ে যদি সার্ভারের আকৃতি বড় করা হয়, তাহলে এটাকে বলা হয় Vertical Scaling। Horizontal Scaling এর মাধ্যমে সার্ভারের আনলিমিটেড পাওয়ার বাড়ানো যায় কিন্তু Vertical Scaling এর মাধ্যমে তা সম্ভব না। একটা অবস্থায় গিয়ে আর সার্ভারের ক্ষমতা বাড়ানো যায়না। তাহলে ইউজারদের ভালো অভিজ্ঞতা দেয়ার জন্য আমাদের দরকার Horizontal Scaling এবং সাথে একটা Load Balancer। আবার Load Balancer কাজ করে Target Group (A Target Group tells a Load Balancer where to direct traffic to) এর সাথে। Load Balancer শুধু Load বন্টন করে দেয় তা না, সাথে কোন IP address সচল আছে কিনা সেটাও চেক করে। Load Balancer কে DNS দিয়ে ব্রাউজ করতে হয়।

একই ওয়েবসাইট বিভিন্ন সার্ভারে রেখে ইউজারকে বোকা বানিয়ে Load Balancer ব্যবহার করা যায়। তবে মাঝেমাঝে সমস্যা দেখা দিতে পারে। দেখা গেলো যে, সার্ভার ১ এ প্রোফাইল পিকচার আপলোড করা হয়েছে। এরপরের বার সার্ভারে হিট করলে যদি Load Balancer সার্ভার ২ এ নিয়ে যায়, সেক্ষেত্রে ইউজার প্রোফাইল পিকচার দেখতে পাবেনা। এই সমস্যা এড়ানোর জন্য আমরা ডেডিকেটেড সার্ভার রাখতে পারি ফাইল স্টোরেজের জন্য।

Load Balancer ব্যবহার করার জন্য যেহেতু আমাদের একাধিক সার্ভার প্রয়োজন, এখন প্রশ্ন হচ্ছে যে কতগুলো সার্ভার আমরা ব্যবহার করবো? ইউজারের সংখ্যার উপর নির্ভর করে সার্ভার সংখ্যা ঠিক করতে হয়। কিন্তু ইউজার কখন বেড়ে যাবে বা কমে যাবে এটা ম্যানুয়ালি খেয়াল রাখা কষ্টসাধ্য বিষয়। ঠিক এই সমস্যাটা সমাধানের জন্য রয়েছে Auto Scaling। এই ফিচার ব্যবহারের মাধ্যমে প্রয়োজন অনুসারে সার্ভার সংখ্যা বেড়ে বা কমে যাবে। এর জন্য আলাদা কোন খরচ পড়েনা।

এখন খেয়াল করার বিষয় হচ্ছে যে, শুধু সার্ভার বাড়ালেই তো হবেনা। সার্ভারের মধ্যে প্রয়োজনীয় জিনিসপত্র গুছিয়ে রাখা লাগবে। একারণে আমাদের প্রয়োজন অনুসারে একটা সার্ভার বানিয়ে তার ইমেজ তৈরি করে রাখা হয় এবং প্রয়োজন অনুসারে এই ইমেজ (AMI - Amazon Machine Image) থেকেই নতুন নতুন সার্ভার ডিপ্লয় হতে থাকে। ইমেজ ডিলিট করা যায় না, এটাকে ডিরেজিস্টার করতে হয়।

A Spot Instance is a specialized Amazon Web Services (AWS) instance that allows you to access and utilize unused EC2 capacity at a steeply discounted rate.

Amazon Simple Email Service (SES) is a cost-effective, flexible and scalable email service that enables developers to send mail from within any application.

Load Balancer, Auto Scaling ইত্যাদি সব ফিচার কোড দিয়েও ইমপ্লিমেন্ট করা যায়। এমনকি কমান্ড লাইন দিয়েও করা যায়। তাহলে প্যানেল, কোড ও কমান্ড এই তিনভাবে কাজগুলো করা যায়।

Amazon Simple Queue Service (SQS) is a managed message queuing service technical professionals and developers use to send, store and retrieve multiple messages of various sizes asynchronously.

কিউ এর মধ্যে ছোট তথ্য (max 256 kb) রাখা যায়, সেটা দেখে সার্ভার থেকে আসল ডাটা তুলে নিয়ে আসে। কিউ থেকে মেসেজ নিয়ে সেটা প্রসেসিং করতে না পারলে পুনরায় সেটা কিউতে গিয়ে জমা হয়। আমরা বলে দিয়ে রাখতে পারি যে, কতবার ব্যর্থ হলে সেটা পুনরায় জমা হবে। সেই নম্বরটা ক্রস করলে উল্লেখিত মেসেজটা আর কিউতে গিয়ে জমা না হয়ে যেখানে জমা হয় তাকে Dead Letter Queue বলে।

Queue এর পলিসির মধ্যে arn বলে একটা জিনিস আছে, এটা অনেকটা id এর মতো। Distributed System তৈরির ক্ষেত্রে Queue টা খুবই গুরুত্বপূর্ণ ফিচার। Purge করে দিলে Queue খালি করে দেয়।

S3 (Simple Storage Service) Bucket হচ্ছে একটা ফাইল স্টোরেজ, গুগল ড্রাইভের মতোই এটার কাজ। বাকেটের নাম ইউনিক এবং ছোট হাতের অক্ষরের হতে হয়। একই নামে একাধিক ফাইল আপলোড করতে হলে versoning এনাবেল করে রাখতে হয়। বাকেটে ফাইল আপলোড, সেখান থেকে ডাউনলোড করতে বিল কাটে। ইউজার জেনারেটেডে কোন ডাটা সার্ভারে রাখা যাবেনা, কারণ যেকোন সময় এটা ডাউন হয়ে যেতে পারে। তাই মাল্টিসার্ভার রিলায়েবল সিস্টেম বানাতে হলে আমাদের আলাদা ফাইল স্টোরেজ দরকার।

বিভিন্ন ধরনের S3 Bucket রয়েছে, যেমন Standard, One Zone, Glacier ইত্যাদি। এগুলো বিভিন্ন দামে বিভিন্নরকম সুযোগ সুবিধা দেয়। Machine এর জন্য role এবং ইউজারের জন্য policies অপশন রয়েছে।

AWS Identity and Access Management (IAM) provides fine-grained access control across all of AWS. With IAM, you can specify who can access which services and resources, and under which conditions.

বড় একটা অ্যাপ্লিকেশনকে ক্ষুদ্র ক্ষুদ্র ‍সার্ভিসে ভেঙ্গে ফেলে সেগুলোকে দিয়ে কাজ করিয়ে নেয়াকে Microservice বলে। একটা সার্ভিসের একটা কাজ থাকবে। সার্ভিসগুলোর মধ্যে কোন যোগাযোগ থাকবেনা। কোন সার্ভিস কাজ শেষ করে Queue তে মেসেজ দিয়ে রাখবে, সেটা দেখে অন্য সার্ভিস কাজ করবে। প্রতিটা সার্ভিসের URL থাকবে, সেগুলো কলের মাধ্যমে কাজ হবে।

DynamoDB একটা NoSQL ডাটাবেজ। বিভিন্ন ধরনের NoSQL Database রয়েছে, যেমন Key-Value Store, Document Store, Graph Database, Column Oriented Database ইত্যাদি। DynamoDB হচ্ছে Key-Value ও Document টাইপ হাইব্রিড ডাটাবেজ। DynamoDB এর সার্ভিস হচ্ছে Managed অর্থাৎ Scaling, Reliability নিয়ে আমাদের চিন্তা করার দরকার পড়েনা। অটোমেটিক্যালি সেটা হ্যান্ডেলড হয়ে যায়।

Consistency, Availability এগুলো হচ্ছে যেকোন সিস্টেম বা সফটওয়্যার বা সার্ভারের আবশ্যক গুণ। একই ডাটার অনেক রেপ্লিকা বানিয়ে অনেকগুলো সার্ভারে রেখে দিলে ডাটার Availability বেড়ে যায়। কিন্তু কোন একটি সার্ভারের ডাটা আপডেট করলে বাকি সার্ভারগুলোতে আপডেটেড ডাটা পাওয়া যাবেনা। এতে করে ডাটার Consistency নষ্ট হবে। তাই সবদিক খেয়াল রাখা জরুরি।

DynamoDB ডাটাবেজ টেবিল তৈরির মাধ্যমে কাজ করে। টেবিলে রিড/রাইটের গতি নির্ভর করে আমরা কি ধরনের ফিচার নিচ্ছি। NoSQL ডাটাবেজে শুধুমাত্র প্রাইমারি কি দরকার, অন্য কোন তথ্য দরকার পড়েনা। এখানে একেকটা রো তে একেক রকম তথ্য রাখা যায়। DynamoDB তে নেস্টেড অবজেক্ট রাখা যায়না তবে লিস্ট আকারে কালেকশন রাখা যায়। এই ডাটাবেজে কোন তথ্য খুঁজে নিয়ে আসার জন্য কোয়েরি এবং স্ক্যান দুটি পদ্ধতি আছে। কোয়েরির জন্য আইডি দেয়া লাগে, এটা দিয়ে খুব তাড়াতাড়ি ডাটা বের করে নিয়ে আসতে পারে। কিন্তু অন্য কিছু দিয়ে খুঁজতে হলে স্ক্যান (লিনিয়ার টাইম) করতে হয়, তাই অনেক বেশি সময় ও খরচ লাগে।

সাধারণত High velocity of data, High volume of data ও unstructured data হলে NoSQL ডাটাবেজ ব্যবহার করা হয়। EC2 হচ্ছে Infrastructure রিলেটেড আর SQS, DynamoDB ও S3 Bucket হচ্ছে managed service। ক্লাউডের মধ্যে ৩ ধরনের সার্ভিস পাওয়া যায়।

```
IaaS	=	Infrastructure as a Service	Example: EC2
PaaS	=	Platform as a Service		Example: AWS Elastic Beanstalk
SaaS	=	Software as a Service		Example: Amazon CloudWatch
```

AWS এর বিভিন্ন সার্ভিস নিয়ে পড়াশোনা করতে চাইলে তাদের আছে AWS Documentation। AWS এর Command Line Interface (CLI) দিয়ে সব ধরনের ফিচার ব্যবহার করা যায়। Documentation এর মধ্যে সব কমান্ড পাওয়া যাবে।

### Single Page Application (SPA)

SPA বানানোর জন্য Angular, React.js, Vue.js ইত্যাদি বিভিন্ন ফ্রেমওয়ার্ক ব্যবহার করা হয়। এদের কাজ হচ্ছে মূলত Front End ডিজাইন করা। Static Website হলে Back End এর প্রয়োজন নাই। তবে Back End এর সাহায্য নিয়ে Dynamic Website বানানো যায়। Back End যেকোন টেকনোলজির হতে পারে যেমন, C#, Java, Python, Node, Express ইত্যাদি। এই Front End এবং Back End এর মধ্যে যোগাযোগ হয় HTTP এর মাধ্যমে।

এটাকে SPA বলার কারণ হচ্ছে যে, Angular, React.js, Vue.js এগুলো Javascript ভিত্তিক লাইব্রেরি। তাই এরা Client Side এ Rendering এর কাজগুলো করতে পারে। Back End এ সবসময় যেতে হয়না, যখন কোন ডাটার দরকার পড়ে তখন Ajax এর মাধ্যমে asynchronously ডাটা তুলে নিয়ে আসে। এর ফলে পেজ Reload বা Refresh করার দরকার খুব একটা পড়েনা। যেহেতু আমরা একটা পেজেই থাকি তাই এটাকে SPA বলা হয়। তবে চাইলে এই Application গুলোতে multiple page বানানো যায়।

### Angular

Angular হচ্ছে একটা component বেজড ফ্রেমওয়ার্ক। এর প্রথম component হচ্ছে App বা Root। কোন component এর মধ্যে আমরা যত চাই তত component যুক্ত করতে পারি। component গুলো ট্রি আকারে বাড়তে থাকে। View অরিয়েন্টেড reusable কিছু তৈরি করার প্রয়োজন পড়লে আমরা একটা component বানাই। Angular এর সাথে Bootstrap ব্যবহার করা যায় না, তবে এর একটা port আছে। সেটা দিয়ে ব্যবহার করা যায়। Material UI বলে একটা css framework আছে, এটা Angular এর সাথে ব্যবহার করা হয়।

```
নতুন প্রজেক্ট তৈরি করার কমান্ড	ng new my-site
```

উপরের কমান্ড দিয়ে কেবইল তৈরি হওয়া ওয়েবসাইট টা একটা স্বাধীন ওয়েবসাইট, এর সাথে Asp.net এর ওয়েবসাইটের কোন সম্পর্ক নাই। এটা আমরা Visual Studio Code এ চালু করবো। Visual Studio তে Angular এর জন্য একটা টেমপ্লেট আছে। তবে এক্সপার্টরা দুইটা বিষয়কে (Asp.net ও Angular এর ওয়েবসাইট) আলাদা রাখার জন্য পরামর্শ দেন। Visual Studio তে Angular এর প্রজেক্ট চালালে Front End এবং Back End এর বিষয়গুলো মিক্স আপ হয়ে থাকে। এটা Front End Developer দের জন্য বেশ ঝামেলার। তাই এগুলো আলাদা রাখাই ভালো।

Visual Studio Code এর main.ts থেকে অ্যাপ টা চালু হয়। Module হচ্ছে Functional Unit এবং component হচ্ছে View অরিয়েন্টেড। একটা component এর চারটা ফাইল থাকে। একটা html, একটা css, একটা typescript (মূল লজিক্যাল বিষয়গুলো এখানে থাকে) এবং একটা spec.ts (টেস্টিং এর জন্য) ফাইল।

```
প্রজেক্ট চালু করার কমান্ড		ng serve
নতুন component বানানোর কমান্ড    ng generate component components/button
```

Angular দ্বারা তৈরি ওয়েবসাইট Back End থেকে ডাটা তুলে নিয়ে আসতে পারে API এর মাধ্যমে। Angular এ proxy ব্যবহার করলে সেটা CORS কে বাইপাস করে কাজ করতে পারে। আবার proxy উঠিয়ে দিলে আর Back End থেকে ডাটা তুলে নিয়ে আসতে পারে না।

### Multi-Tenant Architecture

ই-কমার্স সাইটে যখন কোন শপ রেজিস্টার করে তখন তার জন্য একটা ফাইল স্টোরেজ ও একটা ডেডিকেটেড সার্ভার ইস্যু করা হয়। একেক শপের কাস্টমার সংখ্যা একেক রকম হবে, কারও কম হবে এবং কারও বেশি হবে। তাই একে সার্ভারে একেক রকম চাপ পড়বে। যদি ডেডিকেটেড সার্ভার না দেয়া হতো তাহলে এক শপের কারণে অন্য শপের মালিকের ক্ষতি হতে পারতো। অর্থাৎ যে শপের কাস্টমার বেশি সে বেশি রিসোর্স নিয়ে যেত এবং ছোট শপের পারফর্ম্যান্সে চাপ পড়তো। এভাবে আলাদা আলাদা সার্ভার ও ফাইল স্টোরেজ থাকায় সে সমস্যা হয়না। একেই Multi-Tenant Architecture বা Multi-Tenancy বলে। এখানে প্রতিটি শপ একেকটা Tenant এবং ফাইল স্টোরেজ হচ্ছে Tenant Files ও সার্ভার হচ্ছে Tenant DB।
