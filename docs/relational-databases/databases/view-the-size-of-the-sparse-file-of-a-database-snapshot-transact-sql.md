---
title: "Просмотр размера разреженного файла снимка базы данных (Transact-SQL) | Документация Майкрософт"
ms.date: 07/28/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: databases
ms.reviewer: 
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- snapshots [SQL Server database snapshots], sparse files
- space [SQL Server], sparse files
- sparse files [SQL Server]
- size [SQL Server], sparse files
- maximum sparse file size
- database snapshots [SQL Server], sparse files
- space [SQL Server], database snapshots
ms.assetid: 1867c5f8-d57c-46d3-933d-3642ab0a8e24
caps.latest.revision: "41"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1696e51f0f523a98f3bc3acdbb36bd97b9cf0f22
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/18/2018
---
# <a name="view-the-size-of-the-sparse-file-of-a-database-snapshot-transact-sql"></a>Просмотр размера разреженного файла снимка базы данных (Transact-SQL)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] В этом разделе описывается использование [!INCLUDE[tsql](../../includes/tsql-md.md)] для проверки того, является ли файл базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] разреженным файлом, и для определения фактического и максимального размеров. Разреженные файлы, которые являются средством файловой системы NTFS, используются моментальными снимками базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
> [!NOTE]  
>  При создании моментального снимка базы данных разреженные файлы создаются с помощью имен файлов, указанных в инструкции CREATE DATABASE. Эти имена файлов хранятся в таблице **sys.master_files** в столбце **physical_name** . В таблице **sys.database_files** (в базе данных-источнике или в моментальном снимке) столбец **physical_name** всегда содержит имена файлов базы данных-источника.  
  
## <a name="verify-that-a-database-file-is-a-sparse-file"></a>Убедитесь, что файл базы данных является разреженным файлом  
  
1.  В экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
     Выберите столбец **is_sparse** в таблице **sys.database_files** в моментальном снимке базы данных или в таблице **sys.master_files**. Значение указывает, является ли файл разреженным, следующим образом:  
  
     1 = разреженный файл.  
  
     0 = неразреженный файл.  
  
## <a name="find-out-the-actual-size-of-a-sparse-file"></a>Определение фактического размера разреженного файла  
  
> [!NOTE]  
>  Разреженные файлы каждый раз увеличиваются в размере на 64 килобайта (КБ); таким образом, размер разреженного файла на диске всегда кратен 64 КБ.  
  
 Для определения числа байтов, используемых в настоящее время на диске каждым разреженным файлом моментального снимка, необходимо запросить столбец **size_on_disk_bytes** динамического административного представления [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]sys.dm_io_virtual_file_stats[ в ](../../relational-databases/system-dynamic-management-views/sys-dm-io-virtual-file-stats-transact-sql.md).  
  
 Чтобы увидеть место на диске, занимаемое разреженным файлом, можно щелкнуть правой кнопкой мыши файл в Microsoft Windows, выбрать пункт **Свойства** и просмотреть значение **Место на диске**.  
  
## <a name="find-out-the-maximum-size-of-a-sparse-file"></a>Определение максимального размера разреженного файла  
 Максимальный размер, до которого может увеличиться разреженный файл, равен размеру соответствующего файла базы данных-источника на момент создания моментального снимка. Чтобы узнать этот размер, можно использовать один из следующих способов.  
  
-   Использование командной строки Windows.  
  
    1.  Использование команд Windows **dir** .  
  
    2.  Выбор разреженного файла, открытие диалогового окна **Свойства** в Windows и просмотр значения **Размер** .  
  
-   В экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
     Выбрать столбец **size** из таблицы **sys.database_files** в моментальном снимке базы данных или из таблицы **sys.master_files**. Значение столбца **size** отражает максимальный объем пространства (в страницах SQL), который может когда-либо использоваться моментальным снимком; это значение эквивалентно значению поля Windows **Size** , за исключением того, что оно представлено в терминах количества страниц SQL в файле; размер в байтах равен:  
  
     ( *число_страниц* * 8192)  

## <a name="example"></a>Пример
Следующий скрипт отображается размер в килобайтах для каждого разреженного файла.  Скрипт также указывает максимальный размер в мегабайтах, до которого может увеличиться разреженный файл.  Выполните скрипт Transact-SQL в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].

```sql
SELECT  DB_NAME(sd.source_database_id) AS [SourceDatabase], 
        sd.name AS [Snapshot],
        mf.name AS [Filename], 
        size_on_disk_bytes/1024 AS [size_on_disk (KB)],
        mf2.size/128 AS [MaximumSize (MB)]
FROM sys.master_files mf
JOIN sys.databases sd
    ON mf.database_id = sd.database_id
JOIN sys.master_files mf2
    ON sd.source_database_id = mf2.database_id
    AND mf.file_id = mf2.file_id
CROSS APPLY sys.dm_io_virtual_file_stats(sd.database_id, mf.file_id)
WHERE mf.is_sparse = 1
AND mf2.is_sparse = 0
ORDER BY 1;
```
  
## <a name="see-also"></a>См. также:  
 [Моментальные снимки базы данных (SQL Server)](../../relational-databases/databases/database-snapshots-sql-server.md)   
 [sys.fn_virtualfilestats (Transact-SQL)](../../relational-databases/system-functions/sys-fn-virtualfilestats-transact-sql.md)   
 [sys.database_files (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
 [sys.master_files (Transact-SQL)](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)  
  
  
