---
layout: code
title: A Test Post
date: 2016-04-09
author: Eric Taw
visible: 0
---

# This is a test post

Some information goes down here.

```python
def find_collatz(n):

    # Main Collatz Conjecture function. Takes in integer n, where n is the initial value
    # @param: int n
    # @returns: array result

    result = [n]
    while result[-1] > 1:
        if result[-1] % 2 == 0:
            result.append(int(result[-1] / 2))
        else:
            result.append(int(result[-1] * 3 + 1))
    return result
```

Some Javascript

```js
var express = require('express');
var app = express();

app.get('/', function(req, res) {
    res.send('http 200');
});

app.listen(3031);

```

Some PHP

```php
<? php

use App\User;

class TestController extends Controller {
    public function get_user() {
        $message = 'This is a message.';
        string_append($message, 'Hi');
        return User::find(1);
    }
}
```
