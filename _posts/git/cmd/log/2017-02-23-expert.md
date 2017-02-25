---
title: "log"
date: 2017-02-23 17:05:11 +0100
categories: git cmd log
tags: expert
man: https://www.kernel.org/pub/software/scm/git/docs/git-log.html
---

> Shows commits where patch contains &lt;regex_string&gt; in &lt;file&gt;
> 
	$ git log -G'<regex_string>' -- <file>

<div></div> 

> Shows commits where patch contains case sensitive &lt;regex_string&gt; in &lt;file&gt;
> 
	$ git log -i -G'<regex_string>' -- <file>

<div></div> 

> Shows commits where &lt;string&gt; appears in or disappears from &lt;file&gt;
> 
	$ git log -S'<string>' -- <file>

<div></div> 

> Shows commits where case sensitive &lt;string&gt; appears in or disappears from &lt;file&gt;
> 
	$ git log -i -S'<string>' -- <file>

<div></div> 

> Shows commits where &lt;regex_string&gt; appears in or disappears from &lt;file&gt;
> 
	$ git log -S'<regex_string>' --pickaxe-regex -- <file>

<div></div> 

> Shows commits where case sensitive &lt;regex_string&gt; appears in or disappears from &lt;file&gt;
> 
	$ git log -i -S'<regex_string>' --pickaxe-regex -- <file>
