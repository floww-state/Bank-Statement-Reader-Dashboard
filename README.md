# Changelog
- [X] Upgraded code logic to make algorithm template-independent
- [X] Transaction date identification criteria optimized to handle multiple date formats
- [ ] Robust Power BI dashboard to track expences, patterns, and analyze spend behaviour


# Install required packages
```bash
pip install pdfplumber pandas
```

# Execute algorithm
1. Download repository in local system
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
7. Provide PDF password (if any), else pass None. 2nd argument of function "etl"
```python
dfs = [etl(file_path, None, possible_date_formats) for file_path in file_paths] # Executes all the required functions to get data from PDF to padnas DF
```
8. Pass bank name and output path
```python
bank_name = 'ICICI' # Pass bank name
output_path = r'D:\work\code_and_stuff\git_repos\bank_statement_parser\Bank-Statement-Reader-Dashboard\2_output'
```
9. **That's all! Run Jupyter NB**

# Sample output
| raw_data                                                                            | is_credit | date      | amount | comments                                                                            | bank  | source                                                                                                         |
|-------------------------------------------------------------------------------------|-----------|-----------|--------|-------------------------------------------------------------------------------------|-------|----------------------------------------------------------------------------------------------------------------|
| 29-apr-23 74332743120311966715554 swiggy   bangalore in 0.00 409.00                 | 0         | 29-Apr-23 | 409    |    apr                            swiggy bangalore   in                             | ICICI | D:\work\code_and_stuff\git_repos\bank_statement_parser\Bank-Statement-Reader-Dashboard\1_data\icici_statements |
| 29-apr-23 74766513119316728661926 amazon   http://www.am in 0.00 -799.00            | 0         | 29-Apr-23 | -799   |    apr                            amazon http   www am in                           | ICICI | D:\work\code_and_stuff\git_repos\bank_statement_parser\Bank-Statement-Reader-Dashboard\1_data\icici_statements |
| 29-apr-23 74766513119316720254589 amazon   http://www.am in 0.00 -694.00            | 0         | 29-Apr-23 | -694   |    apr                            amazon http   www am in                           | ICICI | D:\work\code_and_stuff\git_repos\bank_statement_parser\Bank-Statement-Reader-Dashboard\1_data\icici_statements |
| 29-apr-23 74056633120311949501615   paytm_innovativeretail bangalore in 0.00 239.26 | 0         | 29-Apr-23 | 239.26 |    apr                            paytm   innovativeretail bangalore in             | ICICI | D:\work\code_and_stuff\git_repos\bank_statement_parser\Bank-Statement-Reader-Dashboard\1_data\icici_statements |
| 29-apr-23 74332743120311948750760 bisleri   international mumbai in 0.00 180.00     | 0         | 29-Apr-23 | 180    |    apr                            bisleri   international mumbai in                 | ICICI | D:\work\code_and_stuff\git_repos\bank_statement_parser\Bank-Statement-Reader-Dashboard\1_data\icici_statements |
