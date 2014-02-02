---
layout: post
title: "Client-Server Communication. Intercepting proxy"
date: 2011-02-03 18:15:55 +0000
comments: true
categories: 
---

<div class='post_body'><p>It is helpful to see what each side, in a client/Server communication, sends or receives. There are two Unix tools that could be usefull in such situations:</p>
<p><a href="https://www.owasp.org/index.php/Category:OWASP_WebScarab_Project" title="https://www.owasp.org/index.php/Category:OWASP_WebScarab_Project" target="_blank">- OWASP WEBScrab Project</a></p>
<p>WebScarab operates as an intercepting proxy, allowing the operator to   review and modify requests created by the browser before they are sent   to the server, and to review and modify responses returned from the   server before they are received by the browser. It is able to intercept  both HTTP and HTTPS communication.</p>
<p><a href="http://www.parosproxy.org/" title="http://www.parosproxy.org/" target="_blank">- Paros</a> (<a href="http://research.corsaire.com/tools/" title="http://research.corsaire.com/tools/" target="_blank">Mac</a>)</p>
<p>Paros features request and response editing and automated scanning of Cross Site Scripting and SQL injection vulnerabilities</p>
<p>- NETCAT&nbsp; Listen all TCP/UDP connections on a specific port</p>
<p>- cURL&nbsp; send 'fake' requests to a server.</p>
<div><span style="font-size: large;">Listening to incoming requests</span></div>
<p><br /> We start a listening server with</p>
{% codeblock lang:sh %}
	nc -lk $ip $port
{% endcodeblock %}
<ul>
<li><em><span style="font-family: Times,Times New Roman,serif;">-l: listen</span></em></li>
<li><em><span style="font-family: Times,Times New Roman,serif;">-k: forces nc to stay listening for another connection after its current connection is completed.</span></em></li>
<li><em><span style="font-family: Times,Times New Roman,serif;">$ip: the IP/interface you want to bind to. Use 0.0.0.0 to bind to all interfaces and IPs.</span></em></li>
<li><em><span style="font-family: Times,Times New Roman,serif;">$port:  the port you want to bind to. Doesn't really matter which one you use,  as long as the client uses the same one to connect to.</span></em></li>
</ul>
{% codeblock lang:sh %}
	nc -lk 0.0.0.0 8080
{% endcodeblock %}
<p>&nbsp;</p>
<p><span style="font-size: large;">Sending "fake" requests to a server</span></p>
<p>&nbsp;</p>
<p>With CURL it is as simply as that:</p>
{% codeblock lang:sh %}
	curl -v -i -X POST -d $data $uri
{% endcodeblock %}

<ul>
<li><em>-<span style="font-family: Times,Times New Roman,serif;">v: verbose</span></em></li>
<li><em><span style="font-family: Times,Times New Roman,serif;">-i: include HTTP headers in the output</span></em></li>
<li><em><span style="font-family: Times,Times New Roman,serif;">-X: HTTP request type. Defaults to GET if none given</span></em></li>
<li><em><span style="font-family: Times,Times New Roman,serif;">-d: data</span></em></li>
</ul>

{% codeblock lang:sh %}
	curl  -v -i -X POST -d  '{"id":1,"action":"getRecord","params":{"clientVersion":"1.0.0.230","user":"kat"}}'
{% endcodeblock %}


