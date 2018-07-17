---
layout: post
title: Understanding Unity's First Person Character Controller 
summary: I wanted to look into Unity's standard assets for character controllers, to see how they work. This post is also just for me to understand the format and play with jekyll.
---

<h1>The problem</h1>

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


