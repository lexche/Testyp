## Урок 3. Работа с MongoDB

В предыдущих уроках мы рассказали что такое нереляционные базы, рассказали как установить MongoDB и рассмотрели основные операции, в этом уроке расскажем про них более подробно через практику.

Cоздадим базу:

```
use yp_db
```

Создадим в этой базе 2 коллекции: students и faculties, с помощью команд:

```
db.createCollection('students', {validator: {$jsonSchema: {bsonType: 'object',required: ['ID', 'firstName', 'lastName', 'age', 'gpa'],properties: {ID: { bsonType: 'number' },firstName: { bsonType: 'string' },lastName: { bsonType: 'string' },age: { bsonType: 'number' },gpa: { bsonType: 'number' }}}}});

db.createCollection('faculties', {validator: {$jsonSchema: {bsonType: 'object',required: ['ID', 'Faculty', 'PS'],properties: {ID: { bsonType: 'number' },Faculty: { bsonType: 'string' },PS: { bsonType: 'number' }}}}});

```

