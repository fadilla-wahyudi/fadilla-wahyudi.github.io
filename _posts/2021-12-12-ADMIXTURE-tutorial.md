---
title: "Using pophelper to create \"smoother\" ADMIXTURE plots"
classes: "wide"

---

A couple of years ago, when I started out with bioinformatics, I had to create admixture plots. After generating the ancestry fractions using [ADMIXTURE](https://dalexander.github.io/admixture/download.html), I used [pophelper](https://github.com/royfrancis/pophelper) to create them. This is what my plot looked like (I recreated it using the 1000 Genomes dataset):

![ADMIXTURE plot before](/assets/images/posts/2021-12-13-ADMIX.8.Q-before.png)

And this is what I wanted my plot to look like:

![ADMIXTURE plot after](/assets/images/posts/2021-12-13-ADMIX.8.Q-after.png)

I wanted it to look smoother.

The problem I faced was that I could not reorder the population groups (e.g. LWK, ESN) using `subsetgrp` and sort individuals by their ancestry proportions using `sortind="all"` simultaneously. Here is the solution:

*Note: I believe the author of [pophelper](https://github.com/royfrancis/pophelper) posted about this, but I can't seem to find it. If I do, I will link it here.*

## Reading the files and creating population labels

I created a data frame called `popnames` where column 1 (V1) contains the population names listed for each sample in order, and column 2 (V2) contains the respective continental populations.

I set the `stringsAsFactors` as `FALSE` so that the population labels can be read by `grplab`.

In this example, I am using a *K* value of 8.

```r
library(pophelper)

# population names
popnames <- read.table("pop.txt", stringsAsFactors = FALSE)

# K=8
alist8 <- readQ(files="ADMIX.8.Q")
```

## Reordering the population groups

The next step was to reorder the populations using `subsetgrp`. However, instead of creating a plot, the data, which will contain the reordered population groups, will be saved to a variable.

- `grplab` — assigns the population labels
- `selgrp = "V1"` — because there are two population labels, I have to declare the one I'll be using for `ordergrp` and `subsetgrp`
- `ordergrp = TRUE` — in order to sort them using `subsetgrp`, I need to set this as `TRUE` so that all individuals from the same population are grouped together
- `returndata = TRUE` — instead of plotting the data, the data will be stored as a variable
- `exportplot = FALSE` — does not create a plot

```r
neworder <- plotQ(alist8, grplab=popnames[,c(1,2)],
                  selgrp = "V1",
                  ordergrp = TRUE,
                  subsetgrp = c("LWK", "ESN", "YRI", "MSL", "GWD", "ACB", "ASW", "TSI", "IBS", "GBR", "CEU", "FIN", "GIH", "PJL", "BEB", "STU", "ITU", "KHV", "CDX", "CHS", "CHB","JPT", "PUR", "CLM", "MXL", "PEL"),
                  returndata = TRUE,
                  exportplot = FALSE)
```

## Creating an ADMIXTURE plot

Next, I created the plot. The data is located in `neworder$data$qlist` and the population labels are located in `neworder$data$grplab[[1]]`.

- `sortind = "all"` — all clusters (i.e. ancestry groups) are considered when sorting out the individuals
- `exportpath=getwd()` — export the plot in the current working directory

```r
qdata2 <- plotQ(neworder$data$qlist, grplab=neworder$data$grplab[[1]],
                ordergrp = FALSE,
                selgrp = "V1",
                sortind = "all",
                height = 5,
                grplabheight = 1,
                showdiv = TRUE, divsize = 0.4,
                clustercol = c("#1D72F5","#DF0101","#77CE61", "#FF9326","#A945FF","#0089B2","#FDF060","#FFA6B2"),
                exportpath=getwd())
```

And voilà! A smoother, more satisfying plot.
