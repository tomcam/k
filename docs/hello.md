# Creating, compiling, and running your first Kore program in C

The first program is always the same: display the message `hello, world` to the user. In the case of Kore that means:

1. Running `kore create` to create a starter project
2. Editing the stub C program Kore generated to serve an HTML file
3. Using the `kore run` utility to compile the program and run the web server.
4. Opening a browser to see the results of your handiwork

## Run kore create to generate a starter project

A Kore project consists of a number of moving parts. Generate a template project like this:

* Open a terminal and run `kore create` followed by the project name.

```text
kore create hello
```

This output appears as your project directory is populated:

```text
created hello/src/hello.c
created hello/conf/hello.conf
created hello/conf/build.conf
created hello/.gitignore
created hello/dh2048.pem
hello created successfully!
note: do NOT use the created DH parameters/certificates in production
```

A project consisting of several directories has been created. It contains things like certificate information, configuration files, and a source directory.

* Move to the project directory

```text
cd  hello
```

## Edit the stub C file 

* Update the generated C file named src/hello.c as follows:

```c
/* hello.c */
#include <kore/kore.h>
#include <kore/http.h>

static char *html = "<html><body><p>hello, world.</p></body></html>";

int page(struct http_request *);

int
page(struct http_request *req)
{
	http_response(req, 200, html, strlen(html));
	return (KORE_RESULT_OK);
}
```

## Execute kore run

The `kore run` command expects you to be in the project's root directory, so make it current if you changed directories to edit the C file.

* Use `kore run` to build the project and run the Kore development web server.

```bash
kore run
```

You'll see some output like this:

```text
building hello (dev)
CFLAGS=-Wall -Wmissing-declarations -Wshadow -Wstrict-prototypes -Wmissing-prototypes -Wpointer-arith -Wcast-qual -Wsign-compare -fPIC -I./src -I./src/includes -I/usr/local/Cellar/kore/2.0.0/include -I/opt/local/include -I/usr/local/opt/openssl/include -g 
LDFLAGS=-dynamiclib -undefined suppress -flat_namespace 
compiling hello.c
hello built successfully!
[parent]: running on https://127.0.0.1:8888
[parent]: tasks built-in enabled
[wrk 1]: worker 1 started (cpu#1)
[keymgr]: key manager started
```

## View the results in a web browser

The project is built and a blocking web server is run. Blocking means you'll have to stop it using Ctrl+C but don't do that right now. Instead, leave it running and view it in the browser:

* Open a browser and visit this address:

```text
https://127.0.0.1:8888
```

