Download Link: https://assignmentchef.com/product/solved-ece337-dropbox-clone-server-client-system-project-2
<br>
You need to create a file sharing protocol with functionalities like download and upload for files and indexed searching. Following features need to be implemented :




<ul>

 <li>The system should have 2 clients (acting as servers simultaneously) listening to the communication channel for requests and waiting to share files (avoiding collisions) using an application layer protocol(like FTP/HTTP).</li>

 <li>Each client has the ability to do the following :

  <ul>

   <li>Know the files present on each others machines in the designated shared folders.</li>

  </ul></li>

</ul>

○ Download files from this shared folder

<ul>

 <li>File transfer should incorporate MD5 checksum to handle file transfer errors.</li>

</ul>

<strong>Specifications : </strong>The system should incorporate the following commands:

<ul>

 <li>IndexGet flag(args)

  <ul>

   <li>Can request the display of the shared files on the connected system</li>

  </ul></li>

</ul>

○ The history of requests made by either clients should be maintained at each of the clients respectively.

○ The flag variable can be shortlist , longlist .

○ <strong>Shortlist ( BONUS marks for implementing with particular extension)</strong>:

■ Flag would mean the the client only wants to know the names of files between a specific set of timestamps The sample query is shown below:

<ul>

 <li>$&gt; IndexGet shortlist &lt;starttimestamp&gt; &lt;endtimestamp&gt;</li>

 <li>Output : should include ‘name’ , ‘size’ , ‘timestamp’ and ‘type’ of the files between the start and end time stamps.</li>

 <li><strong>***BONUS*** </strong>Return only *.txt , *.pdf files between specified time stamps with this type of query $&gt; IndexGet shortlist &lt;starttimestamp&gt; &lt;endtimestamp&gt; *.txt or *.pdf</li>

</ul>




○ <strong>Longlist : </strong>flag would mean that client wants to know the entire listing of the shared folder/directory including ‘name’,

‘size’ , ‘timestamp’ and ‘type’ of the files .

■ $&gt;IndexGet longlist

■ Output : similar to above , but with complete listing.

■ <strong>*** BONUS*** </strong>: Return longlist for only *.txt file contained a word “Programmer” in it.




<ul>

 <li><strong>FileHash flag(args) : </strong></li>

</ul>

○ This command indicates that the client wants to check if any of the files on the other end have been changed. The flag variable can take two values, verify and checkall.

■ <strong>Verify : </strong>flag should check for the specific file name provided as command line argument and return its

‘checksum’ and ‘last modified’ timestamp.

<ul>

 <li>$&gt;FileHash verify &lt;filename&gt;</li>

 <li><strong>Output : </strong>checksum and lastmodified timestamp of the input file.</li>

</ul>

■ <strong>Checkall : </strong>flag should check perform what ‘verify’ does for all the files in the shared folder. (Hint: this command can be used for the periodic check of changes in the files of shared folders)

<ul>

 <li>$&gt; FileHash checkall</li>

 <li><strong>Output :</strong> filename , checksum and last modified timestamp of all the files in the shared directory.</li>

 <li><strong>FileDownload flag(args) : </strong>This would be used to download files from the shared folder of connected user to our shared folder.</li>

</ul>

○ The flag variable can take the value TCP or UDP depending on the users request.

○ If a socket is not available , it should be created and both clients must use this socket for the file transfer.

■ $&gt;FileDownload &lt;filename&gt;

■ <strong>Output :</strong> should contain the filename , filesize , lastmodified timestamp and the MD5hash of the requested file.




<strong>Caching flag(args) : </strong>It(Client) checks if the requested object is cached (i.e. Client already has the request webpage or file), and if yes, it returns the object from the cache, without contacting the server.

The size of cache should be limited and once it crosses the limit the files which haven’t been used recently need to be removed and the new files should be inserted in the cache

<ul>

 <li>$&gt;Cache verify &lt;filename&gt;</li>

 <li><strong>Output :</strong> If the file is present return it from cache else “FileDownload” it and update the cache.</li>

 <li>$&gt;Cache show</li>

 <li><strong>Output :</strong> Should print all elements of the cache and their sizes.</li>

</ul>




<strong>Instructions : </strong>

<ul>

 <li>You are allowed to choose any language like C , C++ , Python.</li>

 <li>Plagiarism of any kind (online or your batchmate’s or past batches codes) will be given <strong>zero marks</strong></li>

</ul>