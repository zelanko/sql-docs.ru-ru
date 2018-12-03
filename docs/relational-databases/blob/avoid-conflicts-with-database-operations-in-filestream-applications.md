---
title: Предотвращение конфликтов при работе с базой данных в приложениях FILESTREAM | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], Win32 and Transact-SQL Conflicts
ms.assetid: 8b1ee196-69af-4f9b-9bf5-63d8ac2bc39b
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: b5967b38a0bcc648bf02a5b3c6fa404b31eaaccf
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/28/2018
ms.locfileid: "52540629"
---
# <a name="avoid-conflicts-with-database-operations-in-filestream-applications"></a>Избегание конфликтов в операциях баз данных в приложениях FILESTREAM
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Приложения, использующие функцию SqlOpenFilestream() для открытия дескрипторов файлов Win32 для считывания или записи данных FILESTREAM BLOB, могут столкнуться с конфликтами при работе с инструкциями [!INCLUDE[tsql](../../includes/tsql-md.md)] , использованными в общей транзакции. Это также относится и к запросам [!INCLUDE[tsql](../../includes/tsql-md.md)] или MARS, выполнение которых занимает много времени. При разработке приложений надо уделить особое внимание предотвращению данных типов конфликтов.  
  
 Если компонент [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] или приложения пытаются открыть объекты FILESTREAM BLOB, то компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] выполнит проверку контекста ассоциированной транзакции. Компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] разрешит или запретит запрос в зависимости от того, работает ли операция открытия с инструкциями DDL, инструкциями DML, получает данные или управляет транзакциями. В следующей таблице показывается, как компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] определяет, следует ли разрешить или запретить инструкцию [!INCLUDE[tsql](../../includes/tsql-md.md)] , основываясь на типе файлов, открытых в транзакции.  
  
|Инструкции Transact-SQL|Открыты для чтения|Открыты для записи|  
|------------------------------|---------------------|----------------------|  
|Инструкции DDL, работающие с метаданными базы данных, например CREATE TABLE, CREATE INDEX, DROP TABLE и ALTER TABLE.|Разрешено|Заблокированы и завершаются со сбоем по истечении времени ожидания.|  
|Инструкции DML, работающие с данными, хранящимися в базе данных, например UPDATE, DELETE и INSERT.|Разрешено|Запрещены|  
|SELECT|Разрешено|Разрешено|  
|COMMIT TRANSACTION|Запрещены*|Запрещены*|  
|SAVE TRANSACTION|Запрещены*|Запрещены*|  
|ROLLBACK|Разрешено*|Разрешено*|  
  
 \* Транзакция отменяется, а открытые дескрипторы для контекста транзакции становятся недействительными. Приложение должно закрыть все открытые дескрипторы.  
  
## <a name="examples"></a>Примеры  
 В следующих примерах показывается, как могут возникать конфликты при совместном использовании инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)] и доступа к FILESTREAM с помощью функций Win32.  
  
### <a name="a-opening-a-filestream-blob-for-write-access"></a>A. Открытие объекта FILESTREAM BLOB с доступом на запись  
 В следующем примере показывается эффект от открытия файла с доступом только на запись.  
  
```  
dstHandle =  OpenSqlFilestream(dstFilePath, Write, 0,  
    transactionToken, cbTransactionToken, 0);  
  
//Write some date to the FILESTREAM BLOB.  
WriteFile(dstHandle, updateData, ...);  
  
//DDL statements will be denied.  
//DML statements will be denied.  
//SELECT statements will be allowed. The FILESTREAM BLOB is  
//returned without the modifications that are made by  
//WriteFile(dstHandle, updateData, ...).  
CloseHandle(dstHandle);  
  
//DDL statements will be allowed.  
//DML statements will be allowed.  
//SELECT statements will be allowed. The FILESTREAM BLOB  
//is returned with the updateData applied.  
```  
  
### <a name="b-opening-a-filestream-blob-for-read-access"></a>Б. Открытие объекта FILESTREAM BLOB с доступом на считывание  
 В следующем примере показывается эффект от открытия файла с доступом только на считывание.  
  
```  
dstHandle =  OpenSqlFilestream(dstFilePath, Read, 0,  
    transactionToken, cbTransactionToken, 0);  
//DDL statements will be denied.  
//DML statements will be allowed. Any changes that are  
//made to the FILESTREAM BLOB will not be returned until  
//the dstHandle is closed.  
//SELECT statements will be allowed.  
CloseHandle(dstHandle);  
  
//DDL statements will be allowed.  
//DML statements will be allowed.  
//SELECT statements will be allowed.  
```  
  
### <a name="c-opening-and-closing-multiple-filestream-blob-files"></a>В. Открытие и закрытие нескольких файлов FILESTREAM BLOB  
 Если открыто несколько файлов, то используется правило с наибольшими ограничениями. В следующем примере открываются два файла. Первый файл открывается для чтения, а второй — для записи. Инструкции DML будут запрещены, пока не будет открыт второй файл.  
  
```  
dstHandle =  OpenSqlFilestream(dstFilePath, Read, 0,  
    transactionToken, cbTransactionToken, 0);  
//DDL statements will be denied.  
//DML statements will be allowed.  
//SELECT statements will be allowed.  
  
dstHandle1 =  OpenSqlFilestream(dstFilePath1, Write, 0,  
    transactionToken, cbTransactionToken, 0);  
  
//DDL statements will be denied.  
//DML statements will be denied.  
//SELECT statements will be allowed.  
  
//Close the read handle. The write handle is still open.  
CloseHandle(dstHandle);  
//DML statements are still denied because the write handle is open.  
  
//DDL statements will be denied.  
//DML statements will be denied.  
//SELECT statements will be allowed.  
  
CloseHandle(dstHandle1);  
//DDL statements will be allowed.  
//DML statements will be allowed.  
//SELECT statements will be allowed.  
```  
  
### <a name="d-failing-to-close-a-cursor"></a>Г. Сбой при закрытии курсора  
 В следующем примере показывается, как незакрытый курсор инструкции может помешать функции `OpenSqlFilestream()` открыть объект BLOB для доступа на запись.  
  
```  
TCHAR *sqlDBQuery =  
TEXT("SELECT GET_FILESTREAM_TRANSACTION_CONTEXT(),")  
TEXT("Chart.PathName() FROM Archive.dbo.Records");  
  
//Execute a long-running Transact-SQL statement. Do not allow  
//the statement to complete before trying to  
//open the file.  
  
SQLExecDirect(hstmt, sqlDBQuery, SQL_NTS);  
  
//Before you call OpenSqlFilestream() any open files  
//that the Cursor the Transact-SQL statement is using  
// must be closed. In this example,  
//SQLCloseCursor(hstmt) is not called so that  
//the transaction will indicate that there is a file  
//open for reading. This will cause the call to  
//OpenSqlFilestream() to fail because the file is  
//still open.  
  
HANDLE srcHandle =  OpenSqlFilestream(srcFilePath,  
     Write, 0,  transactionToken,  cbTransactionToken,  0);  
  
//srcHandle will == INVALID_HANDLE_VALUE because the  
//cursor is still open.  
```  
  
## <a name="see-also"></a>См. также:  
 [Доступ к данным FILESTREAM с OpenSqlFilestream](../../relational-databases/blob/access-filestream-data-with-opensqlfilestream.md)   
 [Использование множественных активных результирующих наборов (MARS)](../../relational-databases/native-client/features/using-multiple-active-result-sets-mars.md)  
  
  
