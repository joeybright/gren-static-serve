# gren-static-serve

A very simple way to serve static files from a provided directory.

This package tries to make it as simple as possible to serve static files from a specified directory with Gren. It's opinionated in that there are very few ways to customize it, but it should handle common use-cases for serving static files.

### How it works

The server does the follow in order:

1. Attempts to find the requested file at the provided file path. If it finds the file, returns it. If it fails, it tries #2.
2. Attempts to find the `index.html` file within the provided file path. This allows pretty-urls (/about instead of /about/index.html) to be supported. If it is found, it will return the file. It if fails, it tries #2.
3. Find the root `index.html` file (if it exists). This allows support for single-page apps, who most likely have a single `index.html` file in the root of the directory. Whatever single-page app you're serving will then be able to handle the entered url.

If all the steps above fail, the `Task` fails returning a `Response` with a 404 status.
