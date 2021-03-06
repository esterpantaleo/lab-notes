# An alternative to RStudio to create html files from R markdown

I find it very helpful to create html files containing reports of my research. I create reproducile reports using knitr and markdown and embed bash and R code chunks into an "Rmd" file. While knitting to html is pretty simple with RStudio, our administrator said that installing Rstudio on the cluster is not trivial.

Since I find it very convenient to run my code on the cluster (I use Terabytes of data that are saved on the cluster) I wrote a simple script that converts an Rmd file into an html file. The code can be run on the cluster and is available at [RmdToHtml](https://github.com/stephenslab/stat45800/blob/13b680e107fb02c39c4ecaa9dda0e7a403d15dac/code/scripts/RmdToHtml) (this is a private repo - ask Matthew if you want access). 

As you can read in the RmdToHtml file:
```
Put the script RmdToHtml in your PATH.
Add this line to your ~/.bashrc file:

export PATH=$PATH:${path_to_the_repository}/code/scripts

where ${path_to_the_repository} is the path to your repository (of course! :) )
If you want to see the html log into the cluster use:
> ssh -X pps-gateway.uchicago.edu
> ssh -X spudhead
> ql
option -X is enabling X11 forwarding (which means you can see the graphical output)
Check that RmdToHtml is executable or type
> chmod +x RmdToHtml
``

Try running RmdToHtml RMD.Rmd from the directory where this file is saved in.

# Embed bash and R code chunks into an Rmd file


```r
# R code
print("hello world")
```

```
## [1] "hello world"
```


```bash
#bash code
echo hello world
```

```
## hello world
```
