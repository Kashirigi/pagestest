---
layout: default
title: Table of Contents
nav_order: 1
---


# dryad2dataverse

---
**dryad2dataverse** is a set of oddly specific tools which allow easier transfer of metadata and data from a Dryad repository (ie, <https://datadryad.org>) to a [Dataverse] (https://dataverse.org/) repository. 

a) Serialize Dryad JSON to Dataverse JSON

b) Transfer Dryad studies to Dataverse without any knowledge of the somewhat complex Dataverse API

c) Monitor changes in status.

The minimum required Python version for **dryad2dataverse** is Python **3.6**, as it is the earliest version which supports f-strings. You can find Python at <https://www.python.org/downloads/>. It was developed using 3.7.2, and it runs just fine under the [now current] 3.9.1.

### Why would I need this?

There are a few reasons why you might find this product useful.

* You are a researcher and you wish to deposit via API into Dataverse repository. You've used Dryad, but the Dataverse JSON and API is unfamiliar and [complex] (https://guides.dataverse.org/en/latest/_downloads/dataverse-complete.json). You can write your Dryad JSON and convert automatically.

* Your institution has researchers who have deposited data into Dryad and you wish to copy them into the Dataverse repository which contains the bulk of your institution's research data (for example, the Dataverse repository at <https://dataverse.scholarsportal.info>)

* And on top of that, you don't want to keep checking to see if there were any updates.

### Quick install

```
git clone https://test.invalid/dryad2dataverse.git
cd dryad2dataverse
pip install .
```

### Basic usage

#### Converting JSON
```
>>> #Convert Dryad JSON to Dataverse JSON and save to a file
>>> import dryad2dataverse.serializer
>>> i_heart_dryad = dryad2dataverse.serializer.Serializer('doi:10.5061/dryad.2rbnzs7jp')
>>> with open('dataverse_json.json', 'w') as f:
	f.write(f'{i_heart_dryad.dvJson}')
```

#### Transferring data

Note: a number of variables must be set for this to work, such as your target dataverse). This example continues with the Serializer instance above.

```
import dryad2dataverse.transfer
dv = dryad2dataverse.transfer.Transfer(i_heart_dryad)
# Files must first be downloaded; there is no direct transfer
dv.download_files()
# 'dryad' is the short name of the target dataverse
# Yours may be different
# First, create the study metadata
dv.upload_study(targetDv='dryad')
# Then upload the files
dv.upload_files()
```



