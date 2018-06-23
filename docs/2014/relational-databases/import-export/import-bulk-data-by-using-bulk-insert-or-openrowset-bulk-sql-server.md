---
title: Массовый импорт данных при помощи инструкции BULK INSERT или OPENROWSET(BULK...) (SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-bulk-import-export
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 41
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: b2d76310feb37fab7e3d35dcc4211cf70d15b211
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36194486"
---
# <a name="import-bulk-data-by-using-bulk-insert-or-openrowsetbulk-sql-server"></a>Массовый импорт данных при помощи инструкции BULK INSERT или OPENROWSET(BULK...) (SQL Server)
  Этот раздел содержит общие сведения об использовании инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)] BULK INSERT и INSERT...SELECT * FROM OPENROWSET(BULK...) для массового импорта данных из файла данных в таблицу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . В разделе также описываются вопросы безопасности при использовании BULK INSERT и OPENROWSET(BULK…), а также применение этих методов для массового импорта из удаленного источника данных.  
  
> [!NOTE]  
>  При использовании инструкции BULK INSERT или OPENROWSET(BULK…) важно понимать, каким образом выполняется олицетворение в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и более поздних версиях. Дополнительные сведения см. в подразделе «Вопросы безопасности» далее в этом разделе.  
  
## <a name="bulk-insert-statement"></a>Инструкция BULK INSERT  
 Инструкция BULK INSERT загружает данные из файла данных в таблицу. Эти функциональные возможности аналогичны тем, которые предоставляются параметром **in** команды **bcp** , но чтение файла данных выполняется процессом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Описание синтаксиса инструкции BULK INSERT см. в разделе [BULK INSERT (Transact-SQL)](/sql/t-sql/statements/bulk-insert-transact-sql).  
  
### <a name="examples"></a>Примеры  
 Примеры инструкции BULK INSERT:  
  
-   [BULK INSERT (Transact-SQL)](/sql/t-sql/statements/bulk-insert-transact-sql)  
  
-   [Примеры массового импорта и экспорта XML-документов (SQL Server)](examples-of-bulk-import-and-export-of-xml-documents-sql-server.md)  
  
-   [Сохранение значений идентификаторов при массовом импорте данных (SQL Server)](keep-identity-values-when-bulk-importing-data-sql-server.md)  
  
-   [Сохранение значений NULL или использование значений по умолчанию при массовом импорте данных (SQL Server)](keep-nulls-or-use-default-values-during-bulk-import-sql-server.md)  
  
-   [Определение признаков конца поля и строки (SQL Server)](specify-field-and-row-terminators-sql-server.md)  
  
-   [Использование файла форматирования для массового импорта данных (SQL Server)](use-a-format-file-to-bulk-import-data-sql-server.md)  
  
-   [Использование символьного формата для импорта и экспорта данных (SQL Server)](use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Использование собственного формата для импорта и экспорта данных (SQL Server)](use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [Использование символьного формата Юникод для импорта и экспорта данных (SQL Server)](use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Использование собственного формата Юникод для импорта и экспорта данных (SQL Server)](use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
-   [Пропуск столбца таблицы с помощью файла форматирования (SQL Server)](use-a-format-file-to-skip-a-table-column-sql-server.md)  
  
-   [Использование файла форматирования для сопоставления столбцов таблицы полям файла данных (SQL Server)](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  
## <a name="openrowsetbulk-function"></a>Функция OPENROWSET(BULK…)  
 Доступ к поставщику больших наборов строк OPENROWSET осуществляется путем вызова функции OPENROWSET и задания параметра BULK. Функция OPENROWSET(BULK…) обеспечивает доступ к удаленным данным, производя соединение с удаленным источником данных, например файлу данных, через поставщик OLE DB.  
  
 Чтобы импортировать групповые данные, вызовите функцию OPENROWSET(BULK…) из предложения SELECT…FROM инструкции INSERT. Основной синтаксис массового импорта данных:  
  
 Инструкции INSERT ... SELECT * FROM OPENROWSET(BULK...).  
  
 При использовании инструкции INSERT функция OPENROWSET(BULK...) поддерживает табличные указания. Кроме обычных табличных указаний, например TABLOCK, предложение BULK может принимать следующие специальные табличные указания: IGNORE_CONSTRAINTS (игнорирует только ограничения CHECK), IGNORE_TRIGGERS, KEEPDEFAULTS и KEEPIDENTITY. Дополнительные сведения см. в разделе [Табличные указания (Transact-SQL)](/sql/t-sql/queries/hints-transact-sql-table).  
  
 Сведения о дополнительном использовании параметра BULK см. в разделе [OPENROWSET (Transact-SQL)](/sql/t-sql/functions/openrowset-transact-sql).  
  
### <a name="examples"></a>Примеры  
 Примеры инструкций INSERT...SELECT * FROM OPENROWSET(BULK...) см. в следующих разделах:  
  
-   [Примеры массового импорта и экспорта XML-документов (SQL Server)](examples-of-bulk-import-and-export-of-xml-documents-sql-server.md)  
  
-   [Сохранение значений идентификаторов при массовом импорте данных (SQL Server)](keep-identity-values-when-bulk-importing-data-sql-server.md)  
  
-   [Сохранение значений NULL или использование значений по умолчанию при массовом импорте данных (SQL Server)](keep-nulls-or-use-default-values-during-bulk-import-sql-server.md)  
  
-   [Использование файла форматирования для массового импорта данных (SQL Server)](use-a-format-file-to-bulk-import-data-sql-server.md)  
  
-   [Использование символьного формата для импорта и экспорта данных (SQL Server)](use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Пропуск столбца таблицы с помощью файла форматирования (SQL Server)](use-a-format-file-to-skip-a-table-column-sql-server.md)  
  
-   [Использование файла форматирования для пропуска поля данных (SQL Server)](use-a-format-file-to-skip-a-data-field-sql-server.md)  
  
-   [Использование файла форматирования для сопоставления столбцов таблицы полям файла данных (SQL Server)](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  
## <a name="security-considerations"></a>Соображения безопасности  
 Если пользователь использует имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], то применяется профиль безопасности учетной записи процесса [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. За пределами компонента Database Engine невозможно выполнить проверку подлинности имени входа, проходящего проверку подлинности SQL Server. Поэтому, если имя входа, использующее проверку подлинности SQL Server, инициирует команду BULK INSERT, подключение к данным устанавливается с помощью контекста безопасности учетной записи процесса SQL Server (учетной записи, которая используется службой SQL Server Database Engine). Для того чтобы прочитать исходные данные, учетной записи, которая используется службой SQL Server Database Engine, необходимо предоставить доступ к этим исходным данным. Если пользователь [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] входит в систему с проверкой подлинности Windows, то ему доступны только те файлы, к которым имеет доступ учетная запись пользователя, независимо от профиля безопасности процесса [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Предположим, пользователь вошел в экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с проверкой подлинности Windows. Чтобы иметь возможность воспользоваться BULK INSERT или OPENROWSET для импорта данных из файла данных в таблицу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , учетная запись должна иметь доступ на чтение этого файла данных. Если же пользователь имеет доступ к файлу данных, то он может импортировать данные из файла в таблицу даже в том случае, когда процесс [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не имеет прав доступа к файлу. Пользователь не должен предоставлять процессу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] права на доступ к файлу.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows могут быть настроены таким образом, чтобы экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] мог выполнять соединение с другим экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] посредством переадресации учетных данных пользователя Windows, прошедшего проверку подлинности. Такой подход называется *олицетворением* или *делегированием*. При использовании инструкции BULK INSERT или OPENROWSET очень важно понимать, каким образом в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и более поздних версиях обеспечивается безопасность при олицетворении пользователя. Это позволяет хранить файл данных не на том компьютере, на котором вошел пользователь или работает процесс [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Например, если пользователь на **компьютере_A** имеет доступ к файлу данных на **компьютере_B** и делегирование учетных данных было соответствующим образом настроено, этот пользователь может подключиться к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], запущенному на **компьютере_C**, получить доступ к файлу данных на **компьютере_B** и выполнить массовый импорт данных из этого файла в таблицу на **компьютере_C**.  
  
## <a name="bulk-importing-from-a-remote-data-file"></a>Массовый импорт из удаленного файла данных  
 Чтобы использовать инструкции BULK INSERT или INSERT...SELECT \* FROM OPENROWSET(BULK...) для массового импорта данных с другого компьютера, необходимо, чтобы файл данных был доступен на обоих компьютерах. Укажите общий файл данных в формате UNC, то есть в следующем формате: **\\\\***Имя сервера***\\***общая папка***\\***путь***\\***имя файла*. Кроме того, используемая учетная запись должна обладать разрешениями, необходимыми для чтения этого файла на удаленном диске.  
  
 Например, инструкция `BULK INSERT` производит массовый импорт в таблицу `SalesOrderDetail` базы данных `AdventureWorks` из файла данных с именем `newdata.txt`. Этот файл данных находится в общей папке `\dailyorders`, расположенной в общем сетевом каталоге `salesforce` компьютера с именем `computer2`.  
  
```  
BULK INSERT AdventureWorks2012.Sales.SalesOrderDetail  
   FROM '\\computer2\salesforce\dailyorders\neworders.txt';  
GO  
```  
  
> [!NOTE]  
>  Это ограничение не применяется к служебной программе **bcp**, потому что клиент читает файл независимо от [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>См. также  
 [INSERT (Transact-SQL)](/sql/t-sql/statements/insert-transact-sql)   
 [Предложение SELECT (Transact-SQL)](/sql/t-sql/queries/select-clause-transact-sql)   
 [Массовый импорт и экспорт данных (SQL Server)](bulk-import-and-export-of-data-sql-server.md)   
 [OPENROWSET (Transact-SQL)](/sql/t-sql/functions/openrowset-transact-sql)   
 [SELECT (Transact-SQL)](/sql/t-sql/queries/select-transact-sql)   
 [FROM (Transact-SQL)](/sql/t-sql/queries/from-transact-sql)   
 [Программа bcp](../../tools/bcp-utility.md)   
 [BULK INSERT (Transact-SQL)](/sql/t-sql/statements/bulk-insert-transact-sql)  
  
  
