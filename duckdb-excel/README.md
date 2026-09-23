# Excel Reader

Open Excel workbooks as tables you can query.

Opens: **Excel workbooks (.xlsx, .xlsm)**

## What this installs

Nothing of its own. The plugin is a few kilobytes of metadata declaring that
Thoth should ask DuckDB for its `excel` extension — roughly **7.5 MB**,
downloaded once and cached under `~/.duckdb/extensions/<duckdb-version>/<platform>/`.

DuckDB hosts a build per platform and per its own version and picks the right
one, so there is nothing here to keep in step with your machine.

## Why it is opt-in

Left to itself DuckDB fetches a missing reader silently, mid-open, from a
background thread — an unannounced download on a metered connection, and on a
machine with no route out, a failure nobody sees. Thoth turns that off. Opening
a file that needs this reader names it and offers to fetch it; until then the
file opens as plain text.

## Installing

Install it from **Marketplace → File readers**, or accept the offer shown above
a file that needs it. Both do the same thing.
