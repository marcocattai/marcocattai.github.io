---
layout: post
title: "MPI - parallel rotation"
date: 2006-02-02 16:50:48 +0000
comments: true
categories: [MPI, C, PCX(ZSOFT), 24bpp, c, mpi, parallel, pcx, rs6000]
---

Parallel rotation on IBM RS/6000 SP
<br>
<img src="{{ root_url }}/images/23496089-rotaz.jpg" />
<br>

<p>Programmed in C language, using MPI libraries. This is a parallel implementation of a rotation algorithm for 24BPP image in PCX(ZSOFT) format. i also implemented reader/writer for that format. Software finish always with success its execution according to settings in job's file assigned to scheduler using loadLeveler management system. Test was executed highlighting the networking subsystem in the multicore environment IBM RS/6000 SP with image's input of any dimension. Considered parameters in different executions are: - Different size of PCX images (800x600 - 1024x768 - 1191x893 - 2048x1536 - 4000x3000); - Different networking system (high performance switch or ethernet); - Different number of CPU. Remains invariant the angle of rotation for all the tests.
</p>

<a href="http://dl.dropbox.com/u/7201536/pcxrotate.c" title="Source code" target="_self"><strong>I also give you code for that algorithm of rotation/scaling in  standard version for one processor. It include also encoding/decoding  for images PCX(ZSOFT) 24BPP. You can use that source file under Linux  with gcc compiler. </strong></a></p>
<p>&nbsp;</p>
<p><strong><div class='p_embed p_file_embed'>
<div class='p_embed_description'>
<strong>RotazioneMPI.pdf</strong>
<a href="{{ root_url }}/images/5636698-RotazioneMPI.pdf">View this file</a>
</div>