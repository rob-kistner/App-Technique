InDesign Batch Find & Replace Using Script
==========================================

### NOTE: I gotta go back through this one. The technique is pretty old and most likely changed since the older version of InDesign

--- 

InDesign comes with a Javascript automation script that allows you to batch find and replace content in an .indd document. It requires a text file formatted a certain way.


### Prepare the Find / Replace Text File
- Arrange a spreadsheet with old & new content in two columns, this will be your raw find & replace data.
- In InDesign, in the Scripts panel, go to the **FindChangeSupport** and select the **FindChangeList.txt** file.
- In the flyout menu of the **Scripts** panel, select **Reveal in Finder**.
- If you haven't before — duplicate the **FindChangeList.txt** file to **FindChangeList-orig.txt** so you have a backup of the absolute original version.
- Open **FindChangeList.txt** in SublimeText or another REGEX supported text editor. The instructions following will use TextWrangler as the base app for all functionality.
- Replace all bottom statements with this one:
```
grep
{findWhat:""}
{changeTo:""}
{}---".
```

There should be tabs in-between the 5 items.

- Perform a GREP find/replace your text editor to place the values in the empty quotes ("") in **findWhat** and changeTo respectively with your found & replaced content. The GREP statement will vary from one kind of data to another. To replace Family Dollar item codes, for example, you'd use the following GREP statements:

**Find:**
```
(^FAM[0-9]+)\t(FAM[0-9]+$)
```

**Replace:**
```
grep
\{findWhat:"\1"\}
\{changeTo:"\2"\}
\{\}
---
```

- *NOTE:*  See (****** URL HERE *******) for a guide to grep statements. Be prepared to experiment and fail a few times on the data before you get it right.

- Run the GREP find/replace, you should wind up with your two columns of data in the quotes after findWhat and changeTo. Make sure the data is correct before saving. You can save the FindChangeList.txt file exactly where you found it.

### Run the script in InDesign

- Open the document you need to process.
- Double click **FindChangeByList.jsx** in the **Scripts** panel
- All previous values should now be replaced by the new values.

*NOTE:* It's a good idea to check the values, at least extensively at random through the document if not completely, to make sure the script did its thing properly.

