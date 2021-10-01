(@v1.7) pkg> add https://github.com/kimmolinna/julia-duckdb

import DuckDB
con = DuckDB.dbConnect(":memory:")
res = DuckDB.dbExecute(con,"CREATE TABLE integers(date DATE, jcol INTEGER)")
res = DuckDB.dbExecute(con,"INSERT INTO integers VALUES ('2021-09-27', 4), ('2021-09-28', 6), ('2021-09-29', 8)")
res = DuckDB.dbExecute(con,"SELECT * FROM integers")
DuckDB.toDF(res)
# create a table
DuckDB.dbExecute(con, "CREATE TABLE items(item VARCHAR, value DOUBLE, count INTEGER);")
# insert two items into the table
DuckDB.dbExecute(con, "INSERT INTO items VALUES ('jeans', 20.0, 1), ('hammer', 42.2, 2);")
# retrieve the items again
res = DuckDB.dbExecute(con, "SELECT * FROM items")
DuckDB.toDF(res)