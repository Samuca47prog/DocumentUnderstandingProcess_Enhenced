# Document Understanding Process

This is the VB.net variant of the Document Understanding Process

# License
Please check the license in the file under: DocumentUnderstandingProcess/VB/LICENSE or read below:

#### Copyright UiPath 2024

LEGAL NOTICE: 
By installing and using this software, you (individual or legal entity) agree to the applicable LICENSE AGREEMENT available here:

https://www.uipath.com/developers/all-editions/license-agreement

Please read it carefully.
If you disagree with the license agreement, do not install or use the software and delete it from your computer.

# Usage
Please see the attached User Guide and the official documentation for more details about the template and on how to get started.

# Notes

- This process you see here is a 'template' type project in UiPath Studio. As such, if you downloaded it directly from git,
it is recommended you publish it manually to a nuget or copy/paste everything in a process.

- You should be able to get this from the official feed in UiPath Studio as well, and that is the recommended way to use this.

----


# Entities diagram

```mermaid
erDiagram
DOCUMENTUNDERSTANDING {
  GUID Id PK
  NVARCHAR(300) TargetFile
  NVARCHAR(200) logKey
}

CLASSIFICATIONRESULT {
  GUID Id PK
  NVARCHAR(200) ClassifierName
  DECIMAL(4) Confidence
  UNIQUEIDENTIFIER DocumentId FK
  NVARCHAR(400) DocumentTypeId
  DECIMAL(2) OcrConfidence
  DECIMAL StartPage
  DECIMAL PageCount
  DECIMAL TextLength
  DECIMAL TextStartIndex
  NVARCHAR(200) logKey
}

CLASSIFICATIONVALIDATION {
  GUID Id PK
  UNIQUEIDENTIFIER DocumentID FK
  NVARCHAR(400) DocumentTypeID
  DECIMAL StartPage
  DECIMAL PageCount
  DECIMAL(2) TextLength
  DECIMAL(2) TextStartIndex
  NVARCHAR(200) logKey
}

EXTRACTIONRESULT {
  GUID Id PK
  UNIQUEIDENTIFIER DocumentId FK
  BIT Validated
  NVARCHAR(400) Bounds
  NVARCHAR(200) Language
  NVARCHAR(200) DocumentTypeId
  NVARCHAR(4000) BusinessRules
}

EXTRACTIONFIELDS {
  GUID Id PK
  UNIQUEIDENTIFIER ExtractionResultId FK
  NVARCHAR(200) Name
  BIT IsMissing
  NVARCHAR(2000) Value
  NVARCHAR(2000) UnformattedValue
  NVARCHAR(2000) ValidatedValue
  DECIMAL(4) Confidence
  DECIMAL(4) OcrConfidence
  DECIMAL(2) TextType
}

EXTRACTIONTABLES {
  GUID Id PK
  UNIQUEIDENTIFIER ExtractionResultId FK
  NVARCHAR(200) Name
  BIT IsMissing
  DECIMAL(2) ColumnIndex
  DECIMAL(2) RowIndex
  NVARCHAR(4000) Value
  DECIMAL(2) TextType
  DECIMAL(4) Confidence
  DECIMAL(4) OcrConfidence
  BIT IsHeader
  NVARCHAR(4000) UnformattedValue
  NVARCHAR(2000) ValidatedValue
}

%% Relationships (cardinality from parent to children)
DOCUMENTUNDERSTANDING ||--o{ CLASSIFICATIONRESULT    : "via DocumentId"
DOCUMENTUNDERSTANDING ||--o{ CLASSIFICATIONVALIDATION: "via DocumentID"
DOCUMENTUNDERSTANDING ||--o{ EXTRACTIONRESULT        : "via DocumentId"

EXTRACTIONRESULT ||--o{ EXTRACTIONFIELDS : "via ExtractionResult"
EXTRACTIONRESULT ||--o{ EXTRACTIONTABLES : "via ExtractionResult"
```
