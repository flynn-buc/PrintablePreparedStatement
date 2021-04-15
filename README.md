# Contents
- [PrintablePreparedStatement](#printablepreparedstatement)
- [Installation](#installation)
- [Usage](#usage)
  * [To instantiate](#to-instantiate)
  * [To instantiate with auto-printing turned off](#to-instantiate-with-auto-printing-turned-off)
  * [To toggle auto-printing (application-wise)](#to-toggle-auto-printing-application-wise)
  * [To print manually](#to-print-manually)
  * [Sample Output](#sample-output)
- [Current working setters](#current-working-setters)
  * [Known issues](#known-issues)
- [Missing features?](#missing-features)


# PrintablePreparedStatement
Decorator for JDBC PreparedStatement, prints queries in readable format. 
Internal implementation of PreparedStatement is unchanged.

# Installation
Copy the file into your project (jar and/or maven dependency may be coming in the future)
# Usage
## To instantiate


``` 
String query = "INSERT INTO table_name VALUES (?, ?, ?, ?)"
PrintablePreparedStatement ps = 
new PrintablePreparedStatement(connection.prepareStatement(query), query);
```
Where ```connection``` is an instance of ```java.sql.Connection```

- Any query can be passed as a parameter
- With the default settings, calling ```ps.execute()```, ```ps.executeQuery()```, or ```ps.executeUpdate()``` will print the query before executing it

## To instantiate with auto-printing turned off

``` 
String query = "INSERT INTO table_name VALUES (?, ?, ?, ?)"
PrintablePreparedStatement ps = 
new PrintablePreparedStatement(connection.prepareStatement(query), query, false);
```


## To toggle auto-printing (application-wise)
```
PrintablePreparedStatement.autoPrint = false; // true by default
```

## To print manually
```
System.out.println(ps.toString());
```
or
``` 
ps.print();
```


## Sample Output
- Code used
<img width="931" alt="Screen Shot 2021-04-15 at 12 34 22 AM" src="https://user-images.githubusercontent.com/54959558/114831643-776eee00-9d82-11eb-8b2c-8d694a3f8484.png">




- Output
<img width="582" alt="Screen Shot 2021-04-15 at 12 28 45 AM" src="https://user-images.githubusercontent.com/54959558/114831653-7938b180-9d82-11eb-868a-cd4b1f45f794.png">




# Current working setters
```
setBoolean()
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
- May not work if the table name or the attribute contains a '?'
- Does not work with arrays or streams

# Missing features?
- Feel free to make an issue if a particular setter isn't printing properly, or if you'd like one that isn't listed above
