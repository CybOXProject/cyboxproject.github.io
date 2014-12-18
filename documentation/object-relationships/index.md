---
layout: flat
title: Object Relationships
---

This page contains a detailed listing of the available CybOX Object → Object
relationships, and adds some additional context for each relationship. This
includes a richer definition, a listing and description of the Objects that the
relationship is most applicable to, and its inverse (if existing).


<table class="table-bordered">
  <tbody>
    <tr>
	   <td style="text-align: center;"><a name="Created"></a><h4>"Created"</h4></td>
    </tr>
	<tr>
	   <td><b>Definition</b></td>
	   <td>The <b>source Object</b> <i>Created</i> the <b>related Object</b>. Applicable to a wide range of Objects, particularly in the
	       context of a Process that creates other Objects.</td>
	</tr>
	<tr>
	   <td><b>Inverse</b></td>
	   <td>"Deleted"</td>
	</tr>
	<tr>
	   <td><b>Applicable Objects</b></td>
	   <td>
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
			 <td>Thread</td>
			 <td>A process created a thread during its execution.</td>
		   </tr>
		 </tbody>
	   </table>
	  </td>
	</tr>
  </tbody>
</table>

<table class="table-bordered">
  <tbody>
    <tr>
	   <td style="text-align: center;"><a name="Created_By"></a><h4>"Created_By"</h4></td>
	<tr>
	   <td><b>Definition</b></td>
      <td>The <b>source Object was</b> <i>Created By</i> the <b>related Object</b>. Applicable to a wide range of Objects, particularly in the
	      context of Objects that were created by a Process.</td>
	</tr>
	<tr>
	   <td><b>Inverse</b></td>
	   <td>"Deleted_By"</td>
	</tr>
	<tr>
	   <td><b>Applicable Objects</b></td>
	   <td>
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
		     <td>Thread</td>
			 <td>Process</td>
			 <td>A thread was created by a process during its execution.</td>
		   </tr>
		 </tbody>
	   </table>
	  </td>
	</tr>
  </tbody>
</table>

<table class="table-bordered">
  <tbody>
    <tr>
	   <td style="text-align: center;"><a name="Deleted"></a><h4>"Deleted"</h4></td>
	<tr>
	   <td><b>Definition</b></td>
       <td>The <b>source Object</b> <i>Deleted</i> the <b>related Object</b>. Applicable to a wide range of Objects, particularly in the
	       context of a Process that deleted other Objects.</td>
	</tr>
	<tr>
	   <td><b>Inverse</b></td>
	   <td>"Created"</td>
	</tr>
	<tr>
	   <td><b>Applicable Objects</b></td>
	   <td>
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
	  </td>
	</tr>
  </tbody>
</table>

<table class="table-bordered">
  <tbody>
    <tr>
	   <td style="text-align: center;"><a name="Deleted_By"></a><h4>"Deleted_By"</h4></td>
	<tr>
	   <td><b>Definition</b></td>
       <td>The <b>source Object was</b> <i>Deleted By</i> the <b>related Object</b>. Applicable to a wide range of Objects, particularly in the
	       context of Objects that were deleted by a Process.</td>
	</tr>
	<tr>
	   <td><b>Inverse</b></td>
	   <td>"Created_By"</td>
	</tr>
	<tr>
	   <td><b>Applicable Objects</b></td>
	   <td>
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
	  </td>
	</tr>
  </tbody>
</table>

<table class="table-bordered">
  <tbody>
    <tr>
	   <td style="text-align: center;"><a name="Modified_Properties_Of"></a><h4>"Modified_Properties_Of"</h4></td>
	<tr>
	   <td><b>Definition</b></td>
       <td>The <b>source Object</b> <i>Modified the properties of</i> the <b>related Object</b>. Applicable to a wide range of Objects, particularly in the
	       context of a Process that modified the properties of other Objects.</td>
	</tr>
	<tr>
	   <td><b>Inverse</b></td>
	   <td>n/a</td>
	</tr>
	<tr>
	   <td><b>Applicable Objects</b></td>
	   <td>
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
	  </td>
	</tr>
  </tbody>
</table>
	
<table class="table-bordered">
  <tbody>
    <tr>
	   <td style="text-align: center;"><a name="Properties_Modified_By"></a><h4>"Properties_Modified_By"</h4></td>
	<tr>
	   <td><b>Definition</b></td>
       <td>The <b>source Object</b> had its <i>Properties modified by </i> the <b>related Object</b>. Applicable to a wide range of Objects, particularly in the context of Objects whose properties were modified by a Process.</td>
	</tr>
	<tr>
	   <td><b>Inverse</b></td>
	   <td>n/a</td>
	</tr>
	<tr>
	   <td><b>Applicable Objects</b></td>
	   <td>
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
	  </td>
	</tr>
  </tbody>
</table>

<table class="table-bordered">
  <tbody>
    <tr>
	   <td style="text-align: center;"><a name="Downloaded_From"></a><h4>"Downloaded_From"</h4></td>
	<tr>
	   <td><b>Definition</b></td>
      <td>The <b>source Object</b> was <i>Downloaded from</i> the <b>related Object</b>. Commonly used for expressing the fact that a file was downloaded from some network location.</td>
	</tr>
	<tr>
	   <td><b>Inverse</b></td>
	   <td>n/a</td>
	</tr>
	<tr>
	   <td><b>Applicable Objects</b></td>
	   <td>
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
			 <td>Domain</td>
			 <td>A file was downloaded from some particular domain.</td>
		   </tr>
		   <tr>
		     <td>File</td>
			 <td>Address</td>
			 <td>A file was downloaded from some particular IP address.</td>
		   </tr>
		 </tbody>
	   </table>
	  </td>
	</tr>
  </tbody>
</table>

<table class="table-bordered">
  <tbody>
    <tr>
	   <td style="text-align: center;"><a name="Downloaded"></a><h4>"Downloaded"</h4></td>
	<tr>
	   <td><b>Definition</b></td>
       <td>The <b>source Object</b> <i>Downloaded</i> the <b>related Object</b>. Commonly used for expressing the fact that a process downloaded a file.</td>
	</tr>
	<tr>
	   <td><b>Inverse</b></td>
	   <td>"Uploaded"</td>
	</tr>
	<tr>
	   <td><b>Applicable Objects</b></td>
	   <td>
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
	  </td>
	</tr>
  </tbody>
</table>

<table class="table-bordered">
  <tbody>
    <tr>
	   <td style="text-align: center;"><a name="Downloaded_To"></a><h4>"Downloaded_To"</h4></td>
	<tr>
	   <td><b>Definition</b></td>
      <td>The <b>source Object</b> was <i>Downloaded to</i> the <b>related Object</b>. Commonly used for expressing the fact that a file that was downloaded as another file (e.g., "abcd.exe" downloaded as "fun.jpg") or downloaded to a particular location.</td>
	</tr>
	<tr>
	   <td><b>Inverse</b></td>
	   <td>"Uploaded_To"</td>
	</tr>
	<tr>
	   <td><b>Applicable Objects</b></td>
	   <td>
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
			 <td>A file was downloaded and stored as another file or in some particular location (represented as a file).</td>
		   </tr>
		 </tbody>
	   </table>
	  </td>
	</tr>
  </tbody>
</table>

<table class="table-bordered">
  <tbody>
    <tr>
	   <td style="text-align: center;"><a name="Downloaded_By"></a><h4>"Downloaded_By"</h4></td>
	<tr>
	   <td><b>Definition</b></td>
      <td>The <b>source Object</b> was <i>Downloaded by</i> the <b>related Object</b>. Commonly used for expressing the fact that a file that was downloaded by a process.</td>
	</tr>
	<tr>
	   <td><b>Inverse</b></td>
	   <td>"Uploaded_By"</td>
	</tr>
	<tr>
	   <td><b>Applicable Objects</b></td>
	   <td>
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
	  </td>
	</tr>
  </tbody>
</table>

<table class="table-bordered">
  <tbody>
    <tr>
	   <td style="text-align: center;"><a name="Uploaded"></a><h4>"Uploaded"</h4></td>
	<tr>
	   <td><b>Definition</b></td>
      <td>The <b>source Object</b> <i>Uploaded</i> the <b>related Object</b>. Commonly used for expressing the fact that a process uploaded a particular file.</td>
	</tr>
	<tr>
	   <td><b>Inverse</b></td>
	   <td>"Downloaded"</td>
	</tr>
	<tr>
	   <td><b>Applicable Objects</b></td>
	   <td>
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
	  </td>
	</tr>
  </tbody>
</table>

<table class="table-bordered">
  <tbody>
    <tr>
	   <td style="text-align: center;"><a name="Uploaded_By"></a><h4>"Uploaded_By"</h4></td>
	<tr>
	   <td><b>Definition</b></td>
      <td>The <b>source Object</b> was <i>Uploaded by</i> the <b>related Object</b>. Commonly used for expressing the fact that a file was uploaded by a particular process.</td>
	</tr>
	<tr>
	   <td><b>Inverse</b></td>
	   <td>"Downloaded_By"</td>
	</tr>
	<tr>
	   <td><b>Applicable Objects</b></td>
	   <td>
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
	  </td>
	</tr>
  </tbody>
</table>

<table class="table-bordered">
  <tbody>
    <tr>
	   <td style="text-align: center;"><a name="Uploaded_To"></a><h4>"Uploaded_To"</h4></td>
	<tr>
	   <td><b>Definition</b></td>
      <td>The <b>source Object</b> was <i>Uploaded to</i> the <b>related Object</b>. Commonly used for expressing the fact that a file was uploaded to a particular network location.</td>
	</tr>
	<tr>
	   <td><b>Inverse</b></td>
	   <td>"Downloaded_To"</td>
	</tr>
	<tr>
	   <td><b>Applicable Objects</b></td>
	   <td>
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
			 <td>Domain</td>
			 <td>A file was uploaded to a particular domain.</td>
		   </tr>
		   <tr>
		     <td>File</td>
			 <td>Address</td>
			 <td>A file was uploaded to a particular IP address.</td>
		   </tr>
		 </tbody>
	   </table>
	  </td>
	</tr>
  </tbody>
</table>