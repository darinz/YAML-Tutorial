Creating multiple YAML documents within a single file is straightforward. YAML supports this by allowing you to separate documents with a line containing three hyphens (`---`). Each document is treated as a standalone YAML document. Here’s a step-by-step guide to create and manage multiple YAML documents within a single file:

## Step-by-Step Guide to Creating Multiple YAML Documents in a Single File

### Step 1: Understanding Document Separation

In YAML, multiple documents within a single file are separated using `---`. Here’s an example:

```yaml
# Example of multiple YAML documents in a single file

# Document 1
---
database:
  host: localhost
  port: 5432

# Document 2
---
settings:
  debug: true
  log_level: info

# Document 3
---
users:
  - name: alice
    role: admin
  - name: bob
    role: user
  - name: charlie
    role: guest
```

### Step 2: Creating a New YAML File with Multiple Documents

1. **Open your text editor**: Launch your chosen editor.
2. **Create a new file**: Typically found under `File > New`.
3. **Save the file with a `.yaml` or `.yml` extension**: Use `Save As` and choose the extension, e.g., `multiple_docs.yaml`.

### Step 3: Writing Multiple Documents

Write your YAML content, ensuring each document is separated by `---`.

#### Example File: `multiple_docs.yaml`

```yaml
# multiple_docs.yaml

# Document 1: Database Configuration
---
database:
  host: localhost
  port: 5432

# Document 2: Application Settings
---
settings:
  debug: true
  log_level: info

# Document 3: User Information
---
users:
  - name: alice
    role: admin
  - name: bob
    role: user
  - name: charlie
    role: guest
```

### Step 4: Validating Your YAML File

Ensure your YAML is correctly formatted by using online validators like [YAML Lint](https://www.yamllint.com/) or [Code Beautify YAML Validator](https://codebeautify.org/yaml-validator). Paste your entire file content into the validator to check for errors.

### Step 5: Reading Multiple YAML Documents in Python

To read multiple documents from a single YAML file in Python, you can use the `yaml.safe_load_all` function provided by PyYAML.

#### Example Code to Read Multiple YAML Documents

```python
import yaml

# Read the YAML file containing multiple documents
with open('multiple_docs.yaml', 'r') as file:
    documents = list(yaml.safe_load_all(file))

# Access each document
database_config = documents[0]
settings_config = documents[1]
users_config = documents[2]

# Print the contents of each document
print("Database Configuration:", database_config)
print("Settings Configuration:", settings_config)
print("Users Configuration:", users_config)
```

### Explanation

- **`yaml.safe_load_all(file)`**: Loads all documents in the YAML file as an iterator. Converting it to a list allows you to access each document individually.
- **Accessing documents**: Each document can be accessed using list indexing (`documents[0]`, `documents[1]`, etc.).

### Step 6: Writing Multiple YAML Documents in Python

To write multiple documents to a single YAML file in Python, you can use the `yaml.dump_all` function.

#### Example Code to Write Multiple YAML Documents

```python
import yaml

# Define multiple documents as separate dictionaries
database_config = {
    'database': {
        'host': 'localhost',
        'port': 5432,
    }
}

settings_config = {
    'settings': {
        'debug': True,
        'log_level': 'info'
    }
}

users_config = {
    'users': [
        {'name': 'alice', 'role': 'admin'},
        {'name': 'bob', 'role': 'user'},
        {'name': 'charlie', 'role': 'guest'}
    ]
}

# List of all documents
documents = [database_config, settings_config, users_config]

# Write the documents to a YAML file
with open('multiple_docs_output.yaml', 'w') as file:
    yaml.dump_all(documents, file)
```

### Explanation

- **Define documents**: Create dictionaries for each document.
- **`yaml.dump_all(documents, file)`**: Writes all documents to the specified file, separating them with `---`.

### Conclusion

Creating multiple YAML documents within a single file is a useful feature for organizing related configurations or data. By separating documents with `---`, you can easily manage multiple YAML structures in one file. Using PyYAML, you can read and write these multi-document files in Python, making it a powerful tool for configuration management and data serialization.