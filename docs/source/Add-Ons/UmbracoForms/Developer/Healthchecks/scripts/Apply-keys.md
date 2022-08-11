---
meta.Title: "Apply keys and indexes"
---

# Apply keys and indexes

```sql
/*
 Applies recommended primary keys, foreign keys and indexes to core Umbraco Forms tables.
 This replicates for SQL Server the migration AddRecordKeysAndIndexes.
 */

-- Adds relationship between UFRecords and UFRecordFields.
ALTER TABLE dbo.UFRecordFields
ADD CONSTRAINT
  FK_UFRecordFields_UFRecords_Record FOREIGN KEY
  (
  Record
  ) REFERENCES dbo.UFRecords
  (
  Id
  ) ON UPDATE  NO ACTION 
   ON DELETE  NO ACTION 
GO

-- Adds primary keys to UFRecordData* tables.
ALTER TABLE dbo.UFRecordDataBit
ADD CONSTRAINT
  PK_UFRecordDataBit PRIMARY KEY CLUSTERED 
  (
  Id
  ) WITH( STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
GO

ALTER TABLE dbo.UFRecordDataDateTime
ADD CONSTRAINT
  PK_UFRecordDataDateTime PRIMARY KEY CLUSTERED 
  (
  Id
  ) WITH( STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
GO

ALTER TABLE dbo.UFRecordDataInteger
ADD CONSTRAINT
  PK_UFRecordDataInteger PRIMARY KEY CLUSTERED 
  (
  Id
  ) WITH( STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
GO

ALTER TABLE dbo.UFRecordDataLongString
ADD CONSTRAINT
  PK_UFRecordDataLongString PRIMARY KEY CLUSTERED 
  (
  Id
  ) WITH( STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
GO
