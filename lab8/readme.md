# JSON

## JSON built-in package
```
import json
```
## Creating and writing to JSON file
```
with open("data_file.json", "w") as write_file:
    json.dump(data, write_file)
```
## Writing serialized JSON to String file
```
json_string = json.dumps(data)
```
## Deserializing JSON types to python

| JSON type   | Python type |
| ------------|:-----------:|
| object      |  dict       |
| array       | list        |
| string      | str         |
| number(int) | int         |
| number(real)| float       |
| true        | True        |
| false       | false       |
| null        | none        |

## Deserializing JSON
```
with open("data_file.json", "r") as read_file:
    data = json.load(read_file)
```
## Complex numbers JSON Encoder
```
class ComplexEncoder(json.JSONEncoder):
    def default(self, z):
        if isinstance(z, complex):
            return (z.real, z.imag)
        else:
            return super().default(z)
```

# CSV
## What is CSV file?

A CSV file (Comma Separated Values file) is a type of plain text file that uses specific structuring to arrange tabular data. Because it’s a plain text file, it can contain only actual text data—in other words, printable ASCII or Unicode characters.

The structure of a CSV file is given away by its name. Normally, CSV files use a comma to separate each specific data value. Here’s what that structure looks like:
```
column 1 name,column 2 name, column 3 name
first row data 1,first row data 2,first row data 3
second row data 1,second row data 2,second row data 3
```
## Parsing CSV with Python's built-in CSV library.
```
import csv

with open('employee_birthday.txt') as csv_file:
    csv_reader = csv.reader(csv_file, delimiter=',')
    line_count = 0
    for row in csv_reader:
        if line_count == 0:
            print(f'Column names are {", ".join(row)}')
            line_count += 1
        else:
            print(f'\t{row[0]} works in the {row[1]} department, and was born in {row[2]}.')
            line_count += 1
    print(f'Processed {line_count} lines.')
```
## Reading CSV files into a dictionary with csv
```
import csv

with open('employee_birthday.txt', mode='r') as csv_file:
    csv_reader = csv.DictReader(csv_file)
    line_count = 0
    for row in csv_reader:
        if line_count == 0:
            print(f'Column names are {", ".join(row)}')
            line_count += 1
        print(f'\t{row["name"]} works in the {row["department"]} department, and was born in {row["birthday month"]}.')
        line_count += 1
    print(f'Processed {line_count} lines.')
```
## Writing CSV files with csv
```
with open('employee_file.csv', mode='w') as employee_file:
    employee_writer = csv.writer(employee_file, delimiter=',', quotechar='"', quoting=csv.QUOTE_MINIMAL)

    employee_writer.writerow(['John Smith', 'Accounting', 'November'])
    employee_writer.writerow(['Erica Meyers', 'IT', 'March'])
```
## Reading CSV files with pandas
```
import pandas
df = pandas.read_csv('hrdata.csv')
print(df)
```
## Writing CSV files with pandas
```
import pandas
df = pandas.read_csv('hrdata.csv', 
            index_col='Employee', 
            parse_dates=['Hired'],
            header=0, 
            names=['Employee', 'Hired', 'Salary', 'Sick Days'])
df.to_csv('hrdata_modified.csv')
```
