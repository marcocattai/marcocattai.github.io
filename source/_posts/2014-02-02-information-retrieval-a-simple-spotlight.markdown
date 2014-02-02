---
layout: post
title: "Information Retrieval: a simple SPOTLIGHT"
date: 2012-04-02 14:24:03 +0000
comments: true
categories: [Information, retrieval, spotlight, iOS]
---

<div class='post_body'><p>In this post I want to write about Information retrieval. Spotlight is a selection-based search system, which creates a virtual index of all items and files you want.</p>
<p>we must solve the following problem:</p>
<blockquote>
<p><strong><span style="color: #000000;">We have a lot of PDF described by the text they contain or also images/videos described using TAGS. Spotlight allow the user to quickly locate a wide variety of relevant items that contain , with high probability, the informations you are looking for.</span></strong><strong><span style="color: #000000;">  </span></strong>
</blockquote>
<p>We will use:</p>
<p>An <span style="color: #ff0000;"><strong>Information Retrieval System (IRS).</strong></span><strong> </strong>It is a system <span class="short_text"><span title="Fai clic per visualizzare le traduzioni alternative" class="hps">designed and</span> <span title="Fai clic per visualizzare le traduzioni alternative" class="hps">built</span> <span title="Fai clic per visualizzare le traduzioni alternative" class="hps">to</span> <span title="Fai clic per visualizzare le traduzioni alternative" class="hps">perform tasks of Information Retrieval for big collections of documents, it ensures decription of documents </span></span><span class="short_text"><span title="Fai clic per visualizzare le traduzioni alternative" class="hps">and retrieval</span> <span title="Fai clic per visualizzare le traduzioni alternative" class="hps">of</span> <span title="Fai clic per visualizzare le traduzioni alternative" class="hps">those</span> <span title="Fai clic per visualizzare le traduzioni alternative" class="hps">considered</span> <strong><span title="Fai clic per visualizzare le traduzioni alternative" class="hps">relevant </span></strong></span><span> <span title="Fai clic per visualizzare le traduzioni alternative" class="hps">to</span> <span title="Fai clic per visualizzare le traduzioni alternative" class="hps">the needs</span> <span title="Fai clic per visualizzare le traduzioni alternative" class="hps">expressed</span> <span title="Fai clic per visualizzare le traduzioni alternative" class="hps">by the</span> user 's <span title="Fai clic per visualizzare le traduzioni alternative" class="hps">questions</span><span title="Fai clic per visualizzare le traduzioni alternative" class="hps">.<br /></span></span></p>
<p><!--more--></p>
<p>Let's start with some Theory:</p>
<p><span style="font-size: large;"><strong>Let:</strong></span></p>
<p><span style="font-size: x-large;"><strong>d</strong></span>i = (<span style="font-size: x-large;">w</span>i1, ..., <span style="font-size: x-large;">w</span>ik)</p>
<p><span style="font-size: medium;">be the vectorial rappresentation of a document</span>.</p>
<p><span style="font-size: x-large;">w</span>ij is the weight of <strong>descriptor </strong><span style="font-size: x-large;">t</span>j in document <span style="font-size: x-large;"><strong>d</strong></span>i</p>
<p>Right now let's say that a descriptor is a single word in a document (PDF).</p>
<p>&nbsp;</p>
<p>Now we choose a weight schema that's called <strong>TF (Term Frequency).</strong></p>
<p><span style="font-size: x-large;">w</span>ij = <span style="font-size: x-large;">f</span>ij</p>
<p>Where <span style="font-size: x-large;">f</span>ij is the number of times descriptor <span style="font-size: x-large;">t</span>j appear in document <span style="font-size: x-large;"><strong>d</strong></span>i</p>
<p>Let:</p>
<p><span style="font-size: x-large;"><strong>D</strong></span>1 = {a, a, a, b, b, c}</p>
<p><span style="font-size: x-large;"><strong>D</strong></span>2 = {a, a, b, c}</p>
<p><span style="font-size: x-large;"><strong>D</strong></span>3 = {a, b, b, c}</p>
<p><span style="font-size: x-large;"><strong>D</strong></span>4 = {a, b, d}</p>
<p>Our Query is&nbsp; <span style="font-size: x-large;"><strong>Q</strong></span> = {a, c, d}</p>
<p>&nbsp;</p>
<p><span style="font-size: x-large;"><strong>Q</strong></span><span style="font-size: x-large;"><strong> D</strong></span>1 = {4}&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <span style="font-size: x-large;"><strong>Q</strong></span><span style="font-size: x-large;"><strong> D</strong></span>2 = {3}&nbsp;&nbsp;&nbsp;&nbsp; <span style="font-size: x-large;"><strong>Q</strong></span><span style="font-size: x-large;"><strong> D</strong></span>3 = {2}&nbsp;&nbsp;&nbsp;&nbsp; <span style="font-size: x-large;"><strong>Q</strong></span><span style="font-size: x-large;"><strong> D</strong></span>4 = {2}<br /><span style="font-size: x-large;"><strong>&nbsp;</strong></span></p>
<p>Won <span style="font-size: x-large;"><strong>D</strong></span>1 and <span style="font-size: x-large;"><strong>D</strong></span>2 becouse "a" <span class="short_text"><span title="Fai clic per visualizzare le traduzioni alternative" class="hps">appears</span> <span title="Fai clic per visualizzare le traduzioni alternative" class="hps">several</span> <span title="Fai clic per visualizzare le traduzioni alternative" class="hps">times in each. <span style="color: #ff0000;"><strong>BUT IT APPEARS IN ALL DOCUMENTS!!!</strong></span></span></span><span class="short_text"><span title="Fai clic per visualizzare le traduzioni alternative" class="hps">&nbsp;</span></span></p>
<p><span style="color: #ff0000;">The Presence of d in our query can not discriminate <span style="font-size: x-large;"><strong>D</strong></span>4 </span></p>
<p><span class="short_text"><span title="Fai clic per visualizzare le traduzioni alternative" class="hps">We must define a schema <strong>IDF (Inverse Document Frequency)</strong></span></span></p>
<p><span style="font-size: x-large;">w</span>ij = <span style="font-size: x-large;">log (N/n</span>j<span style="font-size: x-large;">)</span></p>
<p><span style="font-size: x-large;">N </span><span class="short_text"><span title="Fai clic per visualizzare le traduzioni alternative" class="hps">is the number of documents in our collection</span></span><span style="font-size: x-large;">. </span></p>
<p><span style="font-size: x-large;">n</span>j<span class="short_text"><span title="Fai clic per visualizzare le traduzioni alternative" class="hps"> is the number of documents, of the whole collection, </span></span><span class="short_text"><span title="Fai clic per visualizzare le traduzioni alternative" class="hps">where</span></span><span class="short_text"><span title="Fai clic per visualizzare le traduzioni alternative" class="hps"> the descriptor</span></span><span class="short_text"><span title="Fai clic per visualizzare le traduzioni alternative" class="hps"> </span></span><span style="font-size: x-large;">t</span>j appear.</p>
<p>So our search Engine will return <span style="font-size: x-large;"><strong>D</strong></span>4.</p>
<p><span style="text-decoration: underline;">If a descriptor appear many times in all documents then it loses importance in the description of documents. </span></p>
<p>&nbsp;</p>
<p>The schema that we will use is a combination of schema explained in this post. Its name is <strong>TFIDF</strong></p>
<p><span style="font-size: x-large;">w</span>ij = <span style="font-size: x-large;">f</span>ij <span style="font-size: x-large;">log (N/n</span>j<span style="font-size: x-large;">)</span></p>
<p>Long documents contains relevant descriptors many times than short documents. Our search Engine will give more importance at first	.</p>
<p><span style="font-size: x-large;"><span style="font-size: medium;"><span style="font-family: mceinline;">In your CoreData Project open .xcdatamodel and add the following table:</span></span></span></p>
<img src="{{ root_url }}/images/descriptor.png"/>

<p>&nbsp;</p>
<p>It describes:</p>
<p>- the word field</p>
<p>- the frequency of the word</p>
<p>- the weight of the word</p>
<p>- A Relation (with Inverse) to your Documents Table.</p>

<p>In a document there are a lot of words that are not useful for our purposes, becouse they don't describe the content of our documents. That words are articles, some adjectives and so on... In the following Link you can find two list of words that I prepared in Italian and English. They're called <strong>STOP WORDS</strong>.</p>
<ul>
<li><a href="http://dl.dropbox.com/u/7201536/stop-words-ita.txt" title="STOP WORDS ITA" target="_blank"><strong>Italian STOP WORDS</strong></a></li>
<li><a href="http://dl.dropbox.com/u/7201536/stop-words-eng.txt" title="STOP WORDS ENG" target="_blank"><strong>English STOP WORDS</strong></a></li>
</ul>
<p><strong>1) Read both files in two NSString:</strong></p>
<p>NSString *englishStopWords &lt;- stop-words-eng.txt<br />NSString *italianStopWords &lt;- stop-words-ita.txt</p>
<p><strong>Now split them in an array</strong><br />

{% codeblock lang:objc %}
	NSArray *stopWordsITA = [italianStopWords componentsSeparatedByCharactersInSet:[NSCharacterSet characterSetWithCharactersInString:@" \n"]];
	NSArray *stopWordsENG = [englishStopWords componentsSeparatedByCharactersInSet:[NSCharacterSet characterSetWithCharactersInString:@" \n"]];  
{% endcodeblock %}

<p><strong>2) Get Your document's text ans Save them in a Dictionary where a word is the key and the value is the frequency of that word in the Document.</strong></p>
<p><strong>3) Filter the dictionary ad remove all stop words. You can also filter the dictionary's representation of a document with the stopwords while you are creating it</strong></p>
<p><strong>4) Describe your document in a DB (ex. NSManagedObject is IADocument class)</strong></p>
<p><strong>5) Save the descriptor for that document</strong></p>
<p><strong>6) Now keeping reference at what we explained at the beginning of this post create your retrieval function</strong></p>
