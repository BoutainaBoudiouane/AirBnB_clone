# HBnB

A command interpreter to manage your AirBnB objects.

## Description

AirBnB is a complete web application, integrating database storage,
a back-end API, and front-end interfacing in a clone of AirBnB.

## Console

The console is a command line interpreter that permits management of the backend of AirBnB. It can be used to handle and manipulate all classes utilized by the application.

### Using the Console

The AirBnB console can be run both interactively and non-interactively.
To run the console in non-interactive mode, pipe any command(s) into an execution of the file `console.py` at the command line.

```bash
$ echo "help" | ./console.py
(hbnb)
Documented commands (type help <topic>):
========================================
EOF  all  count  create  destroy  help  quit  show  update

(hbnb)
$
```

Alternatively, to use the AirBnB console in interactive mode, run the
file `console.py` by itself:

```bash
$ ./console.py
```

While running in interactive mode, the console displays a prompt for input:

```bash
$ ./console.py
(hbnb)
```

To quit the console, enter the command `quit`, or input an EOF signal
(`ctrl-D`).

```bash
$ ./console.py
(hbnb) quit
$
```

```bash
$ ./console.py
(hbnb) EOF
$
```

### Console Commands

The AirBnB console supports the following commands:

* **create**
  * Usage: `create <class>`

Creates a new instance of a given class. The class' ID is printed and
the instance is saved to the file `file.json`.

```bash
$ ./console.py
(hbnb) create BaseModel
0d27c34a-5f4a-42e2-bd0c-3eab8a7076c8
(hbnb) quit
$ cat file.json ; echo ""
{"BaseModel.0d27c34a-5f4a-42e2-bd0c-3eab8a7076c8": {"id": "0d27c34a-5f4a-42e2-bd0c-3eab8a7076c8", "created_at": "2024-11-10T09:23:45.123456",
"updated_at": "2024-11-10T09:23:45.123457", "__class__": "BaseModel"}}

```

* **show**
  * Usage: `show <class> <id>` or `<class>.show(<id>)`

Prints the string representation of a class instance based on a given id.

```bash
$ ./console.py
(hbnb) create User
a12345f7-98d4-4fcd-940f-1a2b3c4d5efg
(hbnb)
(hbnb) show User a12345f7-98d4-4fcd-940f-1a2b3c4d5efg
[User] (a12345f7-98d4-4fcd-940f-1a2b3c4d5efg) {'id': 'a12345f7-98d4-4fcd-940f-1a2b3c4d5efg', 'created_at': datetime.datetime(2024, 4, 10, 15, 45, 12, 123456), 
'updated_at': datetime.datetime(2024, 4, 10, 15, 45, 12, 123457)}
(hbnb)
(hbnb) User.show(a12345f7-98d4-4fcd-940f-1a2b3c4d5efg)
[User] (a12345f7-98d4-4fcd-940f-1a2b3c4d5efg) {'id': 'a12345f7-98d4-4fcd-940f-1a2b3c4d5efg', 'created_at': datetime.datetime(2024, 4, 10, 15, 45, 12, 123456), 
'updated_at': datetime.datetime(2024, 4, 10, 15, 45, 12, 123457)}
(hbnb)
```

* **destroy**
  * Usage: `destroy <class> <id>` or `<class>.destroy(<id>)`

Deletes a class instance based on a given id. The storage file `file.json`
is updated accordingly.

```bash
$ ./console.py
(hbnb) create State
b49e2041-55f8-4d85-aaa4-81e13f2c8cab
(hbnb) create Place
3e16f473-b785-4c6b-9b48-b7d01a0d2e8f
(hbnb)
(hbnb) destroy State b49e2041-55f8-4d85-aaa4-81e13f2c8cab
(hbnb) Place.destroy(3e16f473-b785-4c6b-9b48-b7d01a0d2e8f)
(hbnb) quit
$ cat file.json ; echo ""
{}
```

* **all**
  * Usage: `all` or `all <class>` or `<class>.all()`

Prints the string representations of all instances of a given class. If no
class name is provided, the command prints all instances of every class.

```bash
$ ./console.py
(hbnb) create BaseModel
a1b2c3d4-e5f6-7g8h-9i0j-klmno1pqrstu
(hbnb) create BaseModel
b1c2d3e4-f5g6-h7i8-j9k0-lmnopqrstuvw
(hbnb) create User
f1e2d3c4-b5a6-7d8e-9f0g-hijklm1n2o3p
(hbnb) create User
m1n2o3p4-q5r6-s7t8-u9v0-wx1yzabcd234
(hbnb)
(hbnb) all BaseModel
["[BaseModel] (a1b2c3d4-e5f6-7g8h-9i0j-klmno1pqrstu) {'id': 'a1b2c3d4-e5f6-7g8h-9i0j-klmno1pqrstu', 'created_at': datetime.datetime(2024, 3, 8, 9, 47, 39, 778364), 
'updated_at': datetime.datetime(2024, 3, 8, 9, 47, 39, 778374)}",
"[BaseModel] (b1c2d3e4-f5g6-h7i8-j9k0-lmnopqrstuvw) {'id': 'b1c2d3e4-f5g6-h7i8-j9k0-lmnopqrstuvw', 'created_at': datetime.datetime(2024, 3, 8, 12, 13, 6, 605601), 
'updated_at': datetime.datetime(2024, 3, 8, 12, 13, 6, 605608)}"]
(hbnb)
(hbnb) User.all()
["[User] (f1e2d3c4-b5a6-7d8e-9f0g-hijklm1n2o3p) {'id': 'f1e2d3c4-b5a6-7d8e-9f0g-hijklm1n2o3p', 'created_at': datetime.datetime(2024, 3, 8, 12, 29, 30, 254591), 
'updated_at': datetime.datetime(2024, 3, 8, 12, 29, 30, 254599)}",
"[User] (m1n2o3p4-q5r6-s7t8-u9v0-wx1yzabcd234) {'id': 'm1n2o3p4-q5r6-s7t8-u9v0-wx1yzabcd234', 'created_at': datetime.datetime(2024, 3, 8, 12, 54, 58, 121355), 
'updated_at': datetime.datetime(2024, 3, 8, 12, 54, 58, 121363)}"]
(hbnb)
(hbnb) all
["[BaseModel] (a1b2c3d4-e5f6-7g8h-9i0j-klmno1pqrstu) {'id': 'a1b2c3d4-e5f6-7g8h-9i0j-klmno1pqrstu', 'created_at': datetime.datetime(2024, 3, 8, 9, 47, 39, 778364), 
'updated_at': datetime.datetime(2024, 3, 8, 9, 47, 39, 778374)}",
"[BaseModel] (b1c2d3e4-f5g6-h7i8-j9k0-lmnopqrstuvw) {'id': 'b1c2d3e4-f5g6-h7i8-j9k0-lmnopqrstuvw', 'created_at': datetime.datetime(2024, 3, 8, 12, 13, 6, 605601), 
'updated_at': datetime.datetime(2024, 3, 8, 12, 13, 6, 605608)}",
"[User] (f1e2d3c4-b5a6-7d8e-9f0g-hijklm1n2o3p) {'id': 'f1e2d3c4-b5a6-7d8e-9f0g-hijklm1n2o3p', 'created_at': datetime.datetime(2024, 3, 8, 12, 29, 30, 254591), 
'updated_at': datetime.datetime(2024, 3, 8, 12, 29, 30, 254599)}",
"[User] (m1n2o3p4-q5r6-s7t8-u9v0-wx1yzabcd234) {'id': 'm1n2o3p4-q5r6-s7t8-u9v0-wx1yzabcd234', 'created_at': datetime.datetime(2024, 3, 8, 12, 54, 58, 121355), 
'updated_at': datetime.datetime(2024, 3, 8, 12, 54, 58, 121363)}"]
(hbnb)
```

* **count**
  * Usage: `count <class>` or `<class>.count()`

Retrieves the number of instances of a given class.

```bash
$ ./console.py
(hbnb) create Place
c24174ab-3310-49ac-b6d4-13f1e6b3ccb5
(hbnb) create Place
c6ad2490-c925-441f-b118-cb80863333e3
(hbnb) create City
caec6947-ae3e-4dca-a4ca-38cda4221e86
(hbnb)
(hbnb) count Place
2
(hbnb) City.count()
1
(hbnb)
```

* **update**
  * Usage: `update <class> <id> <attribute name> "<attribute value>"` or
`<class>.update(<id>, <attribute name>, <attribute value>)` or `<class>.update(<id>, <attribute dictionary>)`.

Updates a class instance based on a given id with a given key/value attribute
pair or dictionary of attribute pairs. If `update` is called with a single
key/value attribute pair, only "simple" attributes can be updated (ie. not
`id`, `created_at`, and `updated_at`). However, any attribute can be updated by
providing a dictionary.

```bash
$ ./console.py
(hbnb) create User
9a12d832-4d1b-4329-bbb4-dad6f56c276d
(hbnb)
(hbnb) update User 9a12d832-4d1b-4329-bbb4-dad6f56c276d first_name "Jane"
(hbnb) show User 9a12d832-4d1b-4329-bbb4-dad6f56c276d
[User] (9a12d832-4d1b-4329-bbb4-dad6f56c276d) {'id': '9a12d832-4d1b-4329-bbb4-dad6f56c276d', 'created_at': datetime.datetime(2024, 5, 1, 9, 10, 22, 456789), 'updated_at': datetime.datetime(2024, 5, 1, 9, 10, 22, 456795), 'first_name': 'Jane'}
(hbnb)
(hbnb) update User 9a12d832-4d1b-4329-bbb4-dad6f56c276d last_name "Smith"
(hbnb) show User 9a12d832-4d1b-4329-bbb4-dad6f56c276d
[User] (9a12d832-4d1b-4329-bbb4-dad6f56c276d) {'id': '9a12d832-4d1b-4329-bbb4-dad6f56c276d', 'created_at': datetime.datetime(2024, 5, 1, 9, 10, 22, 456789), 'updated_at': datetime.datetime(2024, 5, 1, 9, 15, 12, 123456), 'first_name': 'Jane', 'last_name': 'Smith'}
(hbnb)
```

## Testing

Unittests for the AirBnB project are defined in the [tests](./tests)
folder. To run the entire test suite simultaneously, execute the following command:

```bash
$ python3 unittest -m discover tests
```

Alternatively, you can specify a single test file to run at a time:

```bash
$ python3 -m unittest tests/test_console.py
```
