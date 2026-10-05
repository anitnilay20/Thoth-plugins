# Avro Reader

Open Avro container files as tables you can query.

Opens: **Avro object container files (.avro)**

## What this installs

Nothing of its own. The plugin is a few kilobytes of metadata declaring that
Thoth should ask DuckDB for its `avro` extension — roughly **7.5 MB**,
downloaded once and cached under `~/.duckdb/extensions/<duckdb-version>/<platform>/`.

DuckDB hosts a build per platform and per its own version and picks the right
one, so there is nothing here to keep in step with your machine.

## What Avro is

A row-oriented container: four magic bytes, a header carrying the writer's
schema as JSON, then blocks of records. Because the schema travels inside the
file, an `.avro` describes itself — Thoth recognises one by its header, so a
file opens as a table whatever it happens to be called.

Where Parquet stores columns and rewards reading a few of them from a large
file, Avro stores whole records and rewards appending them one at a time. It is
what lands at the end of most streaming pipelines for that reason.

## Why it is opt-in

Left to itself DuckDB fetches a missing reader silently, mid-open, from a
background thread — an unannounced download on a metered connection, and on a
machine with no route out, a failure nobody sees. Thoth turns that off. Opening
a file that needs this reader names it and offers to fetch it; until then the
file opens as plain text.

## Installing

Install it from **Marketplace → File readers**, or accept the offer shown above
a file that needs it. Both do the same thing.
