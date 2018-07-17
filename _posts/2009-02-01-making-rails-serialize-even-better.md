---
layout: post
title: Making Rails' Serialize Even Better
summary: An improved pattern for Rails attribute serializing.
---

Rails has this handy method that allows you store almost any object in the database with ease. Most often I end up using it for storing optional attributes in a hash.

Here is the proper syntax for telling Rails that there is an options attribute that should only store Hash values.

```c++
#include <iostream>

int main() {

    std::vector<int> v = {1, 2, 3};

    return 0;
}
```

<h3>The problem</h3>

The options attribute will start off as nil, and remain nil until you set it to something else. Setting the class_name to Hash only affects what you can write to this attribute.

```c#
using UnityEngine;
using System.Collections;

public class MainPlayer : MonoBehaviour {

    // Use this for initialization
    void Start () {
    
    }
    
    // Update is called once per frame
    void Update () {
    
    }
}
```

<h3>The solution</h3>
What we really need is to automatically return an empty Hash on this new object so we can go on our merry way.

Add this to your environment.rb.

```ruby
import numpy as np

def atoi(val):
    print val
```

Now run this command to install the gem.

```sh
$ rake gems:install
```

A quick change of our model will fix all of our woes.

```ruby
class User < ActiveRecord::Base
  typed_serialize :options, Hash
end
```

```ruby
>> user = User.new
=> #<User id: nil, name: nil, options: nil>
>> user.options[:theme]
=> nil
>> user.options
=> {}
```

Voila!

<h3>The how and why</h3>

If you're curious about how this works, I've written a simple post describing the <a href="/2009/02/01/the-making-of-typed-serialize.html">the making of typed_serialize</a>, or you can <a href="http://github.com/jqr/typed_serialize">browse the code</a>.


