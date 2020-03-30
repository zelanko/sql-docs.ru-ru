---
title: Подготовка массового импорта данных (SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- bulk importing [SQL Server], about bulk importing
- BULK INSERT statement, guidelines
- BULK INSERT statement, restrictions
- bcp utility [SQL Server], guidelines
- bcp utility [SQL Server], restrictions
- hidden characters
- OPENROWSET function, BCP guidelines
ms.assetid: a82ef43c-d006-4c71-bfca-f001a3ba1ba0
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b65577b7f6b69bd4fb27392a7d71a2d68f17d7c5
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "68063163"
---
# <a name="prepare-to-bulk-import-data-sql-server"></a>Подготовка массового импорта данных (SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Команда **bcp** , инструкция BULK INSERT и функция OPENROWSET(BULK) могут быть использованы только для массового импорта из файла данных.  
  
> [!NOTE]  
>  Однако можно написать пользовательское приложение, которое будет выполнять массовый импорт из объектов, отличных от текстовых файлов. Чтобы выполнить массовый импорт из буферов памяти, можно использовать либо расширения bcp API-интерфейса собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (ODBC), либо интерфейс OLE DB **IRowsetFastLoad** .  Чтобы выполнить массовый импорт из таблицы данных C#, необходимо использовать API-интерфейс ADO.NET для операций массового копирования **SqlBulkCopy**.  
  
> [!NOTE]  
>  Массовый импорт данных в удаленную таблицу не поддерживается.  
  
 При массовом импорте данных из файла данных в экземпляр [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] следует руководствоваться следующими правилами.  
  
-   Получите необходимые разрешения для учетной записи пользователя.  
  
     Учетная запись пользователя, от имени которой выполняются программа **bcp** , инструкции BULK INSERT или INSERT... SELECT * FROM OPENROWSET(BULK...), должна иметь соответствующие разрешения для таблицы (назначаемые владельцем таблицы). Дополнительные сведения о разрешениях, необходимых для каждого метода, см. в разделах [Программа bcp](../../tools/bcp-utility.md), [OPENROWSET (Transact-SQL)](../../t-sql/functions/openrowset-transact-sql.md)и [BULK INSERT (Transact-SQL)](../../t-sql/statements/bulk-insert-transact-sql.md).  
  
-   Используйте модель восстановления с неполным протоколированием.  
  
     Данное правило относится к базам данных, использующим модель полного восстановления. Эта модель восстановления полезна при выполнении массовых операций в неиндексированной таблице ( *куче*). Восстановление с неполным протоколированием позволяет избежать переполнения журнала транзакций, поскольку при этом не выполняется операция записи в журнал для вставок отдельных строк. Дополнительные сведения о модели восстановления с неполным протоколированием см. в разделе [Модели восстановления (SQL Server)](../../relational-databases/backup-restore/recovery-models-sql-server.md).  
  
     Рекомендуется настроить базу данных на использование модели восстановления с неполным протоколированием до операции массового импорта. Сразу же необходимо переключить базу данных на модель полного восстановления. Дополнительные сведения см. в разделе [Просмотр или изменение модели восстановления базы данных (SQL Server)](../../relational-databases/backup-restore/view-or-change-the-recovery-model-of-a-database-sql-server.md).  
  
    > [!NOTE]  
    >  Дополнительные сведения о сокращении до минимума объема данных, выводимых в журнал при выполнении операций массового импорта, см. в разделе [Предварительные условия для минимального протоколирования массового импорта данных](../../relational-databases/import-export/prerequisites-for-minimal-logging-in-bulk-import.md).  
  
-   Резервное копирование после массового импорта данных.  
  
     Для баз данных, использующих простую модель восстановления, после выполнения операции массового импорта рекомендуется создание полной или разностной резервной копии. Дополнительные сведения см. в разделах [Создание полной резервной копии базы данных (SQL Server)](../../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md) или [Создание разностной резервной копии базы данных (SQL Server)](../../relational-databases/backup-restore/create-a-differential-database-backup-sql-server.md).  
  
     Чтобы произвести полное восстановление или восстановление с неполным протоколированием, достаточно создать резервную копию журнала. Дополнительные сведения см. в разделе [Резервные копии журналов транзакций (SQL Server)](../../relational-databases/backup-restore/transaction-log-backups-sql-server.md).  
  
-   Удаление индексов таблиц для улучшения производительности при выполнении больших операций массового импорта.  
  
     Данное правило справедливо при импорте большого объема данных по сравнению с объемом данных, уже находящимся в таблице. В этом случае удаление индексов из таблицы до выполнения операции массового импорта позволит существенно повысить производительность.  
  
    > [!NOTE]  
    >  Однако если меньший объем загружаемых данных уже находится в таблице, то удаление индексов, наоборот, понизит производительность. В этом случае восстановление индексов может занять больше времени, чем будет сэкономлено во время операции массового импорта.  
  
-   Найдите и удалите скрытые символы в файле данных.  
  
     Многие программы и текстовые редакторы отображают скрытые символы, находящиеся обычно в конце файла данных. Во время операции массового импорта скрытые символы в файле данных в формате ASCII могут привести к появлению сообщения об ошибке «Обнаружено непредвиденное значение NULL». Чтобы решить проблему, обычно необходимо найти и удалить все скрытые символы.  
  
## <a name="see-also"></a>См. также:  
 [Массовый импорт и экспорт данных с использованием программы bcp (SQL Server)](../../relational-databases/import-export/import-and-export-bulk-data-by-using-the-bcp-utility-sql-server.md)   
 [Массовый импорт данных при помощи инструкции BULK INSERT или OPENROWSET(BULK...) (SQL Server)](../../relational-databases/import-export/import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md)   
 [bcp Utility](../../tools/bcp-utility.md)   
 [BULK INSERT (Transact-SQL)](../../t-sql/statements/bulk-insert-transact-sql.md)   
 [Форматы данных для массового экспорта или импорта (SQL Server)](../../relational-databases/import-export/data-formats-for-bulk-import-or-bulk-export-sql-server.md)   
 [OPENROWSET (Transact-SQL)](../../t-sql/functions/openrowset-transact-sql.md)  
  
  
