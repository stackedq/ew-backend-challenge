## Required Tech Stack

Following packages are mandatory to use in this challenge:

- Python 3.6+
- Virtualenv
- Django
- Django-rest-framework
- Posgresql
- git

Feel free to use any other open-source packages.

---

# Challenge

Make sure to clone this repository as using git is a part of challenge.

Use `Posgresql` for the database engine.

The challenge goes in different parts as stated in following:

### Data app

Create a django app called `data`.

Create following models for `data` app:

- DataModel with these fields:
  - type: Enum with values of `select` and `range`
  - name: String

* DataOption with these fields:
  - data: relation to a `DataModel` instance
  - name: String

- DataValue with these fields:
  - selected_option: nullable relation to a `DataOption` instance
  - value: nullable float number

> GOAL: basic usage of Django and database models.

### Data entry

Create the following model instances:
either create a `Postman` collection or use database seeders (the latter one has a bonus).

- `DataModel`, type: "range", name: "data1"
- `DataModel`, type: "range", name: "data2"
- `DataModel`, type: "select", name: "data3"
- `DataModel`, type: "range", name: "data4"

- `DataOption`, data: [id of `DataModel` instance with the name of "data3"], name: "option1"
- `DataOption`, data: [id of `DataModel` instance with the name of "data3"], name: "option2"

> GOAL: Database management

### Data app serializers, views, urls

Create `DRF` serializers for the `Data` app models.

Create `DRF` views for the `Data` app models.

Make views accessible by defining corresponding urls.

> GOAL: basic usage of DRF and routing standards.

### Two Custom views for handling two special requests

#### Bulk-upload

There should be a special url with the path `/api/data/bulk-upload/` which could handle the following request:

- Request method must be `POST`
- Request body should be the following `Application/json`:
  ```json
  [
    {
      "name": "data1",
      "value": 100
    },
    {
      "name": "data2",
      "value": 200
    },
    {
      "name": "data1",
      "value": 120
    },
    {
      "name": "data3",
      "value": "option1"
    },
    {
      "name": "data3",
      "value": "option2"
    },
    {
      "name": "data4",
      "value": 400.23
    }
  ]
  ```

The view must create a `DataValue` instance for each element in this json.

> NOTE: This view must handle these exceptions:

- A `DataModel` named "something" doesn't exist.
- A `DataOption` named "something" doesn't exist.

#### Bulk upload simple

There should be a special url with the path `/api/data/bulk-upload-simple/` which could handle the following request:

- Request method must be `POST`
- Request body should be the following `Application/json`:
  ```json
  {
    "data1": 100,
    "data2": 200,
    "data3": "option1",
    "data4": 400.23
  }
  ```

The view must create a `DataValue` instance for each key-value pair in this json object.

> NOTE: This view must handle these exceptions:

- A `DataModel` named "something" doesn't exist.
- A `DataOption` named "something" doesn't exist.

> GOAL: usage of python algorithms.

---

## Challenge Notes

Additional notes:

- At least one model, one view and one serializer must have documentation.
- Readable codes are a plus.
- Logical comments are a plus but not required in this challenge.

---

## Available Scripts

In the project directory, you can run:

### `./manage.py runserver`

For starting the app

### `./manage.py makemigrations`

For creating automatically generated migration files

### `./manage.py migrate`

For applying migrations

Good luck
