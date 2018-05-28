## Adding Structure and Extracting Features
### Optical Character Recognition (OCR)

*Sometimes we get page images, but what we really need is plain text. Tesseract is free OCR software available in lots of languages that can generate text from images at a large scale.*

Navigate to the sevenagesofwoman folder

`$ cd sevenagesofwoman`

List files in the sevenagesofwoman folder

`$ ls`

Convert one tif file to one txt file using Tesseract OCR

`$ tesseract sevenagesofwoman_thebride.tiff sevenagesofwoman_thebride`

Using your GUI, compare the tif file to the txt files you generated

While we’re here, why don’t we just OCR all of them in one batch?

`$ for i in *.tiff ; do tesseract $i $i; done;`

----
*FYI for Windows Users*

Find tesseract.exe (it’s probably in Program Files (x86)) and drag it
in. You can also try the path below and then hunt down the file if it
doesn’t work

`$ '/c/Program Files (x86)/Tesseract-OCR/tesseract.exe' sevenagesofwoman_thebride.tif sevenagesofwoman_thebride`

Using your GUI, compare the tif file to the txt files you generated

While we’re here, why don’t we just OCR all of them in one batch?

`$ for %i in (*.tif) do '/c/Program Files
(x86)/Tesseract-OCR/tesseract.exe' %i %i`

----

### Regular Expressions in SublimeText

### Stanford NER
#### Scripting with Stanford NER