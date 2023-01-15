## Project Idea: File Watcher

Create a python package that can be configured to watch a single file, multiple files or all files nested within a directory. 
If a file is modified a user defined callback function is executed.

### Example use cases for the package:
- Run a code formatter every time a file is saved.
- Backup a newly created file to a storage server
- Something else?

### Implementation:
The following 3 functions should be exposed by the API/package

```python
def watch_single(filename, callback, period):
    """
    :arg filename: name of the file to watch
    :arg callback: function to call when the file is modified
    :arg period: how often the file should be checked e.g. period=1 -> the file is checked every second
    """
    pass
    
def watch_multiple(files, callback, period):
    """
    :arg files: list of filenames to watch
    :arg callback: function to call for each file that is modified
    :arg period: how often the files should be checked e.g. period=1 -> the files are checked every second
    """
    pass
    
def watch_directory(dirname, callback, period):
    """
    :arg dirname: name of the directory to watch
    :args callback: function to call for each file that is modified
    :arg period:  how often the files in the directory should be checked e.g. period=1 -> the files are checked every second
    """
    pass
```

The callback function will have the following signature:
```python
def some_callback(filename, event_type):
    """Example callback function"""
    
    id event_type == "CREATED":
        # do something
        pass
    elif event_type == "UPDATED":
        # do something
        pass
    elif event_type == "DELETED":
        # do someting
        pass
    else:
        raise Exception("Unknow event type")
            
```

The event types are:
- CREATED
- UPDATED
- DELETED

### Other requirements:
- Pure python implementation (only use standard library).
- Should be able to run on MacOS, Windows and linux.
- Include a simple documentation file on how to use the package
- Publish the package on [PYPI](https://pypi.org/)
