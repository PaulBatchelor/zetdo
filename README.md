# Zetdo
Zetdo is a small TODO list shell utility written on top
of [zet](https://pbat.ch/wiki/zet), the Zettelkasten
utility in [Weewiki](https://pbat.ch/wiki/weewiki).

# Prerequisites
- sqlite3 (the sqlite3 CLI utility).
- [weewiki](https://git.sr.ht/~pbatch/weewiki)

# Usage
Create a new TODO database with


```
$ ./zetdo create
```

Add some tasks:

```
$ ./zetdo add
say: make a task in zetdo.
$ ./zetdo add
say: make another task in zetdo.
```

List tasks that still need to be done. This will list
the UUID, date, and message.

```
$ ./zetdo tasks
0fa78ac6 2021-01-16 14:59:30 make a task in zetdo.
7ef73f6d 2021-01-16 15:01:33 make another task in zetdo.
```

Add some comments to the task with UUID 0fa78ac6. Partial
UUIDs can be accepted.

```
$ ./zetdo comment 0fa78
comment: Commenting on my first task.
$ ./zetdo comment 0fa78
comment: Adding another comment.
```

Get the comment history of task 0fa78ac6:

```
$ ./zetdo history 0fa78
2021-01-16 15:05:36     Commenting on my first task.
2021-01-16 15:06:08     Adding another comment.
```

Set task 0fa78ac6 to be done.

```
$ ./zetdo done 0fa78
```

Now it won't show up on when `./zetdo tasks` is run:

```
$ ./zetdo tasks
7ef73f6d 2021-01-16 15:01:33 make another task in zetdo.
```

The zetdo database can be exported to a TSV where it
can managed in source control.

```
$ ./zetdo export > zetdo.tsv
```

The database can then be rebuilt with

```
$ ./zetdo rebuild zetdo.tsv
```