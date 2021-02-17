# Leetcode Easy #175: Combine Two Tables


A humble tutorial for Leetcode challenge #175 Combine Two Tables.

<!--more-->

{{< admonition >}}
This tutorial is based on MySQL. The author had referred several answer from Leetcode community and improvised into this suggested answer.
{{< /admonition >}}


## 1 Problem: Reverse Integer

Write a SQL query for a report that provides the following information for each person in the Person table, regardless if there is an address for each of those people:
`FirstName, LastName, City, State`

**Table Schema: Person**

| Column Name | Type |
| --- | --- |
| PersonId | int |
| FirstName |  varchar |
| LastName | varchar |

`PersonId` is the primary key column for this table.

**Table Schema: Address**

| Column Name | Type |
| --- | --- |
| AddressId | int |
| PersonId |  int |
| City | varchar |
| State | varchar |

`AddressId` is the primary key column for this table.

---
---
---

## 2 Technical Analysis

### 2.1 Neccesary Columns

Name necessary column from two tables.

{{< admonition note "Solution: Basic SQL SELECT" >}}
1. Use `SELECT` to include all necesary column from two table.

``` sql
select a.FirstName,a.LastName from Person a;
select b.City,b.State from Address b;
```
{{< /admonition >}}

{{< admonition note "Expected Output" >}}

| FirstName | LastName |
| :--- | :--- |
| Allen | Wang |

{{< /admonition >}}


### 2.2 Combine Two Tables

We need to combine these two table into one.

{{< admonition note "Solution: SQL LEFT JOIN" >}}
1. Use `LEFT JOIN` ... `ON` to combine the tables.
2. Make sure same unique key of the tables.

``` sql
select a.FirstName,a.LastName,b.City,b.State from Person a
left join Address b
on a.PersonId = b.PersonId
```
{{< /admonition >}}

{{< admonition note "Expected Output" >}}
| FirstName | LastName | City | State |
| :--- | :--- | :--- | :--- |
| Allen | Wang | null | null |
{{< /admonition >}}

---
---
---

## 3 Test Bench

``` sql
select a.FirstName,a.LastName,b.City,b.State from Person a
left join Address b
on a.PersonId = b.PersonId
```

{{< admonition note "Result" >}}
| FirstName | LastName | City | State |
| :--- | :--- | :--- | :--- |
| Allen | Wang | null | null |
{{< /admonition >}}
