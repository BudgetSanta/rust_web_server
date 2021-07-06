# Rust Web Server

This was a project from [The Book](https://doc.rust-lang.org/book/) in the [Final Project: Building a Multithreaded Web Server](https://doc.rust-lang.org/book/ch20-00-final-project-a-web-server.html) chapter.

To demonstrate the clean up of the workers handling the threads, only the first 50 requests are served.

* A worker pool is created, each gets a thread.
* Jobs get sent through the channel that eadch worker can access
* Workers will loop to pickup messages which can be jobs or terminations
* You can access either the `GET /` endpoint, or by virtue of accessing any other route the `/404.html`page.
* After the 50 requests are served, the workers are dropped and the cleanup begins. 
* Each worker is sent a termination message and will no longer take jobs. The threads are joined into the main thread and execution finishes.

