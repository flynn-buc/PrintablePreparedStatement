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

### Sample Output
- Code used
<img width="921" alt="Screen Shot 2021-03-28 at 2 02 10 AM" src="https://user-images.githubusercontent.com/54959558/112747339-a5be9200-8f69-11eb-9224-7caed7a5ed5e.png">

- Output
<img width="503" alt="Screen Shot 2021-03-28 at 2 00 24 AM" src="https://user-images.githubusercontent.com/54959558/112747340-a6572880-8f69-11eb-8af3-873fbe80aa61.png">



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
- Feel free to make an issue if a particular setter isn't printing properly, or if you'd like one that isn't listed above
