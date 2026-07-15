# C++ CSV Reader 📊

A lightweight, flexible, and easy-to-use C++ library designed for parsing and managing CSV files. It allows you to read entire files, specific rows, or custom ranges into memory efficiently.

## 🚀 Features

* **Flexible Reading Options:** Load the entire file, a specific row, or a designated range of rows.
* **Column-Based Operations:** Read only the categories (columns) you need, or a specific range within those columns, to optimize memory usage.
* **Safe Data Retrieval:** Retrieve values as strings (`std::string`) or numeric values (`long double`) with built-in error handling. If a conversion fails, the library prints an error message and returns `0` instead of crashing.
* **Memory Management:** Easily clear all stored values and free up memory using the `freeMemory()` method.

## 💻 Usage

Integrating the library into your project is straightforward. Just include `readCSV.hpp` and `readCSV.cpp` in your project directory and compile them with your main program.

```cpp
#include <iostream>
#include "readCSV.hpp"

int main() {
    // 1. Initialize the dataset and parse headers (categories)
    DataSet myData("data.csv");

    // 2. Load the CSV content (or specific sections) into memory
    myData.readCSV(); 

    // 3. Retrieve values safely
    std::string name = myData.getValueStr("Name", 2);
    long double salary = myData.getValueNum("Salary", 2);

    std::cout << "Employee: " << name << " - Salary: " << salary << std::endl;

    // 4. Free up memory when done
    myData.freeMemory();

    return 0;
}
```
## 🛠️ API Reference
| Method | Description |
| :--- | :--- |
| `DataSet(const char* fileName)` | Constructor. Opens the file and initializes categories. |
| `readCSV()` | Reads and parses the entire CSV file. |
| `readCSVinRange(int begin, int end)` | Reads and parses a specific range of rows. |
| `readCSVRow(int row)` | Reads and parses a single row. |
| `readCSVCategory(std::string category)` | Reads and parses a single category (column). |
| `readCSVCategoryinRange(...)` | Reads and parses a specific row range within a category. |
| `readCSVCategoryinRow(...)` | Reads and parses a single row within a category. |
| `getValueNum(category, row)` | Retrieves a parsed value as a numeric (`long double`) type. |
| `getValueStr(category, row)` | Retrieves a parsed value as a string (`std::string`) type. |
| `getCategoryName(int CategoryIndex)` | Returns the name of the category at the specified index. |
| `freeMemory()` | Clears the stored values and frees up memory. |

## 📄 License
This project is licensed under the MIT License - see the LICENSE file for details.
