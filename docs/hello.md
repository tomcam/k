# Creating, compiling, and running your first Kore program in C

The first program is always the same: display the message `hello, world` to the user. In the case of Kore that means:

1. Running `kore create` to create a template project
2. Writing a C program that contains an HTML file to be output to the servier
3. Compile the program
4. Run the Kore server to display the program
5. Open a browser to see the results of your handiwork

## Run kore create to generate a template project

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

A project consisting of several directories has been created. It contains things like certificate information, configuration files, and an empty source directory.

* Move into that directory

```text
cd  hello
```

* There is no actual C file yet, but it does in the `src` directory. Create the following C filen named hello.c:

```c
/* hello.c */
#include <kore/kore.h>
#include <kore/http.h>

static char     *html = "<html><body><p>hello, world.</p></body></html>";

int		page(struct http_request *);

int
page(struct http_request *req)
{
	http_response(req, 200, html, strlen(html));
	return (KORE_RESULT_OK);
}
```

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
The project is built and a blocking web server is run. Blocking means you'll have to stop it using Ctrl+C but don't do that right now. Instead:

* Open a browser and visit this address:

```text
https://127.0.0.1:8888
```

