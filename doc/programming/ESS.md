# Using R on the cluster through emacs
Someone in the lab wanted to start using R remotely on the cluster using emacs and asked me for directions. 

Some preliminary info: emacs on our cluster has the add on package [ESS](http://ess.r-project.org/) (Emacs Speaks Statistics) which makes it easy to edit scripts and interact with statistical programs like R.

## How to 
1.   Open emacs using command
```emacs -nw file.R```
where file.R is a file containing R code. 
2.   Use one of the following commands:  “C-c C-b” or “C-c C-r” or "C-c C-p" or "C-c C-j" to run your R code. After using one of those commands the window will split into two parts (the top part should be the R terminal). 
3. Keep wriing R code in file.R or switch to the R terminal using "C-o".

How to use the commands above (from [http://blog.revolutionanalytics.com/2014/03/emacs-ess-and-r-for-zombies.html](http://blog.revolutionanalytics.com/2014/03/emacs-ess-and-r-for-zombies.html)):
```You can submit the whole buffer to an R process by pressing “C-c C-b”.  If you don't have an R process running in your Emacs session, then one will be created for you in a buffer entitled "*R*" which you will see appear as your buffer is split either above/below or left-right.  You can also submit a region by highlighting some code and pressing “C-c C-r”.  You can submit a paragraph in which your cursor resides by C-c C-p (a paragraph is a set of one or more lines of codes separated by blank lines).  You can submit the line on which your cursor resides by C-c C-j (your cursor can be anywhere in the line; it doesn't have to be at the beginning or the end).```




