---
layout: flat
title: Object Relationships
---

This page contains a detailed listing of the available CybOX Object → Object
relationships (from the [ObjectRelationshipVocab-1.1](http://stixproject.github.io/data-model/1.1.1/cyboxVocabs/ObjectRelationshipVocab-1.1/) vocabulary), and adds some additional context for each relationship. This includes a richer definition,
a listing and description of the Objects that the relationship is most applicable
to, its inverse (if existing), and an example XML snippet that demonstrates the
relationship in use.

# Index

* [Created](#Created)
* [Created_By](#Created_By)
* [Deleted](#Deleted)
* [Deleted_By](#Deleted_By)
* [Modified_Properties_Of](#Modified_Properties_Of)
* [Properties_Modified_By](#Properties_Modified_By)
* [Downloaded_From](#Downloaded_From)
* [Downloaded_To](#Downloaded_To)
* [Downloaded](#Downloaded)
* [Downloaded_By](#Downloaded_By)
* [Uploaded](#Uploaded)
* [Uploaded_By](#Uploaded_By)
* [Uploaded_To](#Uploaded_To)
* [Sent_To](#Sent_To)
* [Received_From](#Received_From)
* [Values_Enumerated](#Values_Enumerated)
* [Values_Enumerated_By](#Values_Enumerated_By)
* [Killed](#Killed)
* [Killed_By](#Killed_By)
* [Locked](#Locked)
* [Locked_By](#Locked_By)
* [Unlocked](#Unlocked)
* [Unlocked_By](#Unlocked_By)
* [Listened_On](#Listened_On)
* [Renamed_From](#Renamed_From)
* [Renamed_To](#Renamed_To)
* [Renamed](#Renamed)
* [Renamed_By](#Renamed_By)
* [Contains](#Contains)
* [Contained_Within](#Contained_Within)
* [Extracted_From](#Extracted_From)
* [Connected_To](#Connected_To)

## <a name="Created"></a> "Created"

The **source Object** *Created* the **related Object**. Applicable to a wide range of Objects, particularly in the context of a Process that creates other Objects.

### Inverse

"Deleted"

### Applicable Objects

<table class="table-striped">
 <tbody>
   <tr>
	 <th>Source Object</th>
	 <th>Related Object</th>
	 <th>Description</th>
   </tr>
   <tr>
	 <td>Archive File</td>
	 <td>File</td>
	 <td>A self-extracting archive file created a file upon extraction.</td>
   </tr>
   <tr>
	 <td>Process</td>
	 <td>File</td>
	 <td>A process created a file during its execution.</td>
   </tr>
   <tr>
	 <td>Process</td>
	 <td>Process</td>
	 <td>A process created another process during its execution.</td>
   </tr>
   <tr>
	 <td>Process</td>
	 <td>Win Registry Key</td>
	 <td>A process created a Windows registry key or registry key value during its execution.</td>
   </tr>
   <tr>
	 <td>Process</td>
	 <td>Win Service</td>
	 <td>A process created a Windows service during its execution.</td>
   </tr>
   <tr>
	 <td>Process</td>
	 <td>Mutex</td>
	 <td>A process created a mutex during its execution.</td>
   </tr>
   <tr>
	 <td>Process</td>
	 <td>Win Thread</td>
	 <td>A process created a Windows thread during its execution.</td>
   </tr>
 </tbody>
</table>

### Example

```xml
<cybox:Object id="example:object-c822a70d-7b41-4553-983b-a07fd8c553a0">
	<cybox:Properties xsi:type="ProcessObj:ProcessObjectType">
		<ProcessObj:Image_Info>
			<ProcessObj:File_Name>some_process.exe</ProcessObj:File_Name>
		</ProcessObj:Image_Info>
	</cybox:Properties>
	<cybox:Related_Objects>
		<cybox:Related_Object id="example:object-e970c3df-0c01-4611-8257-6b01d188983c">
			<cybox:Properties xsi:type="FileObj:FileObjectType">
				<FileObj:File_Path>C:\temp\qwerty.dll</FileObj:File_Path>
			</cybox:Properties>
			<cybox:Relationship xsi:type="cyboxVocabs:ObjectRelationshipVocab-1.1">Created</cybox:Relationship>
		</cybox:Related_Object>
	</cybox:Related_Objects>
</cybox:Object>
```	

---

## <a name="Created_By"></a> "Created_By"

The **source Object** was *Created by* the **related Object**. Applicable to a wide range of Objects, particularly in the
context of Objects that were created by a Process.

### Inverse

"Deleted_By"

### Applicable Objects

<table class="table-striped">
 <tbody>
   <tr>
	 <th>Source Object</th>
	 <th>Related Object</th>
	 <th>Description</th>
   </tr>
   <tr>
	 <td>File</td>
	 <td>Archive File</td>
	 <td>A file was created by a self-extracting archive file as part of its extraction operation.</td>
   </tr>
   <tr>
	 <td>File</td>
	 <td>Process</td>
	 <td>A file was created by a process during its execution.</td>
   </tr>
   <tr>
	 <td>Process</td>
	 <td>Process</td>
	 <td>A process was created by another process during its execution.</td>
   </tr>
   <tr>
	 <td>Win Registry Key</td>
	 <td>Process</td>
	 <td>A Windows registry key or registry key value was created by a process during its execution.</td>
   </tr>
   <tr>
	 <td>Win Service</td>
	 <td>Process</td>
	 <td>A Windows service was created by a process during its execution.</td>
   </tr>
   <tr>
	 <td>Mutex</td>
	 <td>Process</td>
	 <td>A mutex was created by a process during its execution.</td>
   </tr>
   <tr>
	 <td>Win Thread</td>
	 <td>Process</td>
	 <td>A Windows thread was created by a process during its execution.</td>
   </tr>
 </tbody>
</table>

### Example

```xml
<cybox:Object id="example:object-e970c3df-0c01-4611-8257-6b01d188983c">
	<cybox:Properties xsi:type="FileObj:FileObjectType">
		<FileObj:File_Path>C:\temp\qwerty.dll</FileObj:File_Path>
	</cybox:Properties>
	<cybox:Related_Objects>
		<cybox:Related_Object id="example:object-c822a70d-7b41-4553-983b-a07fd8c553a0">
			<cybox:Properties xsi:type="ProcessObj:ProcessObjectType">
				<ProcessObj:Image_Info>
					<ProcessObj:File_Name>some_process.exe</ProcessObj:File_Name>
				</ProcessObj:Image_Info>
			</cybox:Properties>
			<cybox:Relationship xsi:type="cyboxVocabs:ObjectRelationshipVocab-1.1">Created_By</cybox:Relationship>
		</cybox:Related_Object>
	</cybox:Related_Objects>
</cybox:Object>
```	

---

## <a name="Deleted"></a> "Deleted"

The **source Object** *Deleted* the **related Object**. Applicable to a wide range of Objects, particularly in the context of a Process that deleted other Objects.

### Inverse

"Created"

### Applicable Objects

<table class="table-striped">
 <tbody>
   <tr>
	 <th>Source Object</th>
	 <th>Related Object</th>
	 <th>Description</th>
   </tr>
   <tr>
	 <td>Process</td>
	 <td>File</td>
	 <td>A process deleted a file during its execution.</td>
   </tr>
   <tr>
	 <td>Process</td>
	 <td>Win Registry Key</td>
	 <td>A process deleted a Windows registry key or registry key value during its execution.</td>
   </tr>
   <tr>
	 <td>Process</td>
	 <td>Win Service</td>
	 <td>A process deleted a Windows service during its execution.</td>
   </tr>
   <tr>
	 <td>Process</td>
	 <td>Mutex</td>
	 <td>A process deleted a mutex during its execution.</td>
   </tr>
 </tbody>
</table>

### Example

```xml
<cybox:Object id="example:object-c822a70d-7b41-4553-983b-a07fd8c553a0">
	<cybox:Properties xsi:type="ProcessObj:ProcessObjectType">
		<ProcessObj:Image_Info>
			<ProcessObj:File_Name>some_process.exe</ProcessObj:File_Name>
		</ProcessObj:Image_Info>
	</cybox:Properties>
	<cybox:Related_Objects>
		<cybox:Related_Object id="example:object-e970c3df-0c01-4611-8257-6b01d188983c">
			<cybox:Properties xsi:type="FileObj:FileObjectType">
				<FileObj:File_Path>C:\temp\qwerty.dll</FileObj:File_Path>
			</cybox:Properties>
			<cybox:Relationship xsi:type="cyboxVocabs:ObjectRelationshipVocab-1.1">Deleted</cybox:Relationship>
		</cybox:Related_Object>
	</cybox:Related_Objects>
</cybox:Object>
```	

---

## <a name="Deleted_By"></a> "Deleted_By"

The **source Object** was *Deleted by* the **related Object**. Applicable to a wide range of Objects, particularly in the
context of Objects that were deleted by a Process.

### Inverse

"Created_By"

### Applicable Objects

<table class="table-striped">
 <tbody>
   <tr>
	 <th>Source Object</th>
	 <th>Related Object</th>
	 <th>Description</th>
   </tr>
   <tr>
	 <td>File</td>
	 <td>Process</td>
	 <td>A file was deleted by a process during its execution.</td>
   </tr>
   <tr>
	 <td>Win Registry Key</td>
	 <td>Process</td>
	 <td>A Windows registry key or registry key value was deleted by a process during its execution.</td>
   </tr>
   <tr>
	 <td>Win Service</td>
	 <td>Process</td>
	 <td>A Windows service was deleted by a process during its execution.</td>
   </tr>
   <tr>
	 <td>Mutex</td>
	 <td>Process</td>
	 <td>A mutex was deleted by a process during its execution.</td>
   </tr>
 </tbody>
</table>

### Example

```xml
<cybox:Object id="example:object-e970c3df-0c01-4611-8257-6b01d188983c">
	<cybox:Properties xsi:type="FileObj:FileObjectType">
		<FileObj:File_Path>C:\temp\qwerty.dll</FileObj:File_Path>
	</cybox:Properties>
	<cybox:Related_Objects>
		<cybox:Related_Object id="example:object-c822a70d-7b41-4553-983b-a07fd8c553a0">
			<cybox:Properties xsi:type="ProcessObj:ProcessObjectType">
				<ProcessObj:Image_Info>
					<ProcessObj:File_Name>some_process.exe</ProcessObj:File_Name>
				</ProcessObj:Image_Info>
			</cybox:Properties>
			<cybox:Relationship xsi:type="cyboxVocabs:ObjectRelationshipVocab-1.1">Deleted_By</cybox:Relationship>
		</cybox:Related_Object>
	</cybox:Related_Objects>
</cybox:Object>
```	

---

## <a name="Modified_Properties_Of"></a> "Modified_Properties_Of"

The **source Object** *Modifed the properties of* the **related Object**. Applicable to a wide range of Objects, particularly in the
context of a Process that modified the properties of other Objects.

### Inverse

n/a

### Applicable Objects

<table class="table-striped">
 <tbody>
   <tr>
	 <th>Source Object</th>
	 <th>Related Object</th>
	 <th>Description</th>
   </tr>
   <tr>
	 <td>Process</td>
	 <td>File</td>
	 <td>A process modified the properties of a file during its execution.</td>
   </tr>
   <tr>
	 <td>Process</td>
	 <td>Win Registry Key</td>
	 <td>A process modified the properties of a Windows registry key or registry key value during its execution.</td>
   </tr>
   <tr>
	 <td>Process</td>
	 <td>Win Service</td>
	 <td>A process modified the properties of a Windows service during its execution.</td>
   </tr>
 </tbody>
</table>

### Example

```xml
<cybox:Object id="example:object-c822a70d-7b41-4553-983b-a07fd8c553a0">
	<cybox:Properties xsi:type="ProcessObj:ProcessObjectType">
		<ProcessObj:Image_Info>
			<ProcessObj:File_Name>some_process.exe</ProcessObj:File_Name>
		</ProcessObj:Image_Info>
	</cybox:Properties>
	<cybox:Related_Objects>
		<cybox:Related_Object id="example:object-e970c3df-0c01-4611-8257-6b01d188983c">
			<cybox:Properties xsi:type="FileObj:FileObjectType">
				<FileObj:File_Path>C:\temp\qwerty.dll</FileObj:File_Path>
			</cybox:Properties>
			<cybox:Relationship xsi:type="cyboxVocabs:ObjectRelationshipVocab-1.1">Modified_Properties_Of</cybox:Relationship>
		</cybox:Related_Object>
	</cybox:Related_Objects>
</cybox:Object>
```	

---

## <a name="Properties_Modified_By"></a> "Properties_Modified_By"

The **source Object** had its *Properties modified* by the **related Object**. Applicable to a wide range of Objects, particularly in the context of Objects whose properties were modified by a Process.

### Inverse

n/a

### Applicable Objects

<table class="table-striped">
 <tbody>
   <tr>
	 <th>Source Object</th>
	 <th>Related Object</th>
	 <th>Description</th>
   </tr>
   <tr>
	 <td>File</td>
	 <td>Process</td>
	 <td>A file had its properties modified by a process during its execution.</td>
   </tr>
   <tr>
	 <td>Win Registry Key</td>
	 <td>Process</td>
	 <td>A Windows registry key or registry key value had its properties modified by a process during its execution.</td>
   </tr>
   <tr>
	 <td>Win Service</td>
	 <td>Process</td>
	 <td>A Windows service had its properties modified by a process during its execution.</td>
   </tr>
 </tbody>
</table>

### Example

```xml
<cybox:Object id="example:object-e970c3df-0c01-4611-8257-6b01d188983c">
	<cybox:Properties xsi:type="FileObj:FileObjectType">
		<FileObj:File_Path>C:\temp\qwerty.dll</FileObj:File_Path>
	</cybox:Properties>
	<cybox:Related_Objects>
		<cybox:Related_Object id="example:object-c822a70d-7b41-4553-983b-a07fd8c553a0">
			<cybox:Properties xsi:type="ProcessObj:ProcessObjectType">
				<ProcessObj:Image_Info>
					<ProcessObj:File_Name>some_process.exe</ProcessObj:File_Name>
				</ProcessObj:Image_Info>
			</cybox:Properties>
			<cybox:Relationship xsi:type="cyboxVocabs:ObjectRelationshipVocab-1.1">Properties_Modified_By</cybox:Relationship>
		</cybox:Related_Object>
	</cybox:Related_Objects>
</cybox:Object>
```	

---

## <a name="Downloaded_From"></a> "Downloaded_From"

The **source Object** was *Downloaded from* the **related Object**. Commonly used for expressing the fact that a file was downloaded from some network location.

### Inverse

n/a

### Applicable Objects

<table class="table-striped">
 <tbody>
   <tr>
	 <th>Source Object</th>
	 <th>Related Object</th>
	 <th>Description</th>
   </tr>
   <tr>
	 <td>File</td>
	 <td>URI</td>
	 <td>A file was downloaded from some particular URL.</td>
   </tr>
   <tr>
	 <td>File</td>
	 <td>Domain Name</td>
	 <td>A file was downloaded from some particular domain name.</td>
   </tr>
   <tr>
	 <td>File</td>
	 <td>Address</td>
	 <td>A file was downloaded from some particular IP address.</td>
   </tr>
   <tr>
	 <td>File</td>
	 <td>Hostname</td>
	 <td>A file was downloaded from some device identified by a particular hostname.</td>
   </tr>
 </tbody>
</table>

### Example

```xml
<cybox:Object id="example:object-e970c3df-0c01-4611-8257-6b01d188983c">
	<cybox:Properties xsi:type="FileObj:FileObjectType">
		<FileObj:File_Path>C:\temp\qwerty.dll</FileObj:File_Path>
	</cybox:Properties>
	<cybox:Related_Objects>
		<cybox:Related_Object id="example:object-d9f7b338-a20f-47b2-9efd-21f5a42b54f1">
			<cybox:Properties xsi:type="DomainNameObj:DomainNameObjectType">
				<DomainNameObj:Value>example.com</DomainNameObj:Value>
			</cybox:Properties>
			<cybox:Relationship xsi:type="cyboxVocabs:ObjectRelationshipVocab-1.1">Downloaded_From</cybox:Relationship>
		</cybox:Related_Object>
	</cybox:Related_Objects>
</cybox:Object>
```	

---

## <a name="Downloaded"></a> "Downloaded"

The **source Object** *Downloaded* the **related Object**. Commonly used for expressing the fact that a process downloaded a file.

### Inverse

"Uploaded"

### Applicable Objects

<table class="table-striped">
 <tbody>
   <tr>
	 <th>Source Object</th>
	 <th>Related Object</th>
	 <th>Description</th>
   </tr>
   <tr>
	 <td>Process</td>
	 <td>File</td>
	 <td>A process downloaded a particular file during its execution.</td>
   </tr>
 </tbody>
</table>

### Example

```xml
<cybox:Object id="example:object-c822a70d-7b41-4553-983b-a07fd8c553a0">
	<cybox:Properties xsi:type="ProcessObj:ProcessObjectType">
		<ProcessObj:Image_Info>
			<ProcessObj:File_Name>some_process.exe</ProcessObj:File_Name>
		</ProcessObj:Image_Info>
	</cybox:Properties>
	<cybox:Related_Objects>
		<cybox:Related_Object id="example:object-e970c3df-0c01-4611-8257-6b01d188983c">
			<cybox:Properties xsi:type="FileObj:FileObjectType">
				<FileObj:File_Path>C:\temp\qwerty.dll</FileObj:File_Path>
			</cybox:Properties>
			<cybox:Relationship xsi:type="cyboxVocabs:ObjectRelationshipVocab-1.1">Downloaded</cybox:Relationship>
		</cybox:Related_Object>
	</cybox:Related_Objects>
</cybox:Object>
```	

---

## <a name="Downloaded_To"></a> "Downloaded_To"

The **source Object** was *Downloaded to* the **related Object**. Commonly used for expressing the fact that a file or URL that refers to a file was downloaded as another file (e.g., "abcd.exe" downloaded as "fun.jpg") or to a particular location.

### Inverse

"Uploaded_To"

### Applicable Objects

<table class="table-striped">
 <tbody>
   <tr>
	 <th>Source Object</th>
	 <th>Related Object</th>
	 <th>Description</th>
   </tr>
   <tr>
	 <td>URI</td>
	 <td>File</td>
	 <td>A file specified by a URL was downloaded and stored as another file or at some particular location.</td>
   </tr>
   <tr>
	 <td>File</td>
	 <td>File</td>
	 <td>A file was downloaded and stored as another file or at some particular location.</td>
   </tr>
 </tbody>
</table>

### Example

```xml
<cybox:Object id="example:object-51b8828d-3068-4a6d-96e9-7b19d3b3ef1a">
	<cybox:Properties xsi:type="URIObj:URIObjectType" type="URL">
		<URIObj:Value>http://example.com/asdfg.jpg</URIObj:Value>
	</cybox:Properties>
	<cybox:Related_Objects>
		<cybox:Related_Object id="example:object-31a600e7-7357-4845-9604-70327c9a7dfc">
			<cybox:Properties xsi:type="FileObj:FileObjectType">
				<FileObj:File_Path>/usr/tmp/test.bin</FileObj:File_Path>
			</cybox:Properties>
			<cybox:Relationship xsi:type="cyboxVocabs:ObjectRelationshipVocab-1.1">Downloaded_To</cybox:Relationship>
		</cybox:Related_Object>
	</cybox:Related_Objects>
</cybox:Object>
```	

---

## <a name="Downloaded_By"></a> "Downloaded_By"

The **source Object** was *Downloaded by* the **related Object**. Commonly used for expressing the fact that a file was downloaded by a process.

### Inverse

"Uploaded_By"

### Applicable Objects

<table class="table-striped">
 <tbody>
   <tr>
	 <th>Source Object</th>
	 <th>Related Object</th>
	 <th>Description</th>
   </tr>
   <tr>
	 <td>File</td>
	 <td>Process</td>
	 <td>A file was downloaded by a particular process during its execution.</td>
   </tr>
 </tbody>
</table>

### Example

```xml
<cybox:Object id="example:object-e970c3df-0c01-4611-8257-6b01d188983c">
	<cybox:Properties xsi:type="FileObj:FileObjectType">
		<FileObj:File_Path>C:\temp\qwerty.dll</FileObj:File_Path>
	</cybox:Properties>
	<cybox:Related_Objects>
		<cybox:Related_Object id="example:object-c822a70d-7b41-4553-983b-a07fd8c553a0">
			<cybox:Properties xsi:type="ProcessObj:ProcessObjectType">
				<ProcessObj:Image_Info>
					<ProcessObj:File_Name>some_process.exe</ProcessObj:File_Name>
				</ProcessObj:Image_Info>
			</cybox:Properties>
			<cybox:Relationship xsi:type="cyboxVocabs:ObjectRelationshipVocab-1.1">Downloaded_By</cybox:Relationship>
		</cybox:Related_Object>
	</cybox:Related_Objects>
</cybox:Object>
```	

---

## <a name="Uploaded"></a> "Uploaded"

The **source Object** *Uploaded* the **related Object**. Commonly used for expressing the fact that a process uploaded a particular file.

### Inverse

"Downloaded"

### Applicable Objects

<table class="table-striped">
 <tbody>
   <tr>
	 <th>Source Object</th>
	 <th>Related Object</th>
	 <th>Description</th>
   </tr>
   <tr>
	 <td>Process</td>
	 <td>File</td>
	 <td>A process uploaded a particular file during its execution.</td>
   </tr>
 </tbody>
</table>

### Example

```xml
<cybox:Object id="example:object-c822a70d-7b41-4553-983b-a07fd8c553a0">
	<cybox:Properties xsi:type="ProcessObj:ProcessObjectType">
		<ProcessObj:Image_Info>
			<ProcessObj:File_Name>some_process.exe</ProcessObj:File_Name>
		</ProcessObj:Image_Info>
	</cybox:Properties>
	<cybox:Related_Objects>
		<cybox:Related_Object id="example:object-e970c3df-0c01-4611-8257-6b01d188983c">
			<cybox:Properties xsi:type="FileObj:FileObjectType">
				<FileObj:File_Path>C:\temp\qwerty.dll</FileObj:File_Path>
			</cybox:Properties>
			<cybox:Relationship xsi:type="cyboxVocabs:ObjectRelationshipVocab-1.1">Uploaded</cybox:Relationship>
		</cybox:Related_Object>
	</cybox:Related_Objects>
</cybox:Object>
```	

---

## <a name="Uploaded_By"></a> "Uploaded_By"

The **source Object** was *Uploaded by* the **related Object**. Commonly used for expressing the fact that a file was uploaded by a process.

### Inverse

"Downloaded_By"

### Applicable Objects

<table class="table-striped">
 <tbody>
   <tr>
	 <th>Source Object</th>
	 <th>Related Object</th>
	 <th>Description</th>
   </tr>
   <tr>
	 <td>File</td>
	 <td>Process</td>
	 <td>A file was uploaded by a particular process during its execution.</td>
   </tr>
 </tbody>
</table>

### Example

```xml
<cybox:Object id="example:object-e970c3df-0c01-4611-8257-6b01d188983c">
	<cybox:Properties xsi:type="FileObj:FileObjectType">
		<FileObj:File_Path>C:\temp\qwerty.dll</FileObj:File_Path>
	</cybox:Properties>
	<cybox:Related_Objects>
		<cybox:Related_Object id="example:object-c822a70d-7b41-4553-983b-a07fd8c553a0">
			<cybox:Properties xsi:type="ProcessObj:ProcessObjectType">
				<ProcessObj:Image_Info>
					<ProcessObj:File_Name>some_process.exe</ProcessObj:File_Name>
				</ProcessObj:Image_Info>
			</cybox:Properties>
			<cybox:Relationship xsi:type="cyboxVocabs:ObjectRelationshipVocab-1.1">Uploaded_By</cybox:Relationship>
		</cybox:Related_Object>
	</cybox:Related_Objects>
</cybox:Object>
```	

---

## <a name="Uploaded_To"></a> "Uploaded_To"

The **source Object** was *Uploaded to* the **related Object**. Commonly used for expressing the fact that a file was uploaded to a particular network location.

### Inverse

n/a

### Applicable Objects

<table class="table-striped">
 <tbody>
   <tr>
	 <th>Source Object</th>
	 <th>Related Object</th>
	 <th>Description</th>
   </tr>
   <tr>
	 <td>File</td>
	 <td>URI</td>
	 <td>A file was uploaded to a particular URL.</td>
   </tr>
   <tr>
	 <td>File</td>
	 <td>Domain Name</td>
	 <td>A file was uploaded to a particular domain name.</td>
   </tr>
   <tr>
	 <td>File</td>
	 <td>Address</td>
	 <td>A file was uploaded to a particular IP address.</td>
   </tr>
   <tr>
	 <td>File</td>
	 <td>Hostname</td>
	 <td>A file was uploaded to a device identified by a particular hostname.</td>
   </tr>
 </tbody>
</table>

### Example

```xml
<cybox:Object id="example:object-e970c3df-0c01-4611-8257-6b01d188983c">
	<cybox:Properties xsi:type="FileObj:FileObjectType">
		<FileObj:File_Path>C:\temp\qwerty.dll</FileObj:File_Path>
	</cybox:Properties>
	<cybox:Related_Objects>
		<cybox:Related_Object id="example:object-0eaf497e-1062-4d52-97fa-670c4426ff3b">
			<cybox:Properties xsi:type="AddressObj:AddressObjectType" category="ipv4-addr">
				<AddressObj:Address_Value>10.1.2.3</AddressObj:Address_Value>
			</cybox:Properties>
			<cybox:Relationship xsi:type="cyboxVocabs:ObjectRelationshipVocab-1.1">Uploaded_To</cybox:Relationship>
		</cybox:Related_Object>
	</cybox:Related_Objects>
</cybox:Object>
```	

---

## <a name="Sent_To"></a> "Sent_To"

The **source Object** was *Sent to* the **related Object**. Commonly used for expressing the fact that a file was sent to a particular email address.

### Inverse

"Received_From"

### Applicable Objects

<table class="table-striped">
 <tbody>
   <tr>
	 <th>Source Object</th>
	 <th>Related Object</th>
	 <th>Description</th>
   </tr>
   <tr>
	 <td>File</td>
	 <td>Address</td>
	 <td>A file was sent to a particular email address.</td>
   </tr>
 </tbody>
</table>

### Example

```xml
<cybox:Object id="example:object-e970c3df-0c01-4611-8257-6b01d188983c">
	<cybox:Properties xsi:type="FileObj:FileObjectType">
		<FileObj:File_Path>C:\temp\qwerty.dll</FileObj:File_Path>
	</cybox:Properties>
	<cybox:Related_Objects>
		<cybox:Related_Object id="example:object-54710212-ca56-4eb6-8b4a-f8bf083303ae">
			<cybox:Properties xsi:type="AddressObj:AddressObjectType" category="e-mail">
				<AddressObj:Address_Value>bob@example.com</AddressObj:Address_Value>
			</cybox:Properties>
			<cybox:Relationship xsi:type="cyboxVocabs:ObjectRelationshipVocab-1.1">Sent_To</cybox:Relationship>
		</cybox:Related_Object>
	</cybox:Related_Objects>
</cybox:Object>
```	

---

## <a name="Received_From"></a> "Received_From"

The **source Object** was *Received from* the **related Object**. Commonly used for expressing the fact that a file was received from an email sent from a particular email address.

### Inverse

"Sent_To"

### Applicable Objects

<table class="table-striped">
 <tbody>
   <tr>
	 <th>Source Object</th>
	 <th>Related Object</th>
	 <th>Description</th>
   </tr>
   <tr>
	 <td>File</td>
	 <td>Address</td>
	 <td>A file was received from an email sent from particular email address.</td>
   </tr>
 </tbody>
</table>

### Example

```xml
<cybox:Object id="example:object-e970c3df-0c01-4611-8257-6b01d188983c">
	<cybox:Properties xsi:type="FileObj:FileObjectType">
		<FileObj:File_Path>C:\temp\qwerty.dll</FileObj:File_Path>
	</cybox:Properties>
	<cybox:Related_Objects>
		<cybox:Related_Object id="example:object-238f4ee7-d986-4c6c-9e50-4474270582a2">
			<cybox:Properties xsi:type="AddressObj:AddressObjectType" category="e-mail">
				<AddressObj:Address_Value>sue@example.com</AddressObj:Address_Value>
			</cybox:Properties>
			<cybox:Relationship xsi:type="cyboxVocabs:ObjectRelationshipVocab-1.1">Received_From</cybox:Relationship>
		</cybox:Related_Object>
	</cybox:Related_Objects>
</cybox:Object>
```	

---

## <a name="Values_Enumerated"></a> "Values_Enumerated"

The **source Object** *Enumerated the values* of the **related Object**. Commonly used for expressing the fact that a process enumerated the values of a particular Windows registry key.

### Inverse

n/a

### Applicable Objects

<table class="table-striped">
 <tbody>
   <tr>
	 <th>Source Object</th>
	 <th>Related Object</th>
	 <th>Description</th>
   </tr>
   <tr>
	 <td>Process</td>
	 <td>Win Registry Key</td>
	 <td>A process enumerated the values of a particular Windows registry key during its execution.</td>
   </tr>
 </tbody>
</table>

### Example

```xml
<cybox:Object id="example:object-c822a70d-7b41-4553-983b-a07fd8c553a0">
	<cybox:Properties xsi:type="ProcessObj:ProcessObjectType">
		<ProcessObj:Image_Info>
			<ProcessObj:File_Name>some_process.exe</ProcessObj:File_Name>
		</ProcessObj:Image_Info>
	</cybox:Properties>
	<cybox:Related_Objects>
		<cybox:Related_Object id="example:object-0eaf497e-1062-4d52-97fa-670c4426ff3b">
			<cybox:Properties xsi:type="WinRegistryKeyObj:WindowsRegistryKeyObjectType">
				<WinRegistryKeyObj:Key>System\services\ACPI</WinRegistryKeyObj:Key>
				<WinRegistryKeyObj:Hive>HKEY_LOCAL_MACHINE</WinRegistryKeyObj:Hive>
			</cybox:Properties>
			<cybox:Relationship xsi:type="cyboxVocabs:ObjectRelationshipVocab-1.1">Values_Enumerated</cybox:Relationship>
		</cybox:Related_Object>
	</cybox:Related_Objects>
</cybox:Object>
```	

---

## <a name="Values_Enumerated_By"></a> "Values_Enumerated_By"

The **source Object** had its *Values enumerated* by the **related Object**. Commonly used for expressing the fact that a Windows registry key had its values enumerated by a particular process.

### Inverse

n/a

### Applicable Objects

<table class="table-striped">
 <tbody>
   <tr>
	 <th>Source Object</th>
	 <th>Related Object</th>
	 <th>Description</th>
   </tr>
   <tr>
	 <td>Win Registry Key</td>
	 <td>Process</td>
	 <td>A Windows registry key had its values enumerated by a particular process during its execution.</td>
   </tr>
 </tbody>
</table>

### Example

```xml
<cybox:Object id="example:object-0eaf497e-1062-4d52-97fa-670c4426ff3b">
	<cybox:Properties xsi:type="WinRegistryKeyObj:WindowsRegistryKeyObjectType">
		<WinRegistryKeyObj:Key>System\services\ACPI</WinRegistryKeyObj:Key>
		<WinRegistryKeyObj:Hive>HKEY_LOCAL_MACHINE</WinRegistryKeyObj:Hive>
	</cybox:Properties>
	<cybox:Related_Objects>
		<cybox:Related_Object id="example:object-c822a70d-7b41-4553-983b-a07fd8c553a0">
			<cybox:Properties xsi:type="ProcessObj:ProcessObjectType">
				<ProcessObj:Image_Info>
					<ProcessObj:File_Name>some_process.exe</ProcessObj:File_Name>
				</ProcessObj:Image_Info>
			</cybox:Properties>
			<cybox:Relationship xsi:type="cyboxVocabs:ObjectRelationshipVocab-1.1">Values_Enumerated_By</cybox:Relationship>
		</cybox:Related_Object>
	</cybox:Related_Objects>
</cybox:Object>
```	

---

## <a name="Killed"></a> "Killed"

The **source Object** *Killed* the **related Object**. Commonly used for expressing the fact that a process killed (or terminated) another process or thread.

### Inverse

"Created"

### Applicable Objects

<table class="table-striped">
 <tbody>
   <tr>
	 <th>Source Object</th>
	 <th>Related Object</th>
	 <th>Description</th>
   </tr>
   <tr>
	 <td>Process</td>
	 <td>Process</td>
	 <td>A process killed (or terminated) another process during its execution.</td>
   </tr>
   <tr>
	 <td>Process</td>
	 <td>Win Thread</td>
	 <td>A process killed (or terminated) a thread during its execution.</td>
   </tr>
 </tbody>
</table>

### Example

```xml
<cybox:Object id="example:object-c822a70d-7b41-4553-983b-a07fd8c553a0">
	<cybox:Properties xsi:type="ProcessObj:ProcessObjectType">
		<ProcessObj:Image_Info>
			<ProcessObj:File_Name>some_process.exe</ProcessObj:File_Name>
		</ProcessObj:Image_Info>
	</cybox:Properties>
	<cybox:Related_Objects>
		<cybox:Related_Object id="example:object-b464a2a1-876b-4e29-9b5f-705f66ca1327">
			<cybox:Properties xsi:type="ProcessObj:ProcessObjectType">
				<ProcessObj:Image_Info>
					<ProcessObj:File_Name>another_process.exe</ProcessObj:File_Name>
				</ProcessObj:Image_Info>
			</cybox:Properties>
			<cybox:Relationship xsi:type="cyboxVocabs:ObjectRelationshipVocab-1.1">Killed</cybox:Relationship>
		</cybox:Related_Object>
	</cybox:Related_Objects>
</cybox:Object>
```	

---

## <a name="Killed_By"></a> "Killed_By"

The **source Object** was *Killed by* the **related Object**. Commonly used for expressing the fact that a process or thread was killed (or terminated) by another process.

### Inverse

"Created_By"

### Applicable Objects

<table class="table-striped">
 <tbody>
   <tr>
	 <th>Source Object</th>
	 <th>Related Object</th>
	 <th>Description</th>
   </tr>
   <tr>
	 <td>Process</td>
	 <td>Process</td>
	 <td>A process was killed (or terminated) by another process during its execution.</td>
   </tr>
   <tr>
	 <td>Win Thread</td>
	 <td>Process</td>
	 <td>A Windows thread was killed (or terminated) by a process during its execution.</td>
   </tr>
 </tbody>
</table>

### Example

```xml
<cybox:Object id="example:object-b464a2a1-876b-4e29-9b5f-705f66ca1327">
	<cybox:Properties xsi:type="ProcessObj:ProcessObjectType">
		<ProcessObj:Image_Info>
			<ProcessObj:File_Name>another_process.exe</ProcessObj:File_Name>
		</ProcessObj:Image_Info>
	</cybox:Properties>
	<cybox:Related_Objects>
		<cybox:Related_Object id="example:object-c822a70d-7b41-4553-983b-a07fd8c553a0">
			<cybox:Properties xsi:type="ProcessObj:ProcessObjectType">
				<ProcessObj:Image_Info>
					<ProcessObj:File_Name>some_process.exe</ProcessObj:File_Name>
				</ProcessObj:Image_Info>
			</cybox:Properties>
			<cybox:Relationship xsi:type="cyboxVocabs:ObjectRelationshipVocab-1.1">Killed_By</cybox:Relationship>
		</cybox:Related_Object>
	</cybox:Related_Objects>
</cybox:Object>
```	

---

## <a name="Locked"></a> "Locked"

The **source Object** *Locked* the **related Object**. Commonly used for expressing the fact that a process locked (in terms of read, write, or delete access) a particular file.

### Inverse

"Unlocked"

### Applicable Objects

<table class="table-striped">
 <tbody>
   <tr>
	 <th>Source Object</th>
	 <th>Related Object</th>
	 <th>Description</th>
   </tr>
   <tr>
	 <td>Process</td>
	 <td>File</td>
	 <td>A process locked (in terms of read, write, or delete access) a particular file during its execution.</td>
   </tr>
 </tbody>
</table>

### Example

```xml
<cybox:Object id="example:object-c822a70d-7b41-4553-983b-a07fd8c553a0">
	<cybox:Properties xsi:type="ProcessObj:ProcessObjectType">
		<ProcessObj:Image_Info>
			<ProcessObj:File_Name>some_process.exe</ProcessObj:File_Name>
		</ProcessObj:Image_Info>
	</cybox:Properties>
	<cybox:Related_Objects>
		<cybox:Related_Object id="example:object-e970c3df-0c01-4611-8257-6b01d188983c">
			<cybox:Properties xsi:type="FileObj:FileObjectType">
				<FileObj:File_Path>C:\temp\qwerty.dll</FileObj:File_Path>
			</cybox:Properties>
			<cybox:Relationship xsi:type="cyboxVocabs:ObjectRelationshipVocab-1.1">Locked</cybox:Relationship>
		</cybox:Related_Object>
	</cybox:Related_Objects>
</cybox:Object>
```	

---

## <a name="Locked_By"></a> "Locked_By"

The **source Object** was *Locked by* the **related Object**. Commonly used for expressing the fact that a file was locked (in terms of read, write, or delete access) by a particular process.

### Inverse

"Unlocked_By"

### Applicable Objects

<table class="table-striped">
 <tbody>
   <tr>
	 <th>Source Object</th>
	 <th>Related Object</th>
	 <th>Description</th>
   </tr>
   <tr>
	 <td>File</td>
	 <td>Process</td>
	 <td>A file was locked (in terms of read, write, or delete access) by a particular process during its execution.</td>
   </tr>
 </tbody>
</table>

### Example

```xml
<cybox:Object id="example:object-e970c3df-0c01-4611-8257-6b01d188983c">
	<cybox:Properties xsi:type="FileObj:FileObjectType">
		<FileObj:File_Path>C:\temp\qwerty.dll</FileObj:File_Path>
	</cybox:Properties>
	<cybox:Related_Objects>
		<cybox:Related_Object id="example:object-c822a70d-7b41-4553-983b-a07fd8c553a0">
			<cybox:Properties xsi:type="ProcessObj:ProcessObjectType">
				<ProcessObj:Image_Info>
					<ProcessObj:File_Name>some_process.exe</ProcessObj:File_Name>
				</ProcessObj:Image_Info>
			</cybox:Properties>
			<cybox:Relationship xsi:type="cyboxVocabs:ObjectRelationshipVocab-1.1">Locked_By</cybox:Relationship>
		</cybox:Related_Object>
	</cybox:Related_Objects>
</cybox:Object>
```	

---

## <a name="Unlocked"></a> "Unlocked"

The **source Object** *Unlocked* the **related Object**. Commonly used for expressing the fact that a process unlocked (in terms of read, write, or delete access) a particular file.

### Inverse

"Locked"

### Applicable Objects

<table class="table-striped">
 <tbody>
   <tr>
	 <th>Source Object</th>
	 <th>Related Object</th>
	 <th>Description</th>
   </tr>
   <tr>
	 <td>Process</td>
	 <td>File</td>
	 <td>A process unlocked (in terms of read, write, or delete access) a particular file during its execution.</td>
   </tr>
 </tbody>
</table>

### Example

```xml
<cybox:Object id="example:object-c822a70d-7b41-4553-983b-a07fd8c553a0">
	<cybox:Properties xsi:type="ProcessObj:ProcessObjectType">
		<ProcessObj:Image_Info>
			<ProcessObj:File_Name>some_process.exe</ProcessObj:File_Name>
		</ProcessObj:Image_Info>
	</cybox:Properties>
	<cybox:Related_Objects>
		<cybox:Related_Object id="example:object-e970c3df-0c01-4611-8257-6b01d188983c">
			<cybox:Properties xsi:type="FileObj:FileObjectType">
				<FileObj:File_Path>C:\temp\qwerty.dll</FileObj:File_Path>
			</cybox:Properties>
			<cybox:Relationship xsi:type="cyboxVocabs:ObjectRelationshipVocab-1.1">Unlocked</cybox:Relationship>
		</cybox:Related_Object>
	</cybox:Related_Objects>
</cybox:Object>
```	

---

## <a name="Unlocked_By"></a> "Unlocked_By"

The **source Object** was *Unlocked by* the **related Object**. Commonly used for expressing the fact that a file was unlocked (in terms of read, write, or delete access) by a particular process.

### Inverse

"Locked_By"

### Applicable Objects

<table class="table-striped">
 <tbody>
   <tr>
	 <th>Source Object</th>
	 <th>Related Object</th>
	 <th>Description</th>
   </tr>
   <tr>
	 <td>File</td>
	 <td>Process</td>
	 <td>A file was unlocked (in terms of read, write, or delete access) by a particular process during its execution.</td>
   </tr>
 </tbody>
</table>

### Example

```xml
<cybox:Object id="example:object-e970c3df-0c01-4611-8257-6b01d188983c">
	<cybox:Properties xsi:type="FileObj:FileObjectType">
		<FileObj:File_Path>C:\temp\qwerty.dll</FileObj:File_Path>
	</cybox:Properties>
	<cybox:Related_Objects>
		<cybox:Related_Object id="example:object-c822a70d-7b41-4553-983b-a07fd8c553a0">
			<cybox:Properties xsi:type="ProcessObj:ProcessObjectType">
				<ProcessObj:Image_Info>
					<ProcessObj:File_Name>some_process.exe</ProcessObj:File_Name>
				</ProcessObj:Image_Info>
			</cybox:Properties>
			<cybox:Relationship xsi:type="cyboxVocabs:ObjectRelationshipVocab-1.1">Unlocked_By</cybox:Relationship>
		</cybox:Related_Object>
	</cybox:Related_Objects>
</cybox:Object>
```	

---

## <a name="Listened_On"></a> "Listened_On"

The **source Object** *Listened on* the **related Object**. Commonly used for expressing the fact that a process listened on a particular port or socket.

### Inverse

n/a

### Applicable Objects

<table class="table-striped">
 <tbody>
   <tr>
	 <th>Source Object</th>
	 <th>Related Object</th>
	 <th>Description</th>
   </tr>
   <tr>
	 <td>Process</td>
	 <td>Port</td>
	 <td>A process listened on a particular port during its execution.</td>
   </tr>
   <tr>
	 <td>Process</td>
	 <td>Network Socket</td>
	 <td>A process listened on a particular network socket during its execution.</td>
   </tr>
 </tbody>
</table>

### Example

```xml
<cybox:Object id="example:object-c822a70d-7b41-4553-983b-a07fd8c553a0">
	<cybox:Properties xsi:type="ProcessObj:ProcessObjectType">
		<ProcessObj:Image_Info>
			<ProcessObj:File_Name>some_process.exe</ProcessObj:File_Name>
		</ProcessObj:Image_Info>
	</cybox:Properties>
	<cybox:Related_Objects>
		<cybox:Related_Object id="example:object-892a4b26-59af-4dcf-88f3-f55f3837fbde">
			<cybox:Properties xsi:type="PortObj:PortObjectType">
			  <PortObj:Port_Value>1234</PortObj:Port_Value>
			</cybox:Properties>
			<cybox:Relationship xsi:type="cyboxVocabs:ObjectRelationshipVocab-1.1">Listened_On</cybox:Relationship>
		</cybox:Related_Object>
	</cybox:Related_Objects>
</cybox:Object>
```	

---

## <a name="Renamed"></a> "Renamed"

The **source Object** *Renamed* the **related Object**. Commonly used for expressing the fact that a process renamed a particular file.

### Inverse

n/a

### Applicable Objects

<table class="table-striped">
 <tbody>
   <tr>
	 <th>Source Object</th>
	 <th>Related Object</th>
	 <th>Description</th>
   </tr>
   <tr>
	 <td>Process</td>
	 <td>File</td>
	 <td>A process renamed a file during its execution.</td>
   </tr>
 </tbody>
</table>

### Example

```xml
<cybox:Object id="example:object-c822a70d-7b41-4553-983b-a07fd8c553a0">
	<cybox:Properties xsi:type="ProcessObj:ProcessObjectType">
		<ProcessObj:Image_Info>
			<ProcessObj:File_Name>some_process.exe</ProcessObj:File_Name>
		</ProcessObj:Image_Info>
	</cybox:Properties>
	<cybox:Related_Objects>
		<cybox:Related_Object id="example:object-e970c3df-0c01-4611-8257-6b01d188983c">
			<cybox:Properties xsi:type="FileObj:FileObjectType">
				<FileObj:File_Path>C:\temp\qwerty.dll</FileObj:File_Path>
			</cybox:Properties>
			<cybox:Relationship xsi:type="cyboxVocabs:ObjectRelationshipVocab-1.1">Renamed</cybox:Relationship>
		</cybox:Related_Object>
	</cybox:Related_Objects>
</cybox:Object>
```	

---

## <a name="Renamed_By"></a> "Renamed_By"

The **source Object** was *Renamed by* the **related Object**.  Commonly used for expressing the fact that a file was renamed by a particular process.

### Inverse

n/a

### Applicable Objects

<table class="table-striped">
 <tbody>
   <tr>
	 <th>Source Object</th>
	 <th>Related Object</th>
	 <th>Description</th>
   </tr>
   <tr>
	 <td>File</td>
	 <td>Process</td>
	 <td>A file was renamed by a particular process during its execution.</td>
   </tr>
 </tbody>
</table>

### Example

```xml
<cybox:Object id="example:object-e970c3df-0c01-4611-8257-6b01d188983c">
	<cybox:Properties xsi:type="FileObj:FileObjectType">
		<FileObj:File_Path>C:\temp\qwerty.dll</FileObj:File_Path>
	</cybox:Properties>
	<cybox:Related_Objects>
		<cybox:Related_Object id="example:object-c822a70d-7b41-4553-983b-a07fd8c553a0">
			<cybox:Properties xsi:type="ProcessObj:ProcessObjectType">
				<ProcessObj:Image_Info>
					<ProcessObj:File_Name>some_process.exe</ProcessObj:File_Name>
				</ProcessObj:Image_Info>
			</cybox:Properties>
			<cybox:Relationship xsi:type="cyboxVocabs:ObjectRelationshipVocab-1.1">Renamed_By</cybox:Relationship>
		</cybox:Related_Object>
	</cybox:Related_Objects>
</cybox:Object>
```	

---

## <a name="Renamed_From"></a> "Renamed_From"

The **source Object** was *Renamed from* the **related Object**.  Commonly used for expressing the fact that a file was renamed from a version of the file with a different name.

### Inverse

n/a

### Applicable Objects

<table class="table-striped">
 <tbody>
   <tr>
	 <th>Source Object</th>
	 <th>Related Object</th>
	 <th>Description</th>
   </tr>
   <tr>
	 <td>File</td>
	 <td>File</td>
	 <td>A file was renamed from another version of the file with a different name.</td>
   </tr>
 </tbody>
</table>

### Example

```xml
<cybox:Object id="example:object-e970c3df-0c01-4611-8257-6b01d188983c">
	<cybox:Properties xsi:type="FileObj:FileObjectType">
		<FileObj:File_Path>C:\temp\qwerty.dll</FileObj:File_Path>
	</cybox:Properties>
	<cybox:Related_Objects>
		<cybox:Related_Object id="example:object-d64e3ee9-39bf-4149-ae77-9b2df9c203e3">
			<cybox:Properties xsi:type="FileObj:FileObjectType">
				<FileObj:File_Path>C:\temp\asdfg.bin</FileObj:File_Path>
			</cybox:Properties>
			<cybox:Relationship xsi:type="cyboxVocabs:ObjectRelationshipVocab-1.1">Renamed_From</cybox:Relationship>
		</cybox:Related_Object>
	</cybox:Related_Objects>
</cybox:Object>
```	

---

## <a name="Renamed_To"></a> "Renamed_To"

The **source Object** was *Renamed to* the **related Object**.  Commonly used for expressing the fact that a file was renamed to a version of the file with a different name.

### Inverse

n/a

### Applicable Objects

<table class="table-striped">
 <tbody>
   <tr>
	 <th>Source Object</th>
	 <th>Related Object</th>
	 <th>Description</th>
   </tr>
   <tr>
	 <td>File</td>
	 <td>File</td>
	 <td>A file was renamed to another version of the file with a different name.</td>
   </tr>
 </tbody>
</table>

### Example

```xml
<cybox:Object id="example:object-d64e3ee9-39bf-4149-ae77-9b2df9c203e3">
	<cybox:Properties xsi:type="FileObj:FileObjectType">
		<FileObj:File_Path>C:\temp\asdfg.bin</FileObj:File_Path>
	</cybox:Properties>
	<cybox:Related_Objects>
		<cybox:Related_Object id="example:object-e970c3df-0c01-4611-8257-6b01d188983c">
			<cybox:Properties xsi:type="FileObj:FileObjectType">
				<FileObj:File_Path>C:\temp\qwerty.dll</FileObj:File_Path>
			</cybox:Properties>
			<cybox:Relationship xsi:type="cyboxVocabs:ObjectRelationshipVocab-1.1">Renamed_To</cybox:Relationship>
		</cybox:Related_Object>
	</cybox:Related_Objects>
</cybox:Object>
```	

---

## <a name="Renamed_To"></a> "Renamed_To"

The **source Object** was *Renamed to* the **related Object**.  Commonly used for expressing the fact that a file was renamed to a version of the file with a different name.

### Inverse

n/a

### Applicable Objects

<table class="table-striped">
 <tbody>
   <tr>
	 <th>Source Object</th>
	 <th>Related Object</th>
	 <th>Description</th>
   </tr>
   <tr>
	 <td>File</td>
	 <td>File</td>
	 <td>A file was renamed to another version of the file with a different name.</td>
   </tr>
 </tbody>
</table>

### Example

```xml
<cybox:Object id="example:object-d64e3ee9-39bf-4149-ae77-9b2df9c203e3">
	<cybox:Properties xsi:type="FileObj:FileObjectType">
		<FileObj:File_Path>C:\temp\asdfg.bin</FileObj:File_Path>
	</cybox:Properties>
	<cybox:Related_Objects>
		<cybox:Related_Object id="example:object-e970c3df-0c01-4611-8257-6b01d188983c">
			<cybox:Properties xsi:type="FileObj:FileObjectType">
				<FileObj:File_Path>C:\temp\qwerty.dll</FileObj:File_Path>
			</cybox:Properties>
			<cybox:Relationship xsi:type="cyboxVocabs:ObjectRelationshipVocab-1.1">Renamed_To</cybox:Relationship>
		</cybox:Related_Object>
	</cybox:Related_Objects>
</cybox:Object>
```	

---

## <a name="Contains"></a> "Contains"

The **source Object** *Contains* the **related Object**.  Used for expressing the fact that an object contains another object inside of it. 

### Inverse

n/a

### Applicable Objects

<table class="table-striped">
 <tbody>
   <tr>
	 <th>Source Object</th>
	 <th>Related Object</th>
	 <th>Description</th>
   </tr>
   <tr>
	 <td>File</td>
	 <td>File</td>
	 <td>A file contains another file inside of it (e.g. appended to it).</td>
   </tr>
   <tr>
	 <td>Archive File</td>
	 <td>File</td>
	 <td>An archive file contains another file inside of it.</td>
   </tr>
   <tr>
	 <td>Email Message</td>
	 <td>File</td>
	 <td>An email message contains a file as an attachment.</td>
   </tr>
   <tr>
	 <td>Email Message</td>
	 <td>Link</td>
	 <td>An email message contains a link within its message body.</td>
   </tr>
   <tr>
	 <td>URI</td>
	 <td>Domain Name</td>
	 <td>A URL contains a domain name as part of its structure.</td>
   </tr>
   <tr>
	 <td>DNS Record</td>
	 <td>Address</td>
	 <td>A DNS record contains an IP address that resolves to the domain identified by the record.</td>
   </tr>
   <tr>
	 <td>ARP Cache</td>
	 <td>Address</td>
	 <td>An ARP cache contains a physical (i.e. MAC) address or IP address in one of its entries.</td>
   </tr>
   <tr>
	 <td>URL History</td>
	 <td>URI</td>
	 <td>A URL history cache contains a particular URL in one of its entries.</td>
   </tr>
   <tr>
	 <td>Win Registry Key</td>
	 <td>Win Registry Key</td>
	 <td>A Windows registry key contains another Windows registry key, as a subkey.</td>
   </tr>
 </tbody>
</table>

### Example

```xml
<cybox:Object id="example:object-210ff682-5362-4391-be79-dfa60f947c07">
	<cybox:Properties xsi:type="ArchiveFileObj:ArchiveFileObjectType">
		<FileObj:File_Path>archive.zip</FileObj:File_Path>
	</cybox:Properties>
	<cybox:Related_Objects>
		<cybox:Related_Object id="example:object-a4a74a15-e2ae-4df2-ab4e-c24cf4178fe9">
			<cybox:Properties xsi:type="FileObj:FileObjectType">
				<FileObj:File_Path>README.txt</FileObj:File_Path>
			</cybox:Properties>
			<cybox:Relationship xsi:type="cyboxVocabs:ObjectRelationshipVocab-1.1">Contains</cybox:Relationship>
		</cybox:Related_Object>
	</cybox:Related_Objects>
</cybox:Object>
```	

---

## <a name="Contained_Within"></a> "Contained_Within"

The **source Object** is *Contained within* the **related Object**.  Used for expressing the fact that an object is contained within another object. 

### Inverse

n/a

### Applicable Objects

<table class="table-striped">
 <tbody>
   <tr>
	 <th>Source Object</th>
	 <th>Related Object</th>
	 <th>Description</th>
   </tr>
   <tr>
	 <td>File</td>
	 <td>File</td>
	 <td>A file is contained within another file (e.g. appended to it).</td>
   </tr>
   <tr>
	 <td>File</td>
	 <td>Archive File</td>
	 <td>A file is contained within an archive file.</td>
   </tr>
   <tr>
	 <td>File</td>
	 <td>Email Message</td>
	 <td>A file is contained within an email message, as an attachment.</td>
   </tr>
   <tr>
	 <td>Link</td>
	 <td>Email Message</td>
	 <td>A link is contained within the body of an email message.</td>
   </tr>
   <tr>
	 <td>Domain Name</td>
	 <td>URI</td>
	 <td>A domain name is contained within the structure of a URL.</td>
   </tr>
   <tr>
	 <td>Address</td>
	 <td>DNS Record</td>
	 <td>A IP address is contained within a DNS record that resolves to the domain identified by the record.</td>
   </tr>
   <tr>
	 <td>Address</td>
	 <td>ARP Cache</td>
	 <td>A physical (i.e. MAC) address or IP address is contained within one of the entries of an ARP cache.</td>
   </tr>
   <tr>
	 <td>URI</td>
	 <td>URL History</td>
	 <td>A URL is contained within one of the entries of a URL history cache.</td>
   </tr>
   <tr>
	 <td>Win Registry Key</td>
	 <td>Win Registry Key</td>
	 <td>A Windows registry key is contained within another Windows registry key, as a subkey.</td>
   </tr>
 </tbody>
</table>

### Example

```xml
<cybox:Object id="example:object-a4a74a15-e2ae-4df2-ab4e-c24cf4178fe9">
	<cybox:Properties xsi:type="FileObj:FileObjectType">
		<FileObj:File_Path>README.txt</FileObj:File_Path>
	</cybox:Properties>
	<cybox:Related_Objects>
		<cybox:Related_Object id="example:object-210ff682-5362-4391-be79-dfa60f947c07">
			<cybox:Properties xsi:type="ArchiveFileObj:ArchiveFileObjectType">
				<FileObj:File_Path>archive.zip</FileObj:File_Path>
			</cybox:Properties>
			<cybox:Relationship xsi:type="cyboxVocabs:ObjectRelationshipVocab-1.1">Contained_Within</cybox:Relationship>
		</cybox:Related_Object>
	</cybox:Related_Objects>
</cybox:Object>
```	

---

## <a name="Extracted_From"></a> "Extracted_From"

The **source Object** was *Extracted from* the **related Object**.  Used for expressing the fact that an object was extracted from another object, in the sense that the extracted object was physically encapsulated in the structure of the object that it was extracted from, as in a file extracted from an archive file.

### Inverse

n/a

### Applicable Objects

<table class="table-striped">
 <tbody>
   <tr>
	 <th>Source Object</th>
	 <th>Related Object</th>
	 <th>Description</th>
   </tr>
   <tr>
	 <td>File</td>
	 <td>File</td>
	 <td>A file was extracted from inside of another file.</td>
   </tr>
   <tr>
	 <td>File</td>
	 <td>Archive File</td>
	 <td>A file was extracted from an archive file.</td>
   </tr>
   <tr>
	 <td>URI</td>
	 <td>Email Message</td>
	 <td>A URL was extracted from the body of an email message.</td>
   </tr>
   <tr>
	 <td>Link</td>
	 <td>Email Message</td>
	 <td>A link was extracted from the body of an email message.</td>
   </tr>
 </tbody>
</table>

### Example

```xml
<cybox:Object id="example:object-210ff682-5362-4391-be79-dfa60f947c07">
	<cybox:Properties xsi:type="FileObj:FileObjectType">
		<FileObj:File_Path>C:\temp\README.txt</FileObj:File_Path>
	</cybox:Properties>
	<cybox:Related_Objects>
		<cybox:Related_Object id="example:object-210ff682-5362-4391-be79-dfa60f947c07">
			<cybox:Properties xsi:type="ArchiveFileObj:ArchiveFileObjectType">
				<FileObj:File_Path>archive.zip</FileObj:File_Path>
			</cybox:Properties>
			<cybox:Relationship xsi:type="cyboxVocabs:ObjectRelationshipVocab-1.1">Extracted_From</cybox:Relationship>
		</cybox:Related_Object>
	</cybox:Related_Objects>
</cybox:Object>
```	

---

## <a name="Connected_To"></a> "Connected_To"

The **source Object** *Connected to* the **related Object**.  Commonly used for expressing the fact that a process connected to some network location or resource.

### Inverse

n/a

### Applicable Objects

<table class="table-striped">
 <tbody>
   <tr>
	 <th>Source Object</th>
	 <th>Related Object</th>
	 <th>Description</th>
   </tr>
   <tr>
	 <td>Process</td>
	 <td>Address</td>
	 <td>A process connected to an IP address.</td>
   </tr>
   <tr>
	 <td>Process</td>
	 <td>Hostname</td>
	 <td>A process connected to a hostname.</td>
   </tr>
   <tr>
	 <td>Process</td>
	 <td>Socket Address</td>
	 <td>A process connected to a socket address.</td>
   </tr>
   <tr>
	 <td>Process</td>
	 <td>Network Socket</td>
	 <td>A process connected to a network socket.</td>
   </tr>
 </tbody>
</table>

### Example

```xml
<cybox:Object id="example:object-c822a70d-7b41-4553-983b-a07fd8c553a0">
	<cybox:Properties xsi:type="ProcessObj:ProcessObjectType">
		<ProcessObj:Image_Info>
			<ProcessObj:File_Name>some_process.exe</ProcessObj:File_Name>
		</ProcessObj:Image_Info>
	</cybox:Properties>
	<cybox:Related_Objects>
		<cybox:Related_Object id="example:object-dec3774a-ee00-4fe8-9a19-924d51f7a46a">
			<cybox:Properties xsi:type="AddressObj:AddressObjectType" category="ipv4-addr">
				<AddressObj:Address_Value>10.1.2.5</AddressObj:Address_Value>
			</cybox:Properties>
			<cybox:Relationship xsi:type="cyboxVocabs:ObjectRelationshipVocab-1.1">Connected_To</cybox:Relationship>
		</cybox:Related_Object>
	</cybox:Related_Objects>
</cybox:Object>
```	

---