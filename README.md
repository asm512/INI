# easyINI


easyINI is a simple class that can be added to any .NET project, and is used for reading and writing INI files using the Windows API.

You can also:
  - Check if a key exists
  - Delete keys
  - Delete sections
  - Get all sections
  
To add:
  - ~~Get all sections (into array)~~


> Feel free to use this in
> any personal projects
> without attribution


### Usage and examples

Make sure to change the namespace of the class to match your original one

Declaring an ini file:

    //Creates a new INI file in your current dir named after the exe
    IniFile MyIni = new IniFile();

    //Creates an ini file in current dir with specified name
    IniFile MyIni = new IniFile("settings.ini");
    
    //Creates a new ini file in specified directory
    IniFile MyIni = new IniFile(@"C:\settings.ini");
    
    //Easy start 
    MyIni.Write("Key", "Value", "Section (optional)");
    MyIni.Read("Key", "Section (only state if it's not default one)");
    
Writing to an INI file:
    
    //Writing to file with default section (name of executable)
    MyIni.Write("DefaultValue", "40");
    MyIni.Write("userName", "admin");
    
    Creates a file like this:
    [EXE NAME]
    DefaultValue=40
    userName=admin
    
    //Writing to file with specified section
    MyIni.Write("DefaultValue", "40", "VALUES");
    MyIni.Write("userName", "admin", "USER");
    
    Creates a file like this:
    [VALUES]
    DefaultValue=40
    [USER]
    userName=admin
    
Reading from INI file:
    
    //Can explicitly state variable type or use var instead
    string DefaultValue = MyIni.Read("DefaultValue");
    or
    int DefaultValue = Convert.ToInt32(MyIni.Read("DefaultValue"));
    
    string username = MyIni.Read("userName");
    
    string[] allSections = MyINI.GetSectionNames();
    
Checking if key exists
    
    //Easy start
    bool keyExist = MyIni.KeyExists("Key", "Section (only state if it's not default one)")

    if(!MyIni.KeyExists("DefaultValue", "VALUES"))
    {
    MyIni.Write("DefaultValue", "40", "VALUES");
    }

Deleting keys and sections:

    MyIni.DeleteKey("DefaultValue", "VALUES");
    MyIni.DeleteSection("VALUES");

### Development

Want to contribute?

Feel free to fork this and make any requests for changes in my repository
