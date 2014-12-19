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
			 <td>Win Thread</td>
			 <td>A process created a Windows thread during its execution.</td>
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
		     <td>Win Thread</td>
			 <td>Process</td>
			 <td>A Windows thread was created by a process during its execution.</td>
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
		   <tr>
		     <td>File</td>
			 <td>Hostname</td>
			 <td>A file was downloaded from some device identified by a particular hostname.</td>
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
		   <tr>
		     <td>File</td>
			 <td>Hostname</td>
			 <td>A file was uploaded to a device identified by a particular hostname.</td>
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
	   <td style="text-align: center;"><a name="Sent_To"></a><h4>"Sent_To"</h4></td>
	<tr>
	   <td><b>Definition</b></td>
      <td>The <b>source Object</b> was <i>Sent to</i> the <b>related Object</b>. Commonly used for expressing the fact that a file was sent to a particular email address.</td>
	</tr>
	<tr>
	   <td><b>Inverse</b></td>
	   <td>"Received_From"</td>
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
			 <td>Address</td>
			 <td>A file was sent to a particular email address.</td>
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
	   <td style="text-align: center;"><a name="Received_From"></a><h4>"Received_From"</h4></td>
	<tr>
	   <td><b>Definition</b></td>
      <td>The <b>source Object</b> was <i>Received from</i> the <b>related Object</b>. Commonly used for expressing the fact that a file was received from an email sent from a particular email address.</td>
	</tr>
	<tr>
	   <td><b>Inverse</b></td>
	   <td>"Sent_To"</td>
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
			 <td>Address</td>
			 <td>A file was received from an email sent from particular email address.</td>
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
	   <td style="text-align: center;"><a name="Values_Enumerated"></a><h4>"Values_Enumerated"</h4></td>
	<tr>
	   <td><b>Definition</b></td>
      <td>The <b>source Object</b> <i>Enumerated the values</i> of the <b>related Object</b>. Commonly used for expressing the fact that a process enumerated the values of a particular Windows registry key.</td>
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
			 <td>Win Registry Key</td>
			 <td>A process enumerated the values of a particular Windows registry key during its execution.</td>
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
	   <td style="text-align: center;"><a name="Values_Enumerated_By"></a><h4>"Values_Enumerated_By"</h4></td>
	<tr>
	   <td><b>Definition</b></td>
      <td>The <b>source Object</b> had its <i>Values enumerated by</i> the <b>related Object</b>. Commonly used for expressing the fact that a Windows registry key had its values enumerated by a particular process.</td>
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
		     <td>Win Registry Key</td>
			 <td>Process</td>
			 <td>A Windows registry key had its values enumerated by a particular process during its execution.</td>
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
	   <td style="text-align: center;"><a name="Killed"></a><h4>"Killed"</h4></td>
	<tr>
	   <td><b>Definition</b></td>
      <td>The <b>source Object</b> <i>Killed</i> the <b>related Object</b>. Commonly used for expressing the fact that a process killed (or terminated) another process or thread.</td>
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
	  </td>
	</tr>
  </tbody>
</table>

<table class="table-bordered">
  <tbody>
    <tr>
	   <td style="text-align: center;"><a name="Killed_By"></a><h4>"Killed_By"</h4></td>
	<tr>
	   <td><b>Definition</b></td>
      <td>The <b>source Object</b> was <i>Killed by</i> the <b>related Object</b>. Commonly used for expressing the fact that a process or thread was killed (or terminated) by another process.</td>
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
	  </td>
	</tr>
  </tbody>
</table>

<table class="table-bordered">
  <tbody>
    <tr>
	   <td style="text-align: center;"><a name="Locked"></a><h4>"Locked"</h4></td>
	<tr>
	   <td><b>Definition</b></td>
      <td>The <b>source Object</b> <i>Locked</i> the <b>related Object</b>. Commonly used for expressing the fact that a process locked (in terms of read, write, or delete access) a particular file.</td>
	</tr>
	<tr>
	   <td><b>Inverse</b></td> 
	   <td>"Unlocked"</td>
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
			 <td>A process locked (in terms of read, write, or delete access) a particular file during its execution.</td>
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
	   <td style="text-align: center;"><a name="Locked_By"></a><h4>"Locked_By"</h4></td>
	<tr>
	   <td><b>Definition</b></td>
      <td>The <b>source Object</b> was <i>Locked by</i> the <b>related Object</b>. Commonly used for expressing the fact that a file was locked (in terms of read, write, or delete access) by a particular process.</td>
	</tr>
	<tr>
	   <td><b>Inverse</b></td> 
	   <td>"Unlocked_By"</td>
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
			 <td>A file was locked (in terms of read, write, or delete access) by a particular process during its execution.</td>
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
	   <td style="text-align: center;"><a name="Unlocked"></a><h4>"Unlocked"</h4></td>
	<tr>
	   <td><b>Definition</b></td>
      <td>The <b>source Object</b> <i>Unlocked</i> the <b>related Object</b>. Commonly used for expressing the fact that a process unlocked (in terms of read, write, or delete access) a particular file.</td>
	</tr>
	<tr>
	   <td><b>Inverse</b></td> 
	   <td>"Locked"</td>
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
			 <td>A process unlocked (in terms of read, write, or delete access) a particular file during its execution.</td>
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
	   <td style="text-align: center;"><a name="Unlocked_By"></a><h4>"Unlocked_By"</h4></td>
	<tr>
	   <td><b>Definition</b></td>
      <td>The <b>source Object</b> was <i>Unlocked by</i> the <b>related Object</b>. Commonly used for expressing the fact that a file was unlocked (in terms of read, write, or delete access) by a particular process.</td>
	</tr>
	<tr>
	   <td><b>Inverse</b></td> 
	   <td>"Locked_By"</td>
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
			 <td>A file was unlocked (in terms of read, write, or delete access) by a particular process during its execution.</td>
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
	   <td style="text-align: center;"><a name="Listened_On"></a><h4>"Listened_On"</h4></td>
	<tr>
	   <td><b>Definition</b></td>
      <td>The <b>source Object</b> <i>Listened on</i> the <b>related Object</b>. Commonly used for expressing the fact that a process listened on a particular port or socket.</td>
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
	  </td>
	</tr>
  </tbody>
</table>

<table class="table-bordered">
  <tbody>
    <tr>
	   <td style="text-align: center;"><a name="Renamed"></a><h4>"Renamed"</h4></td>
	<tr>
	   <td><b>Definition</b></td>
      <td>The <b>source Object</b> <i>Renamed</i> the <b>related Object</b>. Commonly used for expressing the fact that a process renamed a particular file.</td>
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
			 <td>A process renamed a file during its execution.</td>
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
	   <td style="text-align: center;"><a name="Renamed_By"></a><h4>"Renamed_By"</h4></td>
	<tr>
	   <td><b>Definition</b></td>
      <td>The <b>source Object</b> was <i>Renamed by</i> the <b>related Object</b>. Commonly used for expressing the fact that a file was renamed by a particular process.</td>
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
			 <td>A file was renamed by a particular process during its execution.</td>
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
	   <td style="text-align: center;"><a name="Renamed_From"></a><h4>"Renamed_From"</h4></td>
	<tr>
	   <td><b>Definition</b></td>
      <td>The <b>source Object</b> was <i>Renamed from</i> the <b>related Object</b>. Commonly used for expressing the fact that a file was renamed from a version of the file with a different name.</td>
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
			 <td>File</td>
			 <td>A file was renamed from another version of the file with a different name.</td>
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
	   <td style="text-align: center;"><a name="Renamed_To"></a><h4>"Renamed_To"</h4></td>
	<tr>
	   <td><b>Definition</b></td>
      <td>The <b>source Object</b> was <i>Renamed to</i> the <b>related Object</b>. Commonly used for expressing the fact that a file was renamed to a version of the file with a different name.</td>
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
			 <td>File</td>
			 <td>A file was renamed to another version of the file with a different name.</td>
		   </tr>
		 </tbody>
	   </table>
	  </td>
	</tr>
  </tbody>
</table>