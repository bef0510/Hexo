---
title: C# 屬性 GET/SET 演變
date: 2019-05-28 12:10:41
tags:
 - C#
 - Class
categories: 
 - ASP.Net
---

# C# 屬性 GET/SET
#### C# 1.0 
    public class Employee
    {
        private string name;

        public string Name
        {
            get { return this.name; }
            set { this.name = value; }
        }

        private int age;

        public int Age
        {
            get { return this.age; }
            set { this.age = value; }
        }
    }

#### C# 2.0 可限定存取範圍
    public class Employee
    {
        private string name;

        public Employee(string name, int age)
        {
            this.name = name;
            this.age = age;
        }

        public string Name
        {
            get { return this.name; }
            private set { this.name = value; }
        }

        private int age;

        public int Age
        {
            get { return this.age; }
            private set { this.age = value; }
        }
    }

#### C# 3.0 自動屬性
    public class Employee
    {
        public Employee(int age)
        {
            this.Age = age;
        }

        public string Name { get; set; }

        public int Age { get; private set; }
    }

#### C# 6.0 唯讀自動屬性
    public class Employee
    {
        public Employee(int age)
        {
            this.Age = age;
        }

        public string Name { get; set; } = "Michael";

        public int Age { get; } = 30;

        public string Birth => "1989/12/31";
    }

# Reference
[C# 的唯讀自動屬性是怎樣煉成的](https://www.huanlintalk.com/2018/02/c-readonly-auto-property-from-beginning.html)