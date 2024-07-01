---
title: "Using Sets"
weight: 25
pre: "5. "
disableMathJax: false
---
{{< youtube TAkdPSAv1OA  >}}

One of the most common uses of set operations is in database systems. While we will not create a full database system here, we will show you the basics of how they work using our set operations. Assume you have three sets of people:

$$
\text{Students} = \{ \text{"Vanessa"}, \text{"Travis"}, \text{"Lu"}, \text{"Cole"}, \text{"Jordan"}, \text{"Elaine"}, \text{"Caleb"} \} \\
\text{Family} = \{ \text{"Amy"}, \text{"Scott"}, \text{"Vanessa"}, \text{"Lauren"}, \text{"Zachary"}, \text{"Jordan"}, \text{"Caleb"} \} \\
\text{Workers} = \{\text{"Lauren"}, \text{"Amy"}, \text{"Felix"}, \text{"Zachary"}, \text{"Quinn"}, \text{"Jordan"}, \text{"Gabrielle"} \}
$$

The goal of our application is to be able to answer the following types of questions about the data.

1. How many students are there?
2. How many workers are there?
3. How many workers are students too?
4. How many in my family do not go to school?
5. Who works and goes to school?
6. Who works or goes to school?
7. Who works and does not go to school?
8. Who in my family does not go to school?
9. Who in my family does not work or go to school?

The first step in our program is to add all the data to sets as shown below.

```tex
Set students = new Set()
students.add("Vanessa")
students.add("Travis")
students.add("Lu")
students.add("Cole")
students.add("Jordan")
students.add("Elaine")
students.add("Caleb")

Set family = new Set()
family.add("Amy")
family.add("Scott")
family.add("Vanessa")
family.add("Lauren")
family.add("Zachary")
family.add("Jordan")
family.add("Caleb")

Set workers = new Set()
workers.add("Lauren")
workers.add("Amy")
workers.add("Felix")
workers.add("Zachary")
workers.add("Quinn")
workers.add("Jordan")
workers.add("Gabrielle")
```

Once we have all the data in sets, we can use our set operations to find the information we are after. If we wanted to get a count of students and workers to answer questions 1 and 2, we can use the getter operation `getSize` in the following expressions.

```tex
students.getSize()
workers.getSize()
```

Question 3 is a little more interesting. Obviously, we will use the `getSize` operation again, but we can't use it directly on an existing set. We need to compute the set that holds only people who are both in the worker and student sets. Luckily, we have the `intersection` operation to help us do this. We simply need to compute the intersection of the workers and students and then take the size of that set as shown below.

```tex
workers.intersection(students).getSize()
```

Question 4 asks who is in the family set but is not in the student set. We can use the `difference` operation to compute this set. Again, we use the `getSize` operation to obtain the size.

```tex
family.difference(students).getSize()
```

Question 5 asks a slightly different question than question 3. It asks "who" works and goes to school, not just the number. Now, we compute the set of student-workers the same way, we just use the `toString` operation to produce a list of people in the set instead of just reporting the size.

```tex
workers.intersection(students).toString()
```

Question 6 asks who works or goes to school. To answer this question, we need a set of people which includes anyone who is either a worker or a student. This requires the `union` operation. We can compute the union of the two sets as follows.

```tex
workers.union(students).toString()
```

Question 7 wants to know who works and does not go to school. Again, this is everyone in workers who is not in students. This uses the `difference` operation as shown below.

```tex
workers.difference(students).toString()
```

Question 8 is similar and asks who in the family does not go to school. Obviously, we can use the previous expression and just replace the workers set with the family set.

```tex
family.difference(students).toString()
```

Finally, question 9 asks who in the family does not work or go to school. This is basically asking who is in the family set that is not in the work set or the school set. There are actually a couple of ways to approach this. We could take the difference between the family and the workers and then take the difference between the resulting set and the students as shown below.

```tex
family.difference(workers).difference(students).toString()
```

Alternatively, we could take the difference between the family and the union of the worker and student sets. This solution is shown below.

```tex
family.difference(workers.union(students)).toString()
```

If we put all this into a program with the appropriate statements to write the solutions to the console, we would get the following output.

```tex
How many students are there?
7

How many workers are there?
7

How many workers are students too?
1

Who in my family does not go to school?
4

Who works and goes to school?
Jordan

Who works or goes to school?
Lauren, Amy, Felix, Zachary, Quinn, Gabrielle, Vanessa, Travis, Lu, Cole, Jordan, Elaine, Caleb

Who works and does not go to school?
Lauren, Amy, Felix, Zachary, Quinn, Gabrielle

Who in my family does not go to school?
Amy, Scott, Lauren, Zachary

Who in my family does not work or go to school?
Scott
```

As you can see, we can use set operations to quickly and easily compute solutions to database type applications. While we don't often create special set-based solutions to data applications like this, we do use existing database applications that work on the same principle. 
