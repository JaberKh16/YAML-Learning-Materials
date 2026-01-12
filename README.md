# YAML (YAML Ain't Markup Language) Cheat Sheet

YAML is a human-readable data serialization language commonly used for configuration files and data exchange.

---

## 1. Basics

- YAML is indentation-sensitive (spaces only, no tabs)
- Key-value pairs: `key: value`
- Comments start with `#`

```yaml

# This is a comment
name: John Doe
age: 30


## 2. Data Types

```yaml
string: "Hello World"     # Double quotes
string2: 'Hello World'    # Single quotes
string3: Plain text       # No quotes
integer: 42
float: 3.1415
boolean: true
null_value: null


## 3. Specify Types

```yaml
    data: !!int 0

## 4. Multi-line strings
    - two ways setup:
    
    a. literal block | (preserves the line blocks)

    ```yaml
    description: |
        This is a
        multi-line
        string.

    b. folded block > (folds newlines into spaces)
    
    ```yaml
    description: >
        This is a
        multi-line
        string.


## 5. Mappings(Hashes/Objects)
    ```yaml
        fruits:
            - Apple
            - Banana
            - Orange

## 6. Nested Collections
    ```yaml
        people:
            name: John
            age: 30
            email: example@exam.com

## 7. Advance Features
    a. anchors (&) and aliases (*)
        - <<: *defaults merges the mapping from defaults
        
        ```yaml
        defaults: &defaults
            adapter: postgresql
            pool: 5

        development:
            <<: *defaults
            database: dev_db

        test:
            <<: *defaults
            database: test_db


    b. merge multiple mappings
        
        ```yaml
        base: &base
            color: red
            size: medium
        custom:
            <<: [*base]
            size: large


## 8. Multi-document Yaml
    - it uses ---
    
    ```yaml
        
    ---
    name: John
    age: 39
    ---
    app: appdata
    version: 12.1.2


## 9. Special Datatypes
    
    a. Dates 
        
        ```yaml
        birthday: 1992-01-24

    b. Timestamps
        
        ```yaml
        created_at: 2021-01-01T10:00:02Z

    c. Null
        
        ```yaml
        empty_value: null
        missing_value: ~

## 10. Strings With Special Characters
    - use quotes if string contains :, # or starts with special symbols
    - single quotes ' prevents interpolation
    - double quotes " allow escaping and interpolation

    ```yaml
    escaped: "Line 1\nLine 2"
    literal: 'This is # not a comment'

## 11. Boolean Values
    - yaml supports 3 types of expression for booleans values
    - values are: yes/no , true/false, on/off
    
    ```yaml
    is_active: on
    is_data: yes
    tranfered_data: yes


## Best Practices In Yaml
    - use 2 spaces for indentation(never tabs)
    - keep keys lowercase and hyphenated if need for two or multi words like: app-version
    - use anchors and aliases to reduce duplication
    - avoid trailing spaces
    - use quotes only when necessary
    - use comments liberally for clarity

