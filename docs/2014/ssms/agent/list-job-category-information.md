---
title: Просмотр сведений о категории задания | Документация Майкрософт
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 0fc668d4-6244-4fef-b90e-62d2c776cd7c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: dae8f1d98fb1758e9a9802883def1574bda68a78
ms.sourcegitcommit: f912c101d2939084c4ea2e9881eb98e1afa29dad
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2019
ms.locfileid: "72798208"
---
# <a name="list-job-category-information"></a>Просмотр сведений о категории задания
  Сведения о том, как составить список сведений о категории заданий в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)] или управляющие объекты SQL Server.  

  
##  <a name="Security"></a> безопасность  
 Дополнительные сведения см. в разделе [Обеспечение безопасности агента SQL Server](implement-sql-server-agent-security.md).  

  
##  <a name="TSQL"></a> Использование Transact-SQL  
  
#### <a name="to-list-job-category-information"></a>Просмотр сведений о категории задания  
  
1.  В **обозревателе объектов** подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```sql
    -- returns information about jobs that are administered locally  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_help_category  
        @type = N'LOCAL' ;  
    GO  
    ```  
  
 Дополнительные сведения см. в [разделе &#40;SP_HELP_CATEGORY Transact-&#41;SQL](/sql/relational-databases/system-stored-procedures/sp-help-category-transact-sql).  
  
  
##  <a name="SMO"></a>Использование управляющие объекты SQL Server  
 **Просмотр сведений о категории задания**  
  
 Воспользуйтесь классом `JobCategory` на любом языке программирования, таком как Visual Basic, Visual C# или PowerShell. Дополнительные сведения см. в [разделе &#40;управляющие объекты SQL Server&#41; Guide по программированию SMO](../../relational-databases/server-management-objects-smo/sql-server-management-objects-smo-programming-guide.md).  
