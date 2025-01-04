---
layout: post
title: How to ssh passless?
date: 2016-04-08 18:00:00
description: 
---


<h2> Goal </h2>
Assume we are using linux and openssh and we want to do an automatic login form "host A/user a" to "Host B/ user b" without entering your password every time. 

<h2> How to do it? </h2>

<ul>
<li> Open a terminal. </li>
<li> log in to host A</li>
<li> Generating a pair of authentication keys: a@A:~$ ssh-keygen -t rsa</li>
<ul>
<li> Enter file in which to save the key (/home/a/.ssh/id_rsa):</li>
<li> Created directory '/home/a/.ssh'. </li>
<li> Enter passphrase (empty for no passphrase): </li>
<li> Enter same passphrase again:  </li>
</ul>
<li> Now, your identification is saved in "/home/a/.ssh/id_rsa" and your public ey has been saved in "/home/a/.ssh/id_rsa.pub" </li>
<li> Now create a directory "~/.ssh" as user b on B. This directory may already exists. </li>
<ul>
<li> a@A:~$ ssh b@B  </li>
<li> mkdir -p .ssh </li> 
</ul>
<li> Finally you need to append a's new public key to the authorized keys for b@B as</li>
<ul>
<li> a@A:~> cat .ssh/id_rsa.pub | ssh b@B 'cat >> .ssh/authorized_keys'</li>
</ul>
<li> At this step, we are done! I usually add an alias to my ~/.bashrc file, for doing the whole ssh thing with just typing someWord! You can append this line to your ~/.bashrc file: </li>
<ul>
<li> alias someWord="ssh b@B"</li>
</ul>
<li>Voila!! </li>
</ul>                        
