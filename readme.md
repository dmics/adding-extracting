## Adding Structure and Extracting Features

You should already have a project/corpora folder on your Desktop with these files in it. If not, you can [download the texts folder here](https://github.com/dmics/commandlinebootcamp/blob/master/dmics-texts.zip).

### Tesseract Optical Character Recognition (OCR)
#### Description
Tesseract-OCR is an open source OCR (optical character recognition) engine, originally developed by Hewlett Packard Laboratories. The standard installation of Tesseract-OCR can convert images of text in 39 different languages to plain text data.  

#### Scenario
You visit an archive and need to capture images of text based archival collections for your research - ultimately you would like to convert these images into data that you can search, visualize, text mine, etc. Using a digital camera and/or a copier you capture photos of archival collections in the .tif / .tiff format. With these files in hand you are prepared to use Tesseract-OCR to convert your images into plain text files.

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
>*Remember our loop from the Command Line Bootcamp? This works the same way, but condenses everything to a single line using semicolons between commands.*

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

### GREP and Regular Expressions

#### Searching & Mining

Move back to the poetry books

`$ cd ..`

Find out how many lines and words there are in a text of your choosing using **wc -l -w**

`$ wc -l -w ActoEPoems.txt`

Results:

```
3861 15603 ActoEPoems.txt
```

Do some very basic searching with grep

`$ grep europe *txt`

`$ grep Europe *txt`

`$ grep America *txt`

Do some very basic counting with **grep -c**

`$ grep -c man *txt`

`$ grep -c woman *txt`

Count only whole words using **grep -cw**

`$ grep -cw man *txt`

@@ come up with a search that matches a pattern or part of a words

`egrep` opens up an extended set of regular expression search features @@
search for context around a word
`egrep -r -o '.{0,50}\b185[0-9]\b.{0,50}' ./`
@@@

### Stanford NER

#### Description
Stanford Named Entity Recognizer is a Java implementation of Named Entity Recognizer. Named
Entity Recognition (NER) is method that allows automatic labelling of things like people,
organizations, and geographic locations in unstructured text. The standard installation of this
software works relatively well on English sources and contains models trained on CoNLL-2003
data. For novice users, the tool provides a graphical user interface that allows quick
experimentation with the potential utility of this approach for your research question. For more
advanced usage, e.g. training the tool on a specific corpus, command line interaction is needed.

#### Scenario

You want to assess the frequency of mentions of people and places in work(s) of literature. While
you could use a simple text editing program to find all occurrences of X person or Y place, doing
so would require comprehensive prior knowledge of all possible people and places. Rather than
attempt to pre define these possibilities you decide to explore automatic recognition of people
and places to provide a foundation to your assessment.

#### NER GUI Tool

1. Drag the Stanford Named Entity Recognizer folder to your Desktop and open it.
1. Double click stanford-ner.jar
1. Load a Classifier (e.g.) english.all.3class.distsim.crf.ser.gz
1. From the Classifier menu follow the path below
1. Classifier > Load CRF from File > Stanford-ner-[releasedate] > classifiers > english.all.3class.distsim.crf.ser.gz
1. Once loaded you will see options on the right hand side of the graphical user interface for ORGANIZATION, LOCATION, and PERSON.
1. Load one of the texts in the archive folder.
1. Click 'Run NER'
1. Every organization, person, and place that Stanford Named Entity Recognizer is able identify is now tagged.
1. Save the tagged file to your Desktop—File > Save Tagged File as > [ any filename you want ]
1. Open the tagged file in Sublime Text and examine the results - you may want to use cmd+F to search for the tags

#### NER from the Command Line

Stanford NER actually has its own .sh script that you can use to do this work automatically.

`@ ../stanford-ner-@@releasedate]/ner.sh ActoEPoems.txt > ner_ActoEPoems.txt`

Open ner_ActoEPoems.txt in a text editor and examine the results.
