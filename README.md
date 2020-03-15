# python-validate-json-schema

## Validate JSON Schema using Python

This is a helper project for JSON Schema validation in Pyhton, which uses `Jsonschema` the most complete and compliant JSON Schema validator.

# Aim of the application

- Validate the necessary fields present in JSON file
- Validate JSON Field type. We need data of a JSON filed in a type that we want. For example, we want all numeric fields in the number format instead of number encoded in a string format like this `Marks: "75"` so we can use it directly instead of checking and converting it every time.
- To learn the implementation of `Jsonschema` in python.
- To implement,JSON Conversion to Python Object using `json.load` or `json.loads` methods.

## JSON Schema

JSON Schema is a specification for JSON based format for defining the structure of JSON data. It was written under IETF draft which expired in 2011. JSON Schema.

- Describes your existing data format.
- Clear, human- and machine-readable documentation.
- Complete structural validation, useful for automated testing.
- Complete structural validation, validating client-submitted data.

Currently the most complete and compliant JSON Schema validator available for python is `Jsonschema`.

Given below is a basic JSON schema, which covers a basic user details.

```json
{
   "$schema": "http://json-schema.org/draft-04/schema#",
   "title": "User",
   "description": "A user request json",
   "type": "object",
   "properties": {
      "id": {
         "description": "The unique identifier for a user",
         "type": "integer"
      },
      "name": {
         "description": "Name of the user",
         "type": "string"
      },
      "contact_number": {
         "type": "number",
      }
   },
   "required": ["id", "name", "contact_number"]
}
```

`jsonschema` is an implementation of [JSON Schema](https://json-schema.org/) for Python. Using `jsonschema`, we can create a schema of our choice, so every time we can validate the JSON document against this schema, if it passed, we could say that the JSON document is valid.

Keyword | Description |
--- | --- |
$schema | The $schema keyword states that this schema is written according to the draft v4 specification. |
title | You will use this to give a title to your schema. |
description | A little description of the schema. |
type | The type keyword defines the first constraint on our JSON data: it has to be a JSON Object. |
properties | Defines various keys and their value types, minimum and maximum values to be used in JSON file. |
required | This keeps a list of required properties. |
minimum | This is the constraint to be put on the value and represents minimum acceptable value. |
exclusiveMinimum | If "exclusiveMinimum" is present and has boolean value true, the instance is valid if it is strictly greater than the value of "minimum". |
maximum | This is the constraint to be put on the value and represents maximum acceptable value. |
exclusiveMaximum | If "exclusiveMaximum" is present and has boolean value true, the instance is valid if it is strictly lower than the value of "maximum". |
multipleOf | A numeric instance is valid against "multipleOf" if the result of the division of the instance by this keyword's value is an integer. |
maxLength | The length of a string instance is defined as the maximum number of its characters. |
minLength | The length of a string instance is defined as the minimum number of its characters. |
pattern | A string instance is considered valid if the regular expression matches the instance successfully. |

You can check a [http://json-schema.org](http://json-schema.org) for the complete list of keywords that can be used in defining a JSON schema. The above schema can be used to test the validity of the following JSON code 

## How to Run the application

First, install `jsonschema` using pip command.

```pip
pip install jsonschema
```

Run the following, will validate the given json input against `user_schema.json`

```cmd
python json_validate.py 
```

Input Json
```json
{"id" : 10,"name": "DonOfDen","contact_number":1234567890}
```

## Testing

Lets test with alternative json input, If you check `json_validate.py` The `validate()` method will raise an exception if given JSON is not what is described in the schema.

```json
{"id" : "10","name": "DonOfDen","contact_number":1234567890}
```
In the above input json we have modified `"id" : 10` from integer to `"id" : "10"` string.

```txt
'10' is not of type 'integer'

Failed validating 'type' in schema['properties']['id']:
    {'description': 'The unique identifier for a user', 'type': 'integer'}

On instance['id']:
    '10'
Given JSON data is InValid

```

### Reference:

- https://json-schema.org/
- https://pynative.com/python-json-validation/
- https://www.tutorialspoint.com/json/json_schema.htm
- https://github.com/Julian/jsonschema
