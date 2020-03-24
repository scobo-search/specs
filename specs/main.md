# Main Specs

## Searching Content
This is rough idea of what developers would call to search
```php
$driverConfig = [
  'host' => 'localhost',
  'port' => 3306,
  'database' => 'scobo',
  'user' => 'scobo',
  'password' => 'scobo'
];

$options = [
    'search' => [
        'description'
    ],
    'return' => [
        'id',
        'description'
    ]
];
Scobo\Scobo::driver(Scobo\MySQLDriver($driverConfig))->index('example')->search('search query', $options);
```

In the end the developer should recieve an array:
```php
[
    [
        'id' => 1,
        'description' => 'This is a description with a search query'
    ],
    [
        'id' => 1,
        'description' => 'This is another description with the same search query'
    ]
]
```

## Adding to the Index
The following is a basic example, please note that the config array has been ommitted for simplicity.
```php
$data = [
    'id' => 1,
    'description' => 'This is a description',
    'author' => [
        'id' => 'user'
        'username' => 'example_user',
    ]
];
Scobo\Scobo::driver(Scobo\ElasticDriver($driverConfig))->index('example')->add($data);
```
The response should return an object ID, the developer should store this ID if the need arises to delete the object. The ID should be returned as a string for compatibility with services
```php
'f6cfebed-412d-4237-8543-29dc0976939b'
```

## Removing from the index
The following is a basic example, please note that the config array has been ommitted for simplicity.
```php
Scobo\Scobo::driver(Scobo\ElasticDriver($driverConfig))->index('example')->remove('f6cfebed-412d-4237-8543-29dc0976939b');
```
The response should return true, unless there is an error in which case it should return the ScoboError:
```php
true
```
