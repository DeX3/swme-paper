# swme-paper
CI paper for Software Maintenance &amp; Evolution (LaTeX)

## Building

You will need the `sig-alternate` document class to build this paper. You can get it here: http://ipsn.acm.org/2010/IPSN_Submission%20instructions/sig-alternate.cls

### Building with docker

As managing classes is a bit of a pain, you can also use my docker image which has all required classes readily installed:

  docker pull theromanempire/latex
  
  # Build the file using this command:
  docker run --rm -i -v \
    $PWD:/data \
    theromanempire/latex \
    /bin/sh -c "bibtex paper && pdflatex --synctex=1 paper.tex && pdflatex --synctex=1 %'
                        
Additionally, if you're using vim, you can simply do:

  let &makeprg='docker run --rm -i
  \ -v $PWD:/data theromanempire/latex
  \ /bin/sh -c "bibtex %:r && pdflatex --synctex=1 % && pdflatex --synctex=1 %"'

So that running :Make on the `paper.tex` file will build the file.
