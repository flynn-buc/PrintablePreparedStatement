# Contents
- [PrintablePreparedStatement](#printablepreparedstatement)
- [Installation](#installation)
- [Usage](#usage)
  * [To instantiate](#to-instantiate)
  * [To print manually](#to-print-manually)
  * [To turn on/off auto-printing (program-wise)](#to-turn-on-off-auto-printing--program-wise-)
  * [Sample Output](#sample-output)
- [Current working setters](#current-working-setters)
  * [Known issues](#known-issues)
- [Missing features?](#missing-features-)


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


## To turn on/off auto-printing (program-wise)
```
PrintablePreparedStatement.autoPrint = false; // true by default
```


## Sample Output
- Code used
<img width="945" alt="Screen Shot 2021-03-28 at 2 11 00 AM" src="https://user-images.githubusercontent.com/54959558/112747521-e4a11780-8f6a-11eb-9c80-4d8861e2fcd5.png">



- Output
<img width="491" alt="Screen Shot 2021-03-28 at 2 04 37 AM" src="https://user-images.githubusercontent.com/54959558/112747381-f9c97680-8f69-11eb-8bcd-b0837b0d443d.png">



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
setObject() // the object's toString() method will be called.
```

## Known issues
- Will not work if the table name or the attribute contains a '?'
- Does not work with arrays or streams

# Missing features?
- Feel free to make an issue if a particular setter isn't printing properly, or if you'd like one that isn't listed above
