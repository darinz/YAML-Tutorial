
---

# YAML Tutorials

This repository contains step-by-step tutorials on how to use YAML with Python. It covers creating YAML files, writing and reading multiple YAML documents, and using PyYAML in Python.

## Table of Contents

- [Introduction](#introduction)
- [Prerequisites](#prerequisites)
- [Tutorials](#tutorials)
  - [Basic YAML Syntax](#basic-yaml-syntax)
  - [Creating a YAML File](#creating-a-yaml-file)
  - [Reading YAML Files in Python](#reading-yaml-files-in-python)
  - [Writing YAML Files in Python](#writing-yaml-files-in-python)
  - [Handling Multiple YAML Documents in a Single File](#handling-multiple-yaml-documents-in-a-single-file)
- [Examples](#examples)
- [License](#license)

## Introduction

YAML (YAML Ain't Markup Language) is a human-readable data serialization standard commonly used for configuration files. This repository provides comprehensive tutorials on working with YAML files, including how to handle multiple YAML documents in a single file.

## Prerequisites

- Python installed on your machine
- PyYAML library installed (`pip install pyyaml`)
- A text editor (VS Code, Sublime Text, Notepad++, Atom, etc.)

## Tutorials

### Basic YAML Syntax

YAML uses indentation to represent structure. Key-value pairs, lists, and nested structures are fundamental elements. Here’s an example:

```yaml
person:
  name: John Doe
  age: 30
  address:
    street: 123 Main St
    city: Anytown
    state: CA
  hobbies:
    - reading
    - cycling
    - hiking
```

### Creating a YAML File

1. Open your text editor.
2. Create a new file.
3. Save the file with a `.yaml` or `.yml` extension, e.g., `config.yaml`.
4. Write your YAML content.

### Reading YAML Files in Python

```python
import yaml

with open('config.yaml', 'r') as file:
    config = yaml.safe_load(file)

print(config)
```

### Writing YAML Files in Python

```python
import yaml

data = {
    'database': {
        'host': 'localhost',
        'port': 5432,

    },
    'settings': {
        'debug': True,
        'log_level': 'info'
    }
}

with open('output.yaml', 'w') as file:
    yaml.dump(data, file)
```

### Handling Multiple YAML Documents in a Single File

YAML supports multiple documents separated by `---`.

#### Example of Multiple Documents

```yaml
# multiple_docs.yaml

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

#### Reading Multiple Documents in Python

```python
import yaml

with open('multiple_docs.yaml', 'r') as file:
    documents = list(yaml.safe_load_all(file))

database_config = documents[0]
settings_config = documents[1]
users_config = documents[2]

print("Database Configuration:", database_config)
print("Settings Configuration:", settings_config)
print("Users Configuration:", users_config)
```

#### Writing Multiple Documents in Python

```python
import yaml

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

documents = [database_config, settings_config, users_config]

with open('multiple_docs_output.yaml', 'w') as file:
    yaml.dump_all(documents, file)
```