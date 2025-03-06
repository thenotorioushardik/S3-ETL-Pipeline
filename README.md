# S3 ETL Pipeline

## Overview

This code provides a **versatile** ETL pipeline for interacting with AWS S3 using Python. It supports efficient file handling, including:

- **Extraction**: Listing and reading files (CSV, TSV, Excel) from an S3 bucket.
- **Transformation**: Processing data with inferred types using Dask for scalability. Dask enables parallel computing and lazy evaluation to efficiently handle large datasets.
- **Loading**: Uploading processed files back to S3 and managing folders.

## Features

✅ **Multi-format support**: Read CSV, TSV, and Excel files dynamically.\
✅ **Scalable data processing**: Leverages **Dask** for large dataset handling.\
✅ **Automated S3 management**: Easily list, upload, and delete files and folders.\
✅ **Secure credentials handling**: Configure authentication securely to avoid exposure.\
✅ **Cleanup utilities**: Delete folders and files programmatically.\
✅ **Parallel processing**: Efficiently processes files by inferring and applying correct data types.

## Setup

### Prerequisites

Ensure you have the following installed:

- Python 3.7+
- `boto3`, `dask`, `pandas`, `s3fs`

Install dependencies using:

```sh
pip install boto3 dask pandas s3fs
```

### AWS Credentials

Configure your AWS credentials securely using environment variables or `~/.aws/credentials` instead of hardcoding them.

```sh
export AWS_ACCESS_KEY_ID="your-access-key"
export AWS_SECRET_ACCESS_KEY="your-secret-key"
```

## Usage

### 1️⃣ List Folder Contents in S3

```python
folder_contents_df = list_folder_contents(bucket_name, folder_path)
print(folder_contents_df)
```

**Example Output:**

```
                File Name  Size (Bytes)
0  DAX-6871/data.csv         12456
1  DAX-6871/report.xlsx      34200
```

### 2️⃣ Read a File from S3

```python
s3_file_df = read_s3_file(bucket_name, s3_file_path)
s3_file_df.head()
```

### 3️⃣ Upload a File to S3

```python
upload_file(bucket_name, folder_path, local_file_path)
```

### 4️⃣ Delete a Folder from S3

```python
delete_folder(bucket_name, folder_path)
```

## Performance Considerations

- **Dask is used** to handle large datasets efficiently by distributing computations across multiple cores.
- **Parallel processing** speeds up file operations significantly.
- **Lazy evaluation** reduces memory usage by computing transformations only when needed.

## Best Practices

🔹 **Avoid hardcoding credentials** – use AWS IAM roles or environment variables.\
🔹 **Optimise large file processing** – leverage `Dask` for distributed computing.\
🔹 **Use logging and error handling** – implement robust error recovery to prevent failures.\
🔹 **Enable retry mechanisms** – ensure resilience in case of transient failures in S3 operations.

## Contributing

Contributions are welcome! Feel free to submit issues or pull requests.

---

🚀 **Designed for Data Engineers & Scientists handling S3-based ETL workflows.**
