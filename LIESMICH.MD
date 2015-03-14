Einfaches Erlang Beispiel
================

Dieses Beispiel zeigt einen einfachen Erlang Server und Client.

Für das Beispiel ist Erlang notwendig:
- [Erlang](http://www.erlang.org/download.html)

Um das Beispiel auszuführen:
- Starte Erlang mit `erl -sname servernode`.
- Kompiliere das Server-Modul: `c(server).`
- Starte den Server: `Pid = spawn(fun server:loop/0).`
- Jetzt kannst Du dem Server Nachrichten schicken: `Pid ! "42".`

Verteilte Nachrichten sind ebenfalls einfach möglich:
- Gib `register(serverpid, Pid).` ein, um den Server zu registrieren.
- Starte einen weiteren Erlang-Prozess: `erl -sname clientnode`.
- Gib `net_kernel:connect_node(servernode@name).` ein, um einen Erlang-Cluster aufzubauen. Ändere `name` entsprechend dem, was der Server ausgibt. Wenn alles richtig ist, gibt der Aufruf `true` zurück.
- Gib ` {serverpid, servernode@name} ! "42".` ein, um dem Server eine Nachricht zu schicken.
