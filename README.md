errors
=======

Get an easier and faster way to code http error handling in your web app. Largely used on [americanas-go/ignite](https://github.com/americanas-go/ignite) rest app module.

Installation
------------

	go get -u github.com/americanas-go/errors

Example define error
--------
```go
import (
    "log"

    "github.com/americanas-go/errors"
)

func main() {

    err := errors.AlreadyExistsf("order id %s", "123")
    log.Fatalf(err.Error())
    // output: 2021/06/07 15:15:08 order id 123 already exists
}
```

Example check error type
--------
```go
package main

import (
    "log"

    "github.com/americanas-go/errors"
)

func main() {

    err := errors.BadRequestf("order id is required")

    switch {
    case errors.IsAlreadyExists(err):
        log.Fatalf(err.Error())
    case errors.IsForbidden(err):
        log.Fatalf(err.Error())
    case errors.IsBadRequest(err):
        log.Fatalf(err.Error())
        // output: 2021/06/07 15:40:06 order id is required
    default:
        //...
    }
}
```

Contributing
--------
Every help is always welcome. Feel free do throw us a pull request, we'll do our best to check it out as soon as possible. But before that, let us establish some guidelines:

1. This is an open source project so please do not add any proprietary code or infringe any copyright of any sort.
2. Avoid unnecessary dependencies or messing up go.mod file.
3. Be aware of golang coding style. Use a lint to help you out.
4.  Add tests to cover your contribution.
5. Use meaningful [messages](https://medium.com/@menuka/writing-meaningful-git-commit-messages-a62756b65c81) to your commits.
6. Use [pull requests](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/about-pull-requests).
7. At last, but also important, be kind and polite with the community.

Any submitted issue which disrespect one or more guidelines above, will be discarded and closed.


<hr>

Released under the [MIT License](LICENSE).