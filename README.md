# Install required packages
```bash
pip install pdfplumber pandas
```

# Execute algorithm
1. Clone repository in local system
2. Run **bank_statement_reader.ipynb**
3. Navigate to section named **Main - algorithm execution**
4. Update/add regex to match dates in your PDF dates
```python
# CONFIG: Pass additional regexes as you deem fit per your data
possible_date_formats = [r'([0-9]{2}/[0-9]{2}/[0-9]{4})', r'([0-9]{2}-[a-zA-Z]{3}-[0-9]{2})']
```
5. Pass the folder path where PDFs are located
```python
# Pass folder path here
folder_path = r'D:\work\code_and_stuff\git_repos\bank_statement_parser\Bank-Statement-Reader-Dashboard\1_data\icici_statements'
file_paths = [folder_path + '\\' + file for file in os.listdir(folder_path)]
print(f'{len(file_paths)} found in folder `{folder_path.split('\\')[-1]}`')
```
6. Pass bank name and output path
```python
bank_name = 'ICICI' # Pass bank name
output_path = r'D:\work\code_and_stuff\git_repos\bank_statement_parser\Bank-Statement-Reader-Dashboard\2_output'
```
7. **That's all! Run Jupyter NB**

# Sample output
