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

And In return the develops should receive an array:
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
