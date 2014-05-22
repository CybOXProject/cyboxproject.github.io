---
layout: flat
title: Usage Examples
---

# Generate a document

```python
    from cybox.core import Observable, Observables      
    from cybox.objects.file_object import File

    f = File()                                          # Create a File Object
    f.file_name = "bad_file24.exe"                      # Set the file name
    f.file_path = "AppData\Mozilla"                     # Set the file path
    f.file_extension = ".exe"                           # Set the file extension
    f.size_in_bytes = 3282                              # Set the file size

    o = Observable(f)                                   # Create an Observable container for the File Object
    observables = Observables(o)                        # Create an Observables container for the Observable
    print(doc.to_xml())                                 # Print the Observables 
```

# Ingest a document

```python
from cybox.bindings.cybox_core as core_binding
from cybox.core import Observables

fn = 'cybox_content.xml'                       # The CybOX content filename
cybox_obj = core_binding.parse(fn)             # Create CybOX binding object
observables = Observables.from_obj(cybox_obj)  # Create Observables object from binding object
```

# Data Model
information [is often abstracted out](https://github.com/CybOXProject/python-cybox/tree/master/cybox/objects) for application-specific needs.
