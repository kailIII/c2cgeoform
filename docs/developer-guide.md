## Set up development environment

This page describes how to set up the development environment for working on
`c2cgeoform`. It is for developers working on `c2cgeoform` itself, not for
developers working on `c2cgeoform`-based applications.

### Prerequisites

You need to install PostgreSQL and PostGIS. On Ubuntu, the packages
`postgresql-server-dev-9.3` and `python-dev` are required.

You need to create a role. For example:

```shell
$sudo su - postgres
$ createuser --pwprompt c2cgeoform
Enter password for new role: [c2cgeoform]
Enter it again: [c2cgeoform]
```

You need to create a PostGIS database. For example:

```shell
$ createdb --owner=c2cgeoform c2cgeoform
$ psql -d c2cgeoform -c "CREATE EXTENSION postgis;"
```

### Configuration

Edit `development.ini` and modify the SQLAlchemy database connection string as
appropriate.

For example:

```py
sqlalchemy.url = postgresql://c2cgeoform:c2cgeoform@localhost:5432/c2cgeoform
```

### Installation

Install a dev egg of `c2cgeoform` in a virtual env:

```shell
$ make install
```

(This creates the virtual env for you.)

Just run `make` to know about the possible targets.

### Initialize the DB

Initialize the database:

```shell
$ make initdb
```

### Start the dev server

Start the dev server:

```shell
$ make serve
```

### Run the tests

Run the tests:

```shell
$ make test
```
