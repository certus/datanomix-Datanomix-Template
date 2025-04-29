# Qlik Sense Dashboard Implementation Plan

Our goal is to implement the visualization layer of Qlik Sense Application, using the given data load scripts and the software requirements specification.

To implement this we should:
1. Create the Data Model.
2. Create Master Measures.
3. Create Master Visualizations.
4. Create Sheets.


## 1. Data Model

To create the Data Model we need:
1. READ all Qlik Sense Load Scripts in the folder /data_load_script/* .
2. Create the data model documentation markdown file in the /ai_docs/datamodel.md

Tips:
- Try to figure out how the final data model will looks like after running all the /data_load_script/*.qvs scripts in the order, described in /data_load_script/tab_order.txt file.
- AutoCalendar derived fields usually declared using consctrction like "DERIVE FIELDS FROM FIELDS [Field1], [Field2] USING [autoCalendar]" and usually looks like this in the final data model: 
    - "Field1.autoCalendar.Month"
    - "Field1.autoCalendar.YearMonth"
    - ...

## 2. Master Measures

To create Master Measures:
1. READ ai_docs/datamodel.md, ai_docs/SRS.md, ai_templates/master_measure_guide.md.
2. Think about the list of master measures that need to be created in order to implement all requiered visualizations using data model.
3. Store all Master Measures list in ai_docs/measures.md file, including:
    - FileName (with the /objects/measures/ directory prefix);
    - Measure ID (generate unique GUID for each measure);
    - Label (short name for the user);
    - Definition (valid Qlik Sense Expression);
    - Description.
4. For each Master Measure in the list (ai_docs/measures.md) create a corresponding JSON-file in /objects/measures/ directory.

Tips:
- Keep ai_docs/measures.md file updated if you change any /objects/measures/*.json file 
- Use ai_templates/master_measure_guide.md as a reference for understanding the structure of JSON master measures objects.

## 3. Master Visualizations

To create Master Visualizations:
1. READ ai_docs/SRS.md, ai_docs/measures.md ai_templates/master_visualizations_templates.md, ai_templates/master_measure_guide.md.
2. Think about the list of master visualizations that need to be created in order to implement all requiered visualizations using data model.
3. Store all Master Visualization list in ai_docs/masterobjects.md file, including:
    - FileName (with the /objects/masterobjects/ directory prefix);
    - qId (generate unique GUID for each object);
    - Title (short name for the user);
    - Description.
4. For each Master Measure in the list (ai_docs/masterobjects.md) create a corresponding JSON-file in /objects/masterobjects/ directory.


Tips:
- Use ONLY created Master Measures in the Master Visualizations, using corresponding qLibraryId and empty qDef as shown in the ai_templates/master_measure_guide.md file.

## 4. Sheets

To create Sheets:
1. READ ai_docs/SRS.md, ai_docs/masterobjects.md, ai_templates/sheets/*.json.
2. Think about the list of sheets that need to be created in order to implement SRS.md.
3. Store all Sheets list in ai_docs/sheets.md file, including:
    - FileName (with the /objects/sheets/ directory prefix);
    - Title (short name for the user);
    - Description.
4. For each Sheet in the list (ai_docs/sheets.md) create a corresponding JSON-file in /objects/sheets/ directory. Use only Master Visualization on these Sheets (qExtendsId is the link to the Master Visualization ID).



## Implementation Notes

1. /ai_templates/ directory contains the corporate guidelines and templates, use them as a reference and examples. Do not change this directory.
2. /ai_docs/ directory contains documentation needed for context priming using LLM for development. Keep documentation files in this directory up to date when you change master measures, visualizations, sheets or data model.