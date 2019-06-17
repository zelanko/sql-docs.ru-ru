---
title: Образец таблицы HumanResources.myTeam (SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- myTeam sample table [SQL Server]
- bulk importing [SQL Server], examples
- bulk exporting [SQL Server], examples
ms.assetid: 27da45a0-c1f4-4bf4-ab24-6196e80d3834
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b038c1132cf8c1ccd31da2a5a1e2a600f2505624
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66011958"
---
# <a name="humanresourcesmyteam-sample-table-sql-server"></a>Образец таблицы HumanResources.myTeam (SQL Server)
  Большинству примеров кода в разделе [Импорт и экспорт больших массивов данных](bulk-import-and-export-of-data-sql-server.md) требуется специальная учебная таблица **myTeam**. Перед выполнением примеров необходимо создать таблицу **myTeam** в схеме **HumanResources** базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] .  
  
> [!NOTE]  
>  [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] — один из образцов баз данных в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Таблица **myTeam** содержит следующие столбцы.  
  
|Столбец|Тип данных|Допускает значения NULL|Описание|  
|------------|---------------|-----------------|-----------------|  
|**EmployeeID**|`smallint`|Нет|Первичный ключ для строк таблицы. Идентификатор сотрудника — члена команды.|  
|**Name**|`nvarchar(50)`|Нет|Имя члена команды.|  
|**Title**|`nvarchar(50)`|Допускает значения NULL|Должность, которую сотрудник занимает в команде.|  
|**Историческая справка**|`nvarchar(50)`|Нет|Дата и время последнего обновления строки (по умолчанию)|  
  
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
  
## <a name="see-also"></a>См. также  
 [Массовый импорт и экспорт данных (SQL Server)](bulk-import-and-export-of-data-sql-server.md)  
  
  
