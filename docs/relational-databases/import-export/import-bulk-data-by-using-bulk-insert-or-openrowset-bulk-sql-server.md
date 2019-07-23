---
title: Массовый импорт данных при помощи инструкции BULK INSERT или OPENROWSET(BULK...) (SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 07/26/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- BULK INSERT statement, importing data from a remote data file
- bulk importing [SQL Server], methods
- bulk exporting [SQL Server], methods
- OPENROWSET function, BULK INSERT
- bulk importing [SQL Server], security
- bulk rowset providers [SQL Server]
- bulk exporting [SQL Server], BULK INSERT statement
- remote data access [SQL Server], bulk importing
- bulk importing [SQL Server], BULK INSERT statement
- Transact-SQL bulk export/import operations
ms.assetid: 18a64236-0285-46ea-8929-6ee9bcc020b9
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 67f549c0806c0c368aed902407f1fd72fab38025
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68027913"
---
# <a name="import-bulk-data-by-using-bulk-insert-or-openrowsetbulk-sql-server"></a>Массовый импорт данных при помощи инструкции BULK INSERT или OPENROWSET(BULK...) (SQL Server)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  Этот раздел содержит общие сведения об использовании инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)] BULK INSERT и INSERT...SELECT * FROM OPENROWSET(BULK...) для массового импорта данных из файла данных в таблицу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . В разделе также описываются вопросы безопасности при использовании BULK INSERT и OPENROWSET(BULK…), а также применение этих методов для массового импорта из удаленного источника данных.  
  
> [!NOTE]
> При использовании инструкции BULK INSERT или OPENROWSET(BULK…) важно понимать, каким образом выполняется олицетворение в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и более поздних версиях. Дополнительные сведения см. в подразделе «Вопросы безопасности» далее в этом разделе.  
  
## <a name="bulk-insert-statement"></a>BULK INSERT, инструкция  
 Инструкция BULK INSERT загружает данные из файла данных в таблицу. Эти функциональные возможности аналогичны тем, которые предоставляются параметром **in** команды **bcp** , но чтение файла данных выполняется процессом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Описание синтаксиса инструкции BULK INSERT см. в разделе [BULK INSERT (Transact-SQL)](../../t-sql/statements/bulk-insert-transact-sql.md).  
  
## <a name="bulk-insert-examples"></a>Примеры BULK INSERT  
 
  
-   [BULK INSERT (Transact-SQL)](../../t-sql/statements/bulk-insert-transact-sql.md)  
  
-   [Примеры массового импорта и экспорта XML-документов (SQL Server)](../../relational-databases/import-export/examples-of-bulk-import-and-export-of-xml-documents-sql-server.md)  
  
-   [Сохранение значений идентификаторов при массовом импорте данных (SQL Server)](../../relational-databases/import-export/keep-identity-values-when-bulk-importing-data-sql-server.md)  
  
-   [Сохранение значений NULL или использование значений по умолчанию при массовом импорте данных (SQL Server)](../../relational-databases/import-export/keep-nulls-or-use-default-values-during-bulk-import-sql-server.md)  
  
-   [Определение признаков конца поля и строки (SQL Server)](../../relational-databases/import-export/specify-field-and-row-terminators-sql-server.md)  
  
-   [Использование файла форматирования для массового импорта данных (SQL Server)](../../relational-databases/import-export/use-a-format-file-to-bulk-import-data-sql-server.md)  
  
-   [Использование символьного формата для импорта и экспорта данных (SQL Server)](../../relational-databases/import-export/use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Использование собственного формата для импорта и экспорта данных (SQL Server)](../../relational-databases/import-export/use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [Использование символьного формата Юникод для импорта и экспорта данных (SQL Server)](../../relational-databases/import-export/use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Использование собственного формата Юникод для импорта и экспорта данных (SQL Server)](../../relational-databases/import-export/use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
-   [Пропуск столбца таблицы с помощью файла форматирования (SQL Server)](../../relational-databases/import-export/use-a-format-file-to-skip-a-table-column-sql-server.md)  
  
-   [Использование файла форматирования для сопоставления столбцов таблицы с полями файла данных (SQL Server)](../../relational-databases/import-export/use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  
## <a name="openrowsetbulk-function"></a>OPENROWSET(BULK...) Компонент  
 Доступ к поставщику больших наборов строк OPENROWSET осуществляется путем вызова функции OPENROWSET и задания параметра BULK. Функция OPENROWSET(BULK...) обеспечивает доступ к удаленным данным, производя соединение с удаленным источником данных, например файлом данных, через поставщик OLE DB.  

**Применимо к:** `OPENROWSET` недоступно в [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)].
  
 Чтобы импортировать групповые данные, вызовите функцию OPENROWSET(BULK...) из предложения SELECT...FROM инструкции INSERT. Основной синтаксис массового импорта данных:  
  
 Инструкции INSERT ... SELECT * FROM OPENROWSET(BULK...).  
  
 При использовании инструкции INSERT функция OPENROWSET(BULK...) поддерживает табличные указания. Кроме обычных табличных указаний вроде TABLOCK, предложение BULK принимает следующие специальные табличные указания: IGNORE_CONSTRAINTS (не учитывается только ограничения CHECK), IGNORE_TRIGGERS, KEEPDEFAULTS и KEEPIDENTITY. Дополнительные сведения см. в разделе [Табличные указания (Transact-SQL)](../../t-sql/queries/hints-transact-sql-table.md).  
  
 Сведения о дополнительном использовании параметра BULK см. в разделе [OPENROWSET (Transact-SQL)](../../t-sql/functions/openrowset-transact-sql.md).  
  
## <a name="insertselect--from-openrowsetbulk-statements---examples"></a>Инструкции INSERT...SELECT * FROM OPENROWSET(BULK...) — примеры:
  
-   [Примеры массового импорта и экспорта XML-документов (SQL Server)](../../relational-databases/import-export/examples-of-bulk-import-and-export-of-xml-documents-sql-server.md)  
  
-   [Сохранение значений идентификаторов при массовом импорте данных (SQL Server)](../../relational-databases/import-export/keep-identity-values-when-bulk-importing-data-sql-server.md)  
  
-   [Сохранение значений NULL или использование значений по умолчанию при массовом импорте данных (SQL Server)](../../relational-databases/import-export/keep-nulls-or-use-default-values-during-bulk-import-sql-server.md)  
  
-   [Использование файла форматирования для массового импорта данных (SQL Server)](../../relational-databases/import-export/use-a-format-file-to-bulk-import-data-sql-server.md)  
  
-   [Использование символьного формата для импорта и экспорта данных (SQL Server)](../../relational-databases/import-export/use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Пропуск столбца таблицы с помощью файла форматирования (SQL Server)](../../relational-databases/import-export/use-a-format-file-to-skip-a-table-column-sql-server.md)  
  
-   [Использование файла форматирования для пропуска поля данных (SQL Server)](../../relational-databases/import-export/use-a-format-file-to-skip-a-data-field-sql-server.md)  
  
-   [Использование файла форматирования для сопоставления столбцов таблицы с полями файла данных (SQL Server)](../../relational-databases/import-export/use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  
## <a name="security-considerations"></a>Вопросы безопасности  
 Если пользователь использует имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , то применяется профиль безопасности учетной записи процесса [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . За пределами компонента Database Engine невозможно выполнить проверку подлинности имени входа, проходящего проверку подлинности SQL Server. Поэтому, если имя входа, использующее проверку подлинности SQL Server, инициирует команду BULK INSERT, подключение к данным устанавливается с помощью контекста безопасности учетной записи процесса SQL Server (учетной записи, которая используется службой SQL Server Database Engine). 
 
 Для того чтобы прочитать исходные данные, учетной записи, которая используется службой SQL Server Database Engine, необходимо предоставить доступ к этим исходным данным. Если пользователь [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] входит в систему с проверкой подлинности Windows, то ему доступны только те файлы, к которым имеет доступ учетная запись пользователя, независимо от профиля безопасности процесса [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Предположим, пользователь вошел в экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с проверкой подлинности Windows. Чтобы иметь возможность воспользоваться BULK INSERT или OPENROWSET для импорта данных из файла данных в таблицу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , учетная запись должна иметь доступ на чтение этого файла данных. Если же пользователь имеет доступ к файлу данных, то он может импортировать данные из файла в таблицу даже в том случае, когда процесс [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не имеет прав доступа к файлу. Пользователь не должен предоставлять процессу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] права на доступ к файлу.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows могут быть настроены таким образом, чтобы экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] мог выполнять соединение с другим экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] посредством переадресации учетных данных пользователя Windows, прошедшего проверку подлинности. Такой подход называется *олицетворением* или *делегированием*. При использовании инструкции BULK INSERT или OPENROWSET очень важно понимать, каким образом в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и более поздних версиях обеспечивается безопасность при олицетворении пользователя. Это позволяет хранить файл данных не на том компьютере, на котором вошел пользователь или работает процесс [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Например, если пользователь на **компьютере_A** имеет доступ к файлу данных на **компьютере_B**и делегирование учетных данных было соответствующим образом настроено, этот пользователь может подключиться к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , запущенному на **компьютере_C**, получить доступ к файлу данных на **компьютере_B**и выполнить массовый импорт данных из этого файла в таблицу на **компьютере_C**.  
  
## <a name="bulk-importing-from-a-remote-data-file"></a>Массовый импорт из удаленного файла данных  
 Чтобы использовать инструкции BULK INSERT или INSERT...SELECT \* FROM OPENROWSET(BULK...) для массового импорта данных с другого компьютера, необходимо, чтобы файл данных был доступен на обоих компьютерах. Укажите общий файл данных в формате UNC, то есть в следующем формате: **\\\\** _Имя сервера_ **\\** _Общая папка_ **\\** _Путь_ **\\** _Имя файла_. Кроме того, используемая учетная запись должна обладать разрешениями, необходимыми для чтения этого файла на удаленном диске.  
  
 Например, инструкция `BULK INSERT` производит массовый импорт в таблицу `SalesOrderDetail` базы данных `AdventureWorks` из файла данных с именем `newdata.txt`. Этот файл данных находится в общей папке `\dailyorders`, расположенной в общем сетевом каталоге `salesforce` компьютера с именем `computer2`.  
  
```sql
BULK INSERT AdventureWorks2012.Sales.SalesOrderDetail  
   FROM '\\computer2\salesforce\dailyorders\neworders.txt';  
GO  
```  
  
> [!NOTE]
> Это ограничение не применяется к служебной программе **bcp**, потому что клиент читает файл независимо от [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>См. также раздел  
 [INSERT (Transact-SQL)](../../t-sql/statements/insert-transact-sql.md)   
 [Предложение SELECT (Transact-SQL)](../../t-sql/queries/select-clause-transact-sql.md)   
 [Массовый импорт и экспорт данных (SQL Server)](../../relational-databases/import-export/bulk-import-and-export-of-data-sql-server.md)   
 [OPENROWSET (Transact-SQL)](../../t-sql/functions/openrowset-transact-sql.md)   
 [SELECT (Transact-SQL)](../../t-sql/queries/select-transact-sql.md)   
 [FROM (Transact-SQL)](../../t-sql/queries/from-transact-sql.md)   
 [Программа bcp](../../tools/bcp-utility.md)   
 [BULK INSERT (Transact-SQL)](../../t-sql/statements/bulk-insert-transact-sql.md)  
  
  
