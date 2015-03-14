Simple Erlang example
================

[German / Deutsch](LIESMICH.MD)

This is a very simple example for an Erlang based application with a client and a server exchanging messages.

To run you need:
- [Erlang](http://www.erlang.org/download.html)

To execute the example:
- Starting Erlang with `erl -sname servernode`.
- Compile the server module: `c(server).`
- Spawn the server: `Pid = spawn(fun server:loop/0).`
- You can now send it messages like this: `Pid ! "42".`

Distributed messages are also easy to do:
- Enter `register(serverpid, Pid).` to register the server
- Start another Erlang process: `erl -sname clientnode`.
- Enter `net_kernel:connect_node(servernode@name).` to set up an Erlang cluster. Change `name` to what the Erlang prompt on the server says. If it works correctly it returns `true`.
-Enter ` {serverpid, servernode@name} ! "42".` to send the server a message.
