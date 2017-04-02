---
title: "Массовый импорт данных больших объектов при помощи поставщика больших наборов строк OPENROWSET (SQL Server) | Microsoft Docs"
ms.custom: ""
ms.date: "03/23/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-bulk-import-export"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SINGLE_NCLOB, параметр"
  - "поставщики больших наборов строк [SQL Server]"
  - "массовый импорт [SQL Server], форматы данных"
  - "функция OPENROWSET, массовый импорт данных большого объема"
  - "SINGLE_CLOB, параметр"
  - "форматы данных [SQL Server], большие объекты данных"
  - "данные большого объема, массовый импорт"
  - "SINGLE_BLOB, параметр"
ms.assetid: 171cdd5c-1e47-4bd7-b99a-4f0fd4e10526
caps.latest.revision: 16
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
---
# Массовый импорт данных больших объектов при помощи поставщика больших наборов строк OPENROWSET (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Поставщик больших наборов строк OPENROWSET в среде [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] позволяет выполнять массовый импорт файла данных как большого объекта данных.  
  
 Поставщик больших наборов строк OPENROWSET поддерживает следующие типы больших объектов данных: **varbinary**(max) или **image**, **varchar**(max) или **text** и **nvarchar**(max) или **ntext**.  
  
> [!NOTE]  
>  Типы данных **image**, **text** и **ntext** считаются устаревшими.  
  
 В предложении OPENROWSET BULK поддерживаются три параметра для импорта содержимого файла данных в виде однострочного набора строк с одним столбцом. Вместо файла форматирования можно указать один из данных параметров для больших объектов. Это следующие параметры:  
  
 SINGLE_BLOB  
 Считывает содержимое файла *data_file* в одну строку и возвращает его в виде набора строк, состоящего из одного столбца типа **varbinary(max)**.  
  
 SINGLE_CLOB  
 Считывает содержимое указанного файла данных в виде символов и возвращает его в виде набора строк, состоящего из одной строки и одного столбца типа **varchar(max)**, с параметрами сортировки текущей базы данных; это может быть, например, текстовый документ или документ [!INCLUDE[msCoName](../../includes/msconame-md.md)] Word.  
  
 SINGLE_NCLOB  
 Считывает содержимое указанного файла данных в кодировке Юникод и возвращает содержимое в виде набора строк, состоящего из одной строки и одного столбца типа **varchar(max)**, с параметрами сортировки текущей базы данных.  
  
## См. также:  
 [Массовый импорт данных при помощи инструкции BULK INSERT или OPENROWSET(BULK...) (SQL Server)](../../relational-databases/import-export/import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md)   
 [BACKUP (Transact-SQL)](../../t-sql/statements/backup-transact-sql.md)   
 [OPENROWSET (Transact-SQL)](../../t-sql/functions/openrowset-transact-sql.md)   
 [Сохранение значений NULL или использование значений по умолчанию при массовом импорте данных (SQL Server)](../../relational-databases/import-export/keep-nulls-or-use-default-values-during-bulk-import-sql-server.md)   
 [Программа bcp](../../tools/bcp-utility.md)   
 [BULK INSERT (Transact-SQL)](../../t-sql/statements/bulk-insert-transact-sql.md)  
  
  