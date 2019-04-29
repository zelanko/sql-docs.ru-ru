---
title: Удаление файлов данных или журналов из базы данных | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- logs [SQL Server], files
- deleting files
- removing files
- removing data
- data deletions [SQL Server]
- file deletion [SQL Server]
- deleting data
ms.assetid: 0db4018c-ce2c-4ba1-bb29-1e4f3791c925
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e0f2de1f7003e61dbdc8e82f7a9b549fd42c77fc
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62917284"
---
# <a name="delete-data-or-log-files-from-a-database"></a>Удаление файлов данных или журнала из базы данных
  В данном разделе содержатся инструкции по удалению файлов данных или журналов в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] при помощи [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Prerequisites"></a> Предварительные требования  
  
-   Чтобы можно было удалить файл, он должен быть пустым. Дополнительные сведения см. в разделе [Сжатие файла](shrink-a-file.md).  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Необходимо разрешение ALTER на базу данных.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-delete-data-or-log-files-from-a-database"></a>Удаление файлов данных или журнала из базы данных  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] и разверните его.  
  
2.  Раскройте список **Базы данных**, щелкните правой кнопкой мыши базу данных, из которой удаляется файл, а затем выберите пункт **Свойства**.  
  
3.  Выберите страницу **Файлы** .  
  
4.  В списке **Файлы базы данных** выберите файл для удаления и нажмите кнопку **Удалить**.  
  
5.  Нажмите кнопку **ОК**.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-delete-data-or-log-files-from-a-database"></a>Удаление файлов данных или журнала из базы данных  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере удаляется файл `test1dat4`.  
  
 [!code-sql[DatabaseDDL#AlterDatabase4](../../snippets/tsql/SQL14/tsql/databaseddl/transact-sql/alterdatabase.sql#alterdatabase4)]  
  
 Дополнительные сведения см. в разделе [Параметры инструкции ALTER DATABASE для файлов и файловых групп (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options).  
  
## <a name="see-also"></a>См. также  
 [Сжатие базы данных](shrink-a-database.md)   
 [Добавление файлов данных или журналов в базу данных](add-data-or-log-files-to-a-database.md)  
  
  
