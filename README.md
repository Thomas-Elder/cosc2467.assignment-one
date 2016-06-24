# Document Markup Languages - Assignment One
Assignment one from RMIT's COSC2467 Document Markup Languages course.

# Assignment Specification

## Introduction
The objective of this assignment is to test your understanding of XML documents, DTD, XML
Schema, and how XML Schema provides a rich grammatical structure for XML documents
that overcomes the limitations of DTD.

### Task 1 [10 marks]- XML and DTD
Note: Some of the specifications in Task 1 are open to interpretation(s), this is intentional.
You will have to make assumptions while creating XML and DTD. The exercise will give you
a good experience of XML serialization, DTD (and its limitations).

In order to improve the quality and efficiency of health care in Australia, the government
has decided to record patient medical data on individual Medicare Cards. The data will
be encrypted and will only be accessible to health care professionals. In order to make
the data as portable as possible, patient health care information will be stored as an XML
document. The Government has not finally decided on all the information that should be
stored, but it must include at least:
1. The name of the patient
2. The gender of the patient
3. Date of birth (think of an efficient way to serialize this)
4. Blood type
5. Any known allergies
6. Any known adverse drug reactions
7. Any chronic conditions
8. Languages spoken
9. Information about each visit to a medical practitioner, including:
(a) the type of practitioner, and associated information
(b) the date of the visit
(c) the patient’s symptoms
(d) the diagnosis
(e) the prescription (if any)
10. Information about any hospital admissions, including:
(a) date of admission and discharge
(b) reason for admission
(c) procedures performed
Your task is to write the following-
1. Sample XML document depicting information of two patients (5 marks)
2. XML DTD – you must connect XML document to this external DTD (5 marks)
Name your documents as Patient.xml and Patient.dtd. You will be marked on
the following criteria-
• You must use a data-centric approach.
• Element and attribute names must have meaningful semantics.
• You must include descriptive comments where appropriate, including
detailed comments describing the model and why you have chosen to
model the data as you have.
• Patient.xml must validate against Patient.dtd. Validation errors
would lead to heavy penalty.

### Task 2 [10 marks] – XSD
The DatabaseInventory.dtd file is an external DTD, existing in a separate file from
the XML file (DatabaseInventory.xml) referencing it. Both of these files have been
supplied as a zipped archive called SupportingFiles.zip.
#### DatabaseInventory.dtd
```
<!ELEMENT DatabaseInventory (DatabaseName+)>
<!ELEMENT DatabaseName (GlobalDatabaseName
, OracleSID
, DatabaseDomain
, Administrator+
, DatabaseAttributes
, Comments)
>
<!ELEMENT GlobalDatabaseName (#PCDATA)>
<!ELEMENT OracleSID (#PCDATA)>
<!ELEMENT DatabaseDomain (#PCDATA)>
<!ELEMENT Administrator (#PCDATA)>
<!ELEMENT DatabaseAttributes EMPTY>
<!ELEMENT Comments (#PCDATA)>
<!ATTLIST Administrator EmailAlias CDATA #REQUIRED>
<!ATTLIST Administrator Extension CDATA #IMPLIED>
<!ATTLIST DatabaseAttributes Type (Production|Development|Testing) #REQUIRED>
<!ATTLIST DatabaseAttributes Version (7|8|8i|9i) "9i">
```
#### DatabaseInventory.xml
```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE DatabaseInventory SYSTEM "DatabaseInventory.dtd">
<DatabaseInventory>
<DatabaseName>
<GlobalDatabaseName>production.iDevelopment.info</GlobalDatabaseName>
<OracleSID>Production</OracleSID>
<DatabaseDomain>iDevelopment.info</DatabaseDomain>
<Administrator EmailAlias="jhunter"
Extension="6007"> Jeffrey Hunter
</Administrator>
<DatabaseAttributes Type="Production"
Version="9i"/>
<Comments>
The following database should be considered the most stable for
up-to-date data. The backup strategy includes running the
database in Archive Log Mode and performing nightly backup ……
</Comments>
</DatabaseName>
<!--
other elements have been omitted here, kindly look at the supplied file
-->
</DatabaseInventory>
```

Your task is to create an XML Schema DatabaseInventory.xsd from the given
DatabaseInventory.dtd and DatabaseInventory.xml.

Your XSD must also fulfil the following requirements:
a. There are at most three Administrator per database;
b. The element Comments is less than 100 characters in length;
c. The attribute Extension is 4 digits in length beginning with “6”;
d. The value of element OracleSID must be one from Production, Development, or Testing.
(Note: this will be exactly the same as attribute DatabaseAttributes, please design your schema to maximize reuse.)

You must include descriptive comments where appropriate, including detailed comments describing the model.
Your XSD must be neatly indented.
Make sure you remove the DOCTYPE declaration and provide a link from the XML document to the XML Schema.
