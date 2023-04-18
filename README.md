# strawberry-view

This is a simple template engine for [strawberry](https://github.com/elderguardian/strawberry), but you could easily use it in other frameworks.

## Setup

### Installation

1. Download the repository or clone its content
2. Move the `strawberry-view/` directory inside `src/` into the strawberry's `src/foundations`
3. Create a `views/` directory inside `src/`
4. Create a `components/` directory inside `src/views`

### Creating your first view

#### **`src/views/error.php`**

```
Error: {{ $message }}
```

Now you can use it in a controller:

##### **`src/controllers/YourController.php`**

```php
    ...

    public function world() {
        return $this->view('error', [
            'message' => 'lol'
        ]);
    }

    ...
```

### Creating your first component

Create a component you want to reuse and add variables.

#### **`src/views/components/card.php`**

```
<div>
    <h3>{{ name }}</h3>
    <p>{{ $description }}</p>
</div>
```

Now you can use: inside a view:

#### **`src/views/home.php`**

```
<h1>Welcome</h1>
<h2>Cards:</h2>

{{ card, { "name": "John Doe", "description": "Hello World!" } }}
{{ card, { "name": " {{ $firstPerson }}", "description": "hey." } }}
```

And now you can normally use the view:

##### **`src/controllers/YourController.php`**

```php
    ...

    public function world() {
        return $this->view('home', [
            'firstPerson' => 'Max Mustermann'
        ]);
    }

    ...
```