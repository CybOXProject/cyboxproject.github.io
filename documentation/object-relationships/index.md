---
layout: flat
title: Object Relationships
---

This page contains a detailed listing of the available CybOX Object → Object
relationships, and adds some additional context including a richer definition
and the Objects that they are most applicable to.

<table>
  <tbody>
    <tr>
      <th>Relationship</th>
      <th style="text-align: center;">Definition</th>
    </tr>
    <tr>
	  <td>"Created"</td>
      <td>The <b>source Object</b> <i>Created</i> the <b>related Object</b>. Applicable to a wide range of Objects, particularly in the
	  context of a Process that creates other Objects.</td>
	</tr>
	<tr>
	  <td></td>
	  <td>
	   <table border="1">
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
	<tr>
	  <td>"Created_By"</td>
      <td>The <b>source Object was</b> <i>Created By</i> the <b>related Object</b>. Applicable to a wide range of Objects, particularly in the
	  context of Objects that were created by a Process.</td>
	</tr>
	<tr>
	  <td></td>
	  <td>
	  <table border="1">
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
	<tr>
	  <td>"Deleted"</td>
      <td>The <b>source Object</b> <i>Deleted</i> the <b>related Object</b>. Applicable to a wide range of Objects, particularly in the
	  context of a Process that deleted other Objects.</td>
	</tr>
	<tr>
	  <td></td>
	  <td>
	  <table border="1">
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
	<tr>
	  <td>"Deleted_By"</td>
      <td>The <b>source Object was</b> <i>Deleted By</i> the <b>related Object</b>. Applicable to a wide range of Objects, particularly in the
	  context of Objects that were deleted by a Process.
	</tr>
	<tr>
	  <td></td>
	  <td>
	  <table border="1">
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