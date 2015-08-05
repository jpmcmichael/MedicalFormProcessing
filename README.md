# MedicalFormProcessing
A play pen for John and Colin!

## Stuff to install

First put brew on your macbook

rm -rf /usr/local/Cellar /usr/local/.git && brew cleanup
ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/ \
install/master/install)"

We need ghostscript to convert pdf to tiff - tesseract won't eat pdf.

On the macbook do 'brew install ghostscript'

## Install tesseract (or use checked in binaries on yosemite)

brew install tesseract
export TESSDATA_PREFIX=/usr/local/Cellar/tesseract/3.02.02_3/share/

## Convert to TIF

gs -dNOPAUSE -q -r600x600 -sDEVICE=tiffg4 -dBATCH -sOutputFile=doc1.tif ../PDF/doc01.pdf 

the 600x600 is the DPI

## Use OCR

tesseract doc1.tif doc1 

tesseract doc1.tif doc1 hocr




