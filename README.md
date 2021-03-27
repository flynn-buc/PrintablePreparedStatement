# PrintablePreparedStatement
Decorator for JDBC PreparedStatement, prints queries in readable format

# Installation
Copy the file into your project (jar and maven dependency will be coming in the future)
# Usage
## To instantiate
``` 
String query = "INSERT INTO table_name VALUES (?, ?, ?, ?);"
PrintablePreparedStatement ps = new PrintablePreparedStatement(connection.prepareStatement(query), query);
```
- Any query can be passed as a parameter
- With the default settings, calling ```ps.execute()```, ```ps.executeQuery()```, or ```ps.executeUpdate()``` will print the query before executing it

## To print manually
```
System.out.println(ps.toString());
```
or
``` 
ps.print();
```

### Sample Output"
<img width="295" alt="Screen Shot 2021-03-26 at 6 57 31 PM" src="https://user-images.githubusercontent.com/54959558/112706976-26e03100-8e65-11eb-9f98-9411fc0e4d36.png">


## To turn on/off auto-printing (program-wise)
```
PrintablePreparedStatement.autoPrint = true; // or false 
```


# Current working setters
```
setBoolean()
setBytes()
setShort()
setInt()
setString()
setLong()
setFloat()
setDouble()
setBigDecimal()
setDate()
setTime()
setTimestamp()
```

## Known issues
- Will not work if the table name or the attribute contains a '?'
- Does not work with arrays or streams

# Missing features?
- Feel free to let me know if a particular setter isn't printing properly, or if you'd like one that isn't listed above
