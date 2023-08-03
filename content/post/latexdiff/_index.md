---
title: LaTeXdiff
subtitle: Comparing LaTeX made easy
summary: LaTeXdiff helps you to create differences between LaTeX documents
authors:
  - admin
tags: [tools]
categories: []
projects: []
date: '2023-08-03T00:00:00Z'
lastMod: '2023-08-23T00:00:00Z'
image:
  caption: ''
  focal_point: ''
---  
TODO: FIX IMAGES

Paper writing can be nasty business: you write a draft of a paper, your professor gives you comments, you implement them, send it again, just to get back another batch of comments (and repeat).
This loop of misery and despair can lead to quite a bit of frustration and is not fun for either side. Sometimes, the easy solution is to highlight the changes that were done in the paper such that the corrector can quickly see what changes and how it changes. That saves time for your collaborators and a lot of frustration for you.

If you are using Word or Google Docs to write your papers you could do this by tracking your changes. On the other hand, you are using Word to write paper, so stop reading now, and learn LaTeX.

In case you are still reading, you might have noticed that tracking changes in LaTeX is not entirely trivial. There is the "track changes" function of overleaf (which is pretty handy, by the way), but you cannot see those changes in the final PDF. Some people just prefer to read a PDF instead of a LaTeX source.... (Who would have thought...)

One option is to highlight all changes with custom macros like 
```latex
	\usepackage[normalem]{ulem}
	\usepackage{xcolor}
	\newcommend{\oldtext}[#1]{\textcolor{red}{\sout{#1}}}
	\newcommand{\newtext}[#1]{\textcolor{blue}{#1}}
	\oldtext{Hello World}
	\newtext{Hello World!}
```
Adding commands by hand to every edit feels like an awful lot of work for something that could be easily automized. After all, there is already `diff` as a program in Linux. Doesn't something like that exist for LaTeX as well?

Lo and behold, it does: `latexdiff`, your friend and helper. It is a small helper program that can be easily installed on Ubuntu with
```bash
sudo apt install -y latexdiff
```
Similar commands apply for other distributions.
If you are using windows, there is a version of latexdiff by Miktex, but the installation is not as much fun (https://www.overleaf.com/learn/latex/Articles/Using_Latexdiff_For_Marking_Changes_To_Tex_Documents).

The function of `latexdiff` is pretty simple and closely related to `diff`. By executing
```bash
latexdiff old.tex new.tex
```
`latexdiff` will print out a full LaTeX file where all changes are already annotated. Obviously, this does not belong into your terminal, but into a new LaTeX file. So, let's write it into a file
```bash
latexdiff old.tex new.tex > changes.tex
```
Now, you can just compile `changes.tex` and you will get something like the following result:

![[Pasted image 20230723160013.png]]

But can it run... But can it deal with figures and equations? Yes, it can. Freshly added equations will shine in blue, just as the text does.

Have fun trying it out and hopefully it makes your LaTeX revision process a bit less miserable.

## Further reading
In case you are interested in all the sins that you shall not commit when writing LaTeX, have a look [here](https://dabacon.org/pontiff/2012/03/12/the-nine-circles-of-latex-hell/).