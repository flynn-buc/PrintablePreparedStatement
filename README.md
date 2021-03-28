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
<img width="920" alt="Screen Shot 2021-03-28 at 2 06 19 AM" src="https://user-images.githubusercontent.com/54959558/112747429-3dbc7b80-8f6a-11eb-8e3b-4d7b75ccc5bf.png">


- Output
<img width="491" alt="Screen Shot 2021-03-28 at 2 04 37 AM" src="https://user-images.githubusercontent.com/54959558/112747381-f9c97680-8f69-11eb-8bcd-b0837b0d443d.png">




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
