**Report on Splitting a Large CSV File Using Python**

## 1. **Introduction**
This report details the Python script designed to split a large CSV file into multiple smaller CSV files based on a defined chunk size. The script utilizes the Pandas library for data handling, ensuring efficient processing of large datasets.

## 2. **Libraries Used**
- `pandas`: For reading and writing CSV files efficiently.

## 3. **Implementation Details**
The script defines a function to automate the splitting process:

### **Function: `split_large_csv(input_csv, chunk_size)`**
This function performs the following steps:
1. **Read the CSV in chunks**: Uses `pd.read_csv()` with the `chunksize` parameter to process large files efficiently.
2. **Iterate through chunks**: Loops through each chunk, creating separate smaller CSV files.
3. **Generate output filenames**: Appends an index to create unique filenames for each part.
4. **Save each chunk**: Writes the split data into separate CSV files without indexes.
5. **Print confirmation**: Outputs a message for each created file.

#### **Code Implementation**
```python
import pandas as pd

def split_large_csv(input_csv, chunk_size):
    for i, chunk in enumerate(pd.read_csv(input_csv, chunksize=chunk_size)):
        output_csv = f"output_part_{i+1}.csv"
        chunk.to_csv(output_csv, index=False)
        print(f"Created {output_csv}")
```

## 4. **Usage Example**
To execute the script, specify the input CSV file and chunk size:
```python
# Usage Example
split_large_csv("wealth_management_9L_rows.csv", 50000)  # Splits into chunks of 50,000 rows each
```

## 5. **Key Features & Benefits**
- **Memory Efficiency**: Reads large files in chunks, reducing memory consumption.
- **Automated Splitting**: No manual intervention needed for processing large files.
- **Customizable Chunk Size**: Allows users to define the size of each smaller file.
- **Fast Processing**: Uses Pandas for optimized data handling.

## 6. **Potential Enhancements**
- **Custom Output Directory**: Allow users to specify a folder for storing split files.
- **Progress Indicator**: Show progress while processing large files.
- **Error Handling**: Handle missing files and permission errors gracefully.
- **Header Retention**: Ensure the header is included in each split file for easier readability.

## 7. **Conclusion**
This script provides a simple and efficient way to split large CSV files into smaller, manageable parts. Future improvements can enhance usability by adding logging, progress tracking, and error handling.
