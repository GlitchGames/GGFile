GGFile
============

GGFile makes it easy to work with files and directories.

Basic Usage
-------------------------

##### Require the code
```lua
local GGFile = require( "GGFile" )
```

##### Create your file manager
```lua
local fileManager = GGFile:new()
```

##### Write data to a file
```lua
fileManager:write( "test.txt", "Hello,\nWorld!", system.DocumentsDirectory )
```

##### Read data from a file
```lua
print( fileManager:read( "test.txt", system.DocumentsDirectory ) )
```

##### Append data to a file
```lua
fileManager:append( "test.txt", "\nGlitch\nAre\nAwesome :-)", system.DocumentsDirectory )
```

##### Read in, and print out, all lines in a file.
```lua
local lines = fileManager:readLines( "test.txt", system.DocumentsDirectory )

for i = 1, #lines, 1 do
	print( lines[ i ] )
end
```

##### Rename a file
```lua
fileManager:rename( "test.txt", "test2.txt", system.DocumentsDirectory )
```

##### Delete a file
```lua
fileManager:delete( "test2.txt", system.DocumentsDirectory )
```

##### Move a file
```lua
fileManager:move( "test.lua", system.ResourceDirectory, "test.lua", system.DocumentsDirectory )
```

##### Copy a file
```lua
fileManager:copy( "test.lua", system.ResourceDirectory, "test.lua", system.DocumentsDirectory )
```

##### Get, and print out, a list of files found in a directory called 'savedPhotos' in the Documents Directory
```lua
local files = fileManager:getFilesInDirectory( "savedPhotos", system.DocumentsDirectory )

for i = 1, #files, 1 do
	print( files[ i ] )
end
```

##### Create a directory called 'test' in the Documents Directory
```lua
local success, reason = fileManager:makeDirectory( "", "test", system.DocumentsDirectory )

print( success, reason )
```

##### Delete a directory called 'test' from the Documents Directory
```lua
local success, reason = fileManager:removeDirectory( "test", system.DocumentsDirectory )

print( success, reason )
```

##### Get a specific attribute of a file
```lua
local attribute = fileManager:getAttributes( "test/srfg.txt", GGFile.Attribute.LastAccess )
print( attribute )
```

##### Get, and print out, all attributes of a file
```lua
local attributes = fileManager:getAttributes( "test/srfg.txt" )

for k, v in pairs( attributes ) do
	print( k, v )
end
```

##### Check if a file/directory exists
```lua
local exists = fileManager:exists( "test/srfg.txt" )
print( exists )
```

##### Check if something is a directory
```lua
local isDirectory = fileManager:isDirectory( "test" )
print( isDirectory )
```

##### Destroy the file manager
```lua
fileManager:destroy()
fileManager = nil
```