# Lambda Streams Java Demo

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Java programs demonstrating advanced functional programming concepts using **Lambda Expressions** and **Stream Operations**. This project covers practical implementations of sorting, filtering, grouping, and statistical operations on different datasets.

## 📚 Overview

This repository contains three comprehensive Java projects that showcase modern functional programming techniques introduced in Java 8+. Each project demonstrates real-world use cases of lambda expressions and streams for data processing.

## 🎯 Project Objectives

### Part A: Sorting Employee Objects Using Lambda Expressions
**Objective**: Develop a Java program that sorts a list of Employee objects based on fields like name, age, or salary using lambda expressions.

**Key Features**:
- Create Employee POJO with properties (name, age, salary, department)
- Implement multiple sorting strategies using lambda expressions
- Sort by name (alphabetically)
- Sort by age (ascending/descending)
- Sort by salary (ascending/descending)
- Combine multiple sort criteria using comparators
- Display results in formatted output

**Learning Outcomes**:
- Understanding lambda expressions syntax
- Working with Comparator interface
- Functional programming approach vs traditional loops

---

### Part B: Filtering and Sorting Students Using Streams
**Objective**: Create a Java program that uses lambda expressions and stream operations to filter students scoring above 75%, sort them by marks, and display their names.

**Key Features**:
- Create Student POJO with properties (id, name, marks, subject)
- Use streams to filter students with marks > 75%
- Sort filtered results by marks in descending order
- Extract and display only student names
- Chain multiple stream operations
- Calculate statistics (average, count, min, max marks)

**Learning Outcomes**:
- Stream API fundamentals (filter, map, sorted, collect)
- Method references and functional interfaces
- Terminal vs intermediate operations
- Working with collectors (Collectors.toList(), etc.)

---

### Part C: Stream Operations on Product Dataset
**Objective**: Process a large dataset of products using Java streams for grouping, finding maximum, and calculating averages.

**Key Features**:
- Create Product POJO with properties (id, name, category, price, quantity)
- Group products by category
- Find the most expensive product in each category
- Calculate average price by category
- Calculate total inventory value
- Find products within a price range
- Generate statistical summaries

**Learning Outcomes**:
- Advanced stream operations (groupingBy, reducing)
- Working with Map and collectors
- Functional aggregations and statistics
- Stream performance considerations

---

## 📁 Project Structure

```
lambda-streams-java-demo/
├── README.md
├── LICENSE
├── .gitignore
│
├── PartA_EmployeeSorting/
│   ├── src/
│   │   ├── model/
│   │   │   └── Employee.java
│   │   ├── service/
│   │   │   └── EmployeeSortingService.java
│   │   └── EmployeeSortingDemo.java
│   └── test/
│       └── EmployeeSortingTest.java
│
├── PartB_StudentFiltering/
│   ├── src/
│   │   ├── model/
│   │   │   └── Student.java
│   │   ├── service/
│   │   │   └── StudentFilteringService.java
│   │   └── StudentFilteringDemo.java
│   └── test/
│       └── StudentFilteringTest.java
│
├── PartC_ProductStreams/
│   ├── src/
│   │   ├── model/
│   │   │   └── Product.java
│   │   ├── service/
│   │   │   └── ProductStreamService.java
│   │   └── ProductStreamDemo.java
│   └── test/
│       └── ProductStreamTest.java
│
└── docs/
    ├── SETUP.md
    └── EXAMPLES.md
```

## 🚀 Setup Instructions

### Prerequisites
- **Java Development Kit (JDK)**: Version 8 or higher
- **IDE**: IntelliJ IDEA, Eclipse, or VS Code (optional)
- **Build Tool**: Maven or Gradle (optional)

### Step 1: Clone the Repository
```bash
git clone https://github.com/akashsinhamahapatra78-cmd/lambda-streams-java-demo.git
cd lambda-streams-java-demo
```

### Step 2: Verify Java Installation
```bash
java -version
```
Should output Java 8 or higher.

### Step 3: Compile the Code

**Using Command Line (Javac)**:
```bash
# For Part A
cd PartA_EmployeeSorting/src
javac model/Employee.java service/EmployeeSortingService.java EmployeeSortingDemo.java
java EmployeeSortingDemo

# For Part B
cd ../../PartB_StudentFiltering/src
javac model/Student.java service/StudentFilteringService.java StudentFilteringDemo.java
java StudentFilteringDemo

# For Part C
cd ../../PartC_ProductStreams/src
javac model/Product.java service/ProductStreamService.java ProductStreamDemo.java
java ProductStreamDemo
```

**Using Maven** (if pom.xml is configured):
```bash
mvn clean compile
mvn exec:java -Dexec.mainClass="EmployeeSortingDemo"
mvn exec:java -Dexec.mainClass="StudentFilteringDemo"
mvn exec:java -Dexec.mainClass="ProductStreamDemo"
```

### Step 4: Run Tests (Optional)
```bash
mvn test
```

## 💡 Starter Code Outline

### Part A: Employee.java
```java
public class Employee {
    private int id;
    private String name;
    private int age;
    private double salary;
    private String department;
    
    // Constructor, getters, setters, toString()
}
```

### Part A: EmployeeSortingService.java
```java
public class EmployeeSortingService {
    
    // Sort by name
    public static List<Employee> sortByName(List<Employee> employees) {
        return employees.stream()
            .sorted((e1, e2) -> e1.getName().compareTo(e2.getName()))
            .collect(Collectors.toList());
    }
    
    // Sort by age
    public static List<Employee> sortByAge(List<Employee> employees) {
        return employees.stream()
            .sorted((e1, e2) -> Integer.compare(e1.getAge(), e2.getAge()))
            .collect(Collectors.toList());
    }
    
    // Sort by salary
    public static List<Employee> sortBySalary(List<Employee> employees) {
        return employees.stream()
            .sorted((e1, e2) -> Double.compare(e1.getSalary(), e2.getSalary()))
            .collect(Collectors.toList());
    }
}
```

### Part B: Student.java
```java
public class Student {
    private int id;
    private String name;
    private double marks;
    private String subject;
    
    // Constructor, getters, setters, toString()
}
```

### Part B: StudentFilteringService.java
```java
public class StudentFilteringService {
    
    public static List<Student> filterAndSort(List<Student> students) {
        return students.stream()
            .filter(s -> s.getMarks() > 75)
            .sorted((s1, s2) -> Double.compare(s2.getMarks(), s1.getMarks()))
            .collect(Collectors.toList());
    }
    
    public static List<String> getStudentNames(List<Student> students) {
        return filterAndSort(students).stream()
            .map(Student::getName)
            .collect(Collectors.toList());
    }
}
```

### Part C: Product.java
```java
public class Product {
    private int id;
    private String name;
    private String category;
    private double price;
    private int quantity;
    
    // Constructor, getters, setters, toString()
}
```

### Part C: ProductStreamService.java
```java
public class ProductStreamService {
    
    public static Map<String, List<Product>> groupByCategory(List<Product> products) {
        return products.stream()
            .collect(Collectors.groupingBy(Product::getCategory));
    }
    
    public static Map<String, Double> averagePriceByCategory(List<Product> products) {
        return products.stream()
            .collect(Collectors.groupingBy(
                Product::getCategory,
                Collectors.averagingDouble(Product::getPrice)
            ));
    }
    
    public static Product findMaxPricedProduct(List<Product> products) {
        return products.stream()
            .max(Comparator.comparingDouble(Product::getPrice))
            .orElse(null);
    }
}
```

## 🔧 Development Workflow

1. **Clone the repository**
2. **Read the README and understand the objectives**
3. **Create POJOs** (Employee, Student, Product) with appropriate fields
4. **Implement service classes** with lambda and stream operations
5. **Create demo classes** to test and display results
6. **Run and verify** the output
7. **Experiment** with different sorting/filtering criteria

## 📖 Learning Resources

### Java Lambda Expressions
- [Oracle - Lambda Expressions](https://docs.oracle.com/javase/tutorial/java/javaOO/lambdaexpressions.html)
- [Java Lambda Tutorial](https://www.javatpoint.com/java-lambda-expressions)

### Stream API
- [Oracle - Streams](https://docs.oracle.com/javase/tutorial/collections/streams/)
- [Stream Operations Guide](https://www.geeksforgeeks.org/stream-in-java/)

### Comparators
- [Comparator Interface Documentation](https://docs.oracle.com/javase/10/docs/api/java/util/Comparator.html)

## 📋 Expected Output Examples

### Part A Output
```
=== Employees Sorted by Name ===
Employee{id=3, name='Alice', age=28, salary=55000.0}
Employee{id=1, name='Bob', age=35, salary=65000.0}
Employee{id=2, name='Charlie', age=30, salary=60000.0}

=== Employees Sorted by Salary (Descending) ===
Employee{id=1, name='Bob', age=35, salary=65000.0}
Employee{id=2, name='Charlie', age=30, salary=60000.0}
Employee{id=3, name='Alice', age=28, salary=55000.0}
```

### Part B Output
```
=== Students with Marks > 75% (Sorted by Marks) ===
Student{id=1, name='John', marks=92.5, subject='Math'}
Student{id=3, name='Sarah', marks=88.0, subject='Science'}
Student{id=4, name='Mike', marks=76.5, subject='English'}

Student Names: [John, Sarah, Mike]
```

### Part C Output
```
=== Products Grouped by Category ===
Electronics: [Product1, Product2]
Furniture: [Product3, Product4]
Clothing: [Product5]

=== Average Price by Category ===
Electronics: 15000.00
Furniture: 5000.00
Clothing: 2500.00
```

## 🤝 Contributing

Contributions are welcome! Please follow these steps:
1. Fork the repository
2. Create a new branch (`git checkout -b feature/your-feature`)
3. Commit your changes (`git commit -m 'Add your feature'`)
4. Push to the branch (`git push origin feature/your-feature`)
5. Open a Pull Request

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

MIT License permits:
- ✅ Commercial use
- ✅ Modification
- ✅ Distribution
- ✅ Private use

With conditions:
- ⚠️ License and copyright notice required

## 👨‍💻 Author

**Akash Sinha Mahapatra**
- GitHub: [@akashsinhamahapatra78-cmd](https://github.com/akashsinhamahapatra78-cmd)

## 📞 Support

If you encounter any issues:
1. Check existing GitHub issues
2. Create a new issue with detailed description
3. Include Java version, IDE, and error messages

## 🎓 Educational Purpose

This project is designed for:
- Java students learning functional programming
- Developers transitioning from procedural to functional paradigms
- Interview preparation for Java developers
- Understanding modern Java stream operations

---

**Happy Coding! 🚀 Learn functional programming with Java Streams and Lambda Expressions.**
