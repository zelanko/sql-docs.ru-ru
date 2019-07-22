---
title: Удаление файлов данных или журналов из базы данных | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
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
ms.openlocfilehash: be0f5865965ab419d1807783196e18a4e873c6a0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68073762"
---
# <a name="delete-data-or-log-files-from-a-database"></a>Удаление файлов данных или журнала из базы данных
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  В данном разделе содержатся инструкции по удалению файлов данных или журналов в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] при помощи [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы выполните следующие действия.**  
  
     [Предварительные требования](#Prerequisites)  
  
     [безопасность](#Security)  
  
-   **Удаление файлов данных или журналов из базы данных с помощью следующих средств:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Prerequisites"></a> Предварительные требования  
  
-   Чтобы можно было удалить файл, он должен быть пустым. Дополнительные сведения см. в разделе [Сжатие файла](../../relational-databases/databases/shrink-a-file.md).  
  
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

[!INCLUDE[freshInclude](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-delete-data-or-log-files-from-a-database"></a>Удаление файлов данных или журнала из базы данных  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере удаляется файл `test1dat4`.  
  
 [!code-sql[DatabaseDDL#AlterDatabase4](../../relational-databases/databases/codesnippet/tsql/delete-data-or-log-files_1.sql)]  
  
 Дополнительные сведения см. в разделе [Параметры инструкции ALTER DATABASE для файлов и файловых групп (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql-file-and-filegroup-options.md).  
  
## <a name="see-also"></a>См. также:  
 [Сжатие базы данных](../../relational-databases/databases/shrink-a-database.md)   
 [Добавление файлов данных или журналов в базу данных](../../relational-databases/databases/add-data-or-log-files-to-a-database.md)  
  
  
