# MedicalFormProcessing
A play pen for John and Colin!

## Stuff to install

First put brew on your macbook

rm -rf /usr/local/Cellar /usr/local/.git && brew cleanup
ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/ \
install/master/install)"

We need ghostscript to convert pdf to tiff - tesseract won't eat pdf.

On the macbook do 'brew install ghostscript'

We also need imagemagick to clean up those nasty files

brew install imagemagick

## Install tesseract (or use checked in binaries on yosemite)

brew install tesseract
export TESSDATA_PREFIX=/usr/local/Cellar/tesseract/3.02.02_3/share/

## Convert to TIF

gs -dNOPAUSE -q -r600x600 -sDEVICE=tiffg4 -dBATCH -sOutputFile=doc1.tif ../PDF/doc01.pdf 

the 600x600 is the DPI - higher values are better of course.

Use textcleaner as needed.  These defaults work well.

./textcleaner -g ../Samples/TIF300DPI/doc5.tif ../Samples/TIF300DPI/doc5.clean.tif

## Use OCR

I've added a large user dictionary of medical terms that will help with recognition.

cp scripts/tesseract-medical-dict.txt /usr/local/Cellar/tesseract/3.02.02_3/share/tessdata/eng.user-words

to use these do 

tesseract ../Samples/TIF300DPI/doc1.tif -l eng scripts/tess.config

For normal use go with ... 

tesseract doc1.tif doc1 

tesseract doc1.tif doc1 hocr




