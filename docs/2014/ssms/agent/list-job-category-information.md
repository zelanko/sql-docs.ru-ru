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
ms.openlocfilehash: ac903ecb951e98e29dcd6521f8c9623f8cc62768
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2018
ms.locfileid: "52754256"
---
# <a name="list-job-category-information"></a>Просмотр сведений о категории задания
  Как получить список сведений о категории задания в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)] или управляющих объектов SQL Server.  

  
##  <a name="Security"></a> безопасность  
 Дополнительные сведения см. в разделе [Обеспечение безопасности агента SQL Server](implement-sql-server-agent-security.md).  

  
##  <a name="TSQL"></a> Использование Transact-SQL  
  
#### <a name="to-list-job-category-information"></a>Просмотр сведений о категории задания  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    -- returns information about jobs that are administered locally  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_help_category  
        @type = N'LOCAL' ;  
    GO  
    ```  
  
 Дополнительные сведения см. в разделе [sp_help_category &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-category-transact-sql).  
  
  
##  <a name="SMO"></a> Использование управляющих объектов SQL Server  
 **Просмотр сведений о категории задания**  
  
 Воспользуйтесь классом `JobCategory` на любом языке программирования, таком как Visual Basic, Visual C# или PowerShell. Дополнительные сведения см. в разделе [управляющих объектов SQL Server &#40;SMO&#41; руководство по программированию](../../relational-databases/server-management-objects-smo/sql-server-management-objects-smo-programming-guide.md).  
  
  
  
