# TCPServer
Package tcp_server created to help build TCP servers faster.

### Install package

``` bash
> go get github.com/dudehook/tcp_server
```

### Usage:

NOTICE: `OnNewMessage` callback will receive new message only if it's ending with `\n`

``` go
package main

import "github.com/dudehook/tcp_server"

func main() {
	server := tcp_server.New("localhost:9999")

	server.OnNewClient(func(c *tcp_server.Client) {
		// new client connected
		// lets send some message
		c.Send("Hello")
	})
	server.OnNewMessage(func(c *tcp_server.Client, message string) {
		// new message received
	})
	server.OnClientConnectionClosed(func(c *tcp_server.Client, err error) {
		// connection with client lost
	})

	server.Listen()
}
```

# Contributing

Contribute upstream:

1. Fork it on GitHub
2. Add your remote (`git remote add fork git@github.com:firstrow/tcp_server.git`)
3. Push to the branch (`git push fork my-new-feature`)
4. Create a new Pull Request on GitHub

Notice: Always use the original import path by installing with `go get`.
