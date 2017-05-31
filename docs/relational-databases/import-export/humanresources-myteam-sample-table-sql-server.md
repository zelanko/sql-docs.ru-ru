---
title: "Образец таблицы HumanResources.myTeam (SQL Server) | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-bulk-import-export
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- myTeam sample table [SQL Server]
- bulk importing [SQL Server], examples
- bulk exporting [SQL Server], examples
ms.assetid: 27da45a0-c1f4-4bf4-ab24-6196e80d3834
caps.latest.revision: 35
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: dd4e971fa001faeafd26468a80e9a95f18dc261e
ms.contentlocale: ru-ru
ms.lasthandoff: 04/11/2017

---
# <a name="humanresourcesmyteam-sample-table-sql-server"></a>Образец таблицы HumanResources.myTeam (SQL Server)
  Большинству примеров кода в разделе [Импорт и экспорт больших массивов данных](../../relational-databases/import-export/bulk-import-and-export-of-data-sql-server.md) требуется специальная учебная таблица **myTeam**. Перед выполнением примеров необходимо создать таблицу **myTeam** в схеме **HumanResources** базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] .  
  
> [!NOTE]  
>  [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] — один из образцов баз данных в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Таблица **myTeam** содержит следующие столбцы.  
  
|Столбец|Тип данных|Допускает значения NULL|Описание|  
|------------|---------------|-----------------|-----------------|  
|**EmployeeID**|**smallint**|Нет|Первичный ключ для строк таблицы. Идентификатор сотрудника — члена команды.|  
|**Название**|**nvarchar(50)**|Нет|Имя члена команды.|  
|**Title**|**nvarchar(50)**|Допускает значения NULL|Должность, которую сотрудник занимает в команде.|  
|**Историческая справка**|**nvarchar(50)**|Нет|Дата и время последнего обновления строки (по умолчанию)|  
  
 **Для создания таблицы HumanResources.myTeam**  
  
-   Используйте следующие инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] :  
  
    ```  
    --Create HumanResources.MyTeam:   
    USE AdventureWorks;  
    GO  
    CREATE TABLE HumanResources.myTeam   
    (EmployeeID smallint NOT NULL,  
    Name nvarchar(50) NOT NULL,  
    Title nvarchar(50) NULL,  
    Background nvarchar(50) NOT NULL DEFAULT ''  
    );  
    GO  
    ```  
  
 **Для заполнения таблицы HumanResources.myTeam**  
  
-   Чтобы вставить в таблицу две строки, выполните следующие инструкции `INSERT` .  
  
    ```  
    USE AdventureWorks;  
    GO  
    INSERT INTO HumanResources.myTeam(EmployeeID,Name,Title,Background)  
       VALUES(77,'Mia Doppleganger','Administrative Assistant','Microsoft Office');  
    GO  
    INSERT INTO HumanResources.myTeam(EmployeeID,Name,Title,Background)  
       VALUES(49,'Hirum Mollicat','I.T. Specialist','Report Writing and Data Mining');  
    GO  
    ```  
  
    > [!NOTE]  
    >  В этих инструкциях пропущен четвертый столбец таблицы `Background`. У него есть значение по умолчанию. Если не указывать этот столбец в инструкции `INSERT` , поле останется пустым.  
  
## <a name="see-also"></a>См. также:  
 [Массовый импорт и экспорт данных (SQL Server)](../../relational-databases/import-export/bulk-import-and-export-of-data-sql-server.md)  
  
  
