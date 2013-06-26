It is possible to set launch modules automatically on new hooked browsers in BeEF. You just have to set the autorun value to true in the config.yaml of targeted module.

For example for the test_return_ascii_chars module

```yaml
beef:
    module:
        test_return_ascii_chars:
            enable: true
            category: "Debug"
            name: "Return Ascii Chars"
            description: "This module will return the set of ascii chars."
            authors: ["wade"]
            autorun: true
            target:
                working: ["ALL"]
```

Today, the autorunned modules are launched with default parameters value, which is an important limitation however improvements are planned by the BeEF team on this point.