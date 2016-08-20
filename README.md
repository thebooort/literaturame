# literatura.me

Measuring progress in literature and in other creative endeavours, like programming. Preparing a paper/presentation for YAPC::EU 2016.

This repo and branch contain scripts to process repositories and generate time series of lines changed in commits, as well as, if it is a literary work that has been continously integrated, to extract the number of words changed. You need to use the `Test::Text` module in order to process it in this way.

## How to use this on your repo.

Perl needs to be installed. Do it the usual way. I'll be using `cpanm` in the instructions, so that is needed too. If you use `perlbrew`, which you should, you will have both.

Scripts for processing repositories are contained in the appropriately named `scripts` repository. So

	cd scripts
	cpanm --installdeps .
	
And then, to run the script itself, you can `cd` to the repo you want analyzed and

	/path/to/scripts/get-diffs.pl <glob including all files you want to analyze> 
	
The repository has to be downloaded to your drive. By default, you will analyze the current repo, but you can also analyze others:

	./get-diffs.pl <glob including all files you want to analyze> <repo directory>
	
This will generate a `.csv` file with `lines` as preffix and a name related to the repo name and glob. This file will contain a single column with the size of the commit, with size being the maximum of lines added/deleted. 

There is no rule to what the glob should include, other than you should try and include only files that have been typed *by hand*, not those automatically generated by, well, code generators or `LICENSE` files, that kind of thing. The whole point of this is to analyze coding patterns as reflected by commit sizes, so non-human files make no sense. 

## What to do with this file

`cd` to `../stats`. You can plug the file name into the first lines of
`creativity.Rmd` and, if you have R and knitr, generate the file from
rstudio or directly from R using knitr. Please check the knitr size
for how to do this, or directly share your file in a repo, tell me via
twitter to `@jjmerelo`, and I'll do it for you. Of course, that file
includes author and stuff, so if you want to change conclusions,
author or whatever, feel free to do so, it has the same license as the
whole repo. 

You can also add a link to these results in [`data.md`](data.md) if you so desire. Take a look at [CONTRIBUTING.md](CONTRIBUTING.md) to do it properly (don't worry, just a minimal set of rules).

## What kind of repos will be *interesting*

You will need a repo with more than a few hundred commits to have some
real effect showing up. And by *real effect* I mean power laws, maybe
pink noise, all that adding up to *self-organized criticality*. Which
is kind of cool. 

