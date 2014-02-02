---
layout: post
title: "Linux - snippets"
date: 2011-06-10 17:52:14 +0000
comments: true
categories: [linux, snippets]
---

<p>
Search all the files/folder with that name and remove them 
{% codeblock lang:sh %}
 find . -name "FILE-TO-FIND"-exec rm -rf {} \;
{% endcodeblock %}
</p>

<p>
Find all files having .bak (*.bak) extension in current directory and remove them:
{% codeblock lang:sh %}
  find . -type f -name "*.bak" -exec rm -f {} \;
{% endcodeblock %}
</p>

<p>
Find all core files and remove them
{% codeblock lang:sh %}
  find / -name core -exec rm -f {} \;
{% endcodeblock %}
</p>

<p>
Find all *.bak files in current directory and removes them with confirmation from user:
{% codeblock lang:sh %}
  find . -type f -name "*.bak" -exec rm -i {} \;
{% endcodeblock %}
</p>

<p>
Find all pdf files and copy them in DestinationFolder:
{% codeblock lang:sh %}
  find . -type f -name "*.pdf" -exec cp {} DestinationPath \;
{% endcodeblock %}
</p>

<h2>Searching</h2> <br>
Search for pattern in files
{% codeblock lang:sh %}
  	grep pattern files
{% endcodeblock %}

Search recursively for pattern in dir
{% codeblock lang:sh %}
	grep -r pattern dir 
{% endcodeblock %}

Search for pattern in the output of command
{% codeblock lang:sh %}
	command | grep pattern
{% endcodeblock %}

Locate file – Find all instances of file <br>
Starting with the root directory, look for the file called filename
{% codeblock lang:sh %}
	find / -name filename 
{% endcodeblock %}

Starting with the root directory, look for the file containing the string filename
{% codeblock lang:sh %}
	find / -name ”*filename*”
{% endcodeblock %}

Starting with the directory called dir, look for and list all files containing TextStringToFind
{% codeblock lang:sh %}
	grep TextStringToFind /dir
{% endcodeblock %}


Create symbolic link link to file
{% codeblock lang:sh %}
	ln -s file link 
{% endcodeblock %}

Create or update file
{% codeblock lang:sh %}
	touch file
{% endcodeblock %}

Places standard input into file
{% codeblock lang:sh %}
	cat > file
{% endcodeblock %}

Display the file called file one page at a time, proceed to next page using the spacebar
{% codeblock lang:sh %}
	more file 
{% endcodeblock %}

Output the first 10 lines of file
{% codeblock lang:sh %}
	head file
{% endcodeblock %}

Display the first 20 lines of the file called file
{% codeblock lang:sh %}
	head -20 file
{% endcodeblock %}

Output the last 10 lines of file
{% codeblock lang:sh %}
	tail file 
{% endcodeblock %}

Display the last 20 lines of the file called file
{% codeblock lang:sh %}
	tail -20 file 
{% endcodeblock %}

Output the contents of file as it grows, starting with the last 10 lines
{% codeblock lang:sh %}
	tail -f file 
{% endcodeblock %}

<h2>Compression</h2>

 Compression

 Create a tar named file.tar containing files
{% codeblock lang:sh %}
	tar cf file.tar files
{% endcodeblock %}


Extract the files from file.tar
{% codeblock lang:sh %}
	tar xf file.tar 
{% endcodeblock %}

Create a tar with Gzip compression
{% codeblock lang:sh %}
	tar czf file.tar.gz files
{% endcodeblock %}

Extract a tar using Gzip
{% codeblock lang:sh %}
	tar xzf file.tar.gz
{% endcodeblock %}

Create a tar with Bzip2 compression
{% codeblock lang:sh %}
	tar cjf file.tar.bz2
{% endcodeblock %}

Extract a tar using Bzip2
{% codeblock lang:sh %}
	tar xjf file.tar.bz2
{% endcodeblock %}

Compresses file and renames it to file.gz
{% codeblock lang:sh %}
	gzip file
{% endcodeblock %}

Decompresses file.gz back to file
{% codeblock lang:sh %}
	gzip -d file.gz
{% endcodeblock %}




