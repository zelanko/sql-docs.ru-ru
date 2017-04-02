---
title: "удалить точку управления служебной программой (SQL Server Utility) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c048a416-900e-4c77-8243-e0f0d8b94068
caps.latest.revision: 10
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 10
---
# удалить точку управления служебной программой (SQL Server Utility)
  В этом разделе описывается удаление точки управления служебной программой [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] из экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы выполните следующие действия.**  
  
     [Ограничения](#Restrictions)  
  
     [Безопасность](#Security)  
  
-   **Для удаления точки управления служебной программы используется:**  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
 До использования этой процедуры до удаления пункта управления программой из программы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] следует учесть следующие обстоятельства. При выполнении операции хранимая процедура выполнит проверку готовности к установке.  
  
-   До выполнения этой процедуры все управляемые экземпляры [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] необходимо удалить из точки управления служебной программой. Обратите внимание, что пункт управления программой является управляемым экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в разделе [Удаление экземпляра SQL Server из служебной программы SQL Server](../../relational-databases/manage/remove-an-instance-of-sql-server-from-the-sql-server-utility.md).  
  
-   Эта процедура должна запускаться на компьютере, являющемся точкой управления служебной программой.  
  
-   Если экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], где удален пункт управления служебной программой, содержал набор элементов сбора, не относящийся к служебной программе, эта процедура не удаляет базу данных UMDW (sysutility_mdw). В этом случае перед повторным созданием точки управления служебной программой необходимо вручную удалить базу данных UMDW (sysutility_mdw).  
  
###  <a name="Security"></a> Безопасность  
  
####  <a name="Permissions"></a> Разрешения  
 Эта процедура должна выполняться пользователем, имеющим разрешения **sysadmin** , необходимые для создания точки управления служебной программой.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### Удаление точки управления служебной программой  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
```  
EXEC msdb.dbo.sp_sysutility_ucp_remove;  
```  
  
## См. также:  
 [Функции и задачи служебной программы SQL Server](../../relational-databases/manage/sql-server-utility-features-and-tasks.md)   
 [Использование проводника служебных программ для управления служебной программой SQL Server](../../relational-databases/manage/use-utility-explorer-to-manage-the-sql-server-utility.md)   
 [Устранение неполадок служебной программы SQL Server](../Topic/Troubleshoot%20the%20SQL%20Server%20Utility.md)  
  
  