---
layout: flat
title: Usage Examples
---


# Generate a document
``` python

import cybox.bindings.cybox_core as cybox_binding
import cybox.bindings.cybox_common as cybox_common_binding
import cybox.bindings.file_object as file_binding

#Create the Observables object, representing the root of the document
observables = cybox_binding.ObservablesType(cybox_minor_version=0,cybox_major_version=2)
#Create an observable to hold the File Object
observable = cybox_binding.ObservableType()
#Create the CybOX object and instantiate and populate File Object
obj = cybox_binding.ObjectType()
file_obj = file_binding.FileObjectType()
file_obj.set_File_Name(cybox_common_binding.StringObjectPropertyType(datatype=None,apply_condition=None, valueOf_='foobar.dll'))
file_obj.set_Size_In_Bytes(cybox_common_binding.UnsignedLongObjectPropertyType(datatype=None,apply_condition=None, valueOf_='25562'))
#Set the XSI extension type of the File Object
file_obj.set_xsi_type('FileObj:FileObjectType')
#Set the File Object as the Properties of the parent CybOX Object
obj.set_Properties(file_obj)
#Set the CybOX Object as the Observable Object
observable.set_Object(obj)
#Add the Observable to the root Observables
observables.add_Observable(observable)
#Open a file for writing and export the Observables and all of its children to an XML document
out_file = open('test.xml', 'w')
observables.export(out_file,0)
out_file.close()
```

# Ingest a document
``` python
import cybox_core_1_0 as cybox

#Parse the input CybOX XML file
observables = cybox.parse('watchlist_example.xml')
#Print out the number of Observables in the document
print 'Number of Observables: ' + str(len(observables.get_Observable()))
```
