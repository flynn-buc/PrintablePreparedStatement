# PrintablePreparedStatement
Decorator for PreparedStatement, prints queries in readable format

# Usage
## To setup
``` 
String query = "INSERT INTO table_name VALUES (?, ?, ?, ?);"
PrintablePreparedStatement ps = new PrintablePreparedStatement(connection.prepareStatement(query), query);
```
- Any query can be passed as a parameter
- With the default settings, calling ```ps.execute()```, ```ps.executeQuery()```, or ```ps.executeUpdate()``` will print the query before executing it

## To print
```
System.out.println(ps.toString());
```
or
``` 
ps.print();
```

## To turn on/off auto-printing (program-wise)
```
PrintablePreparedStatement.autoPrint = true; // or false 
```
