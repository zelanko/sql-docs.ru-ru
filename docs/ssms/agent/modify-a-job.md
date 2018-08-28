---
title: Изменение задания | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssms-agent
ms.reviewer: ''
ms.suite: sql
ms.technology: ssms
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], modifying
- modifying jobs
- SQL Server Agent jobs, modifying
ms.assetid: dd5e5f20-20c4-4ab9-a19a-db87577dcd43
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: d2396ae1bd90e6edb2e85ffb20fa759d4f81051b
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/14/2018
ms.locfileid: "42775752"
---
# <a name="modify-a-job"></a>Изменение задания
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Сейчас в [управляемом экземпляре базы данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия T-SQL между управляемым экземпляром базы данных SQL Azure и SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

В этом разделе описано, как изменять свойства заданий агента [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью среды [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)]или управляющих объектов SQL Server.  
  
**В этом разделе**  
  
-   **Перед началом работы**   
  
    [Ограничения](#Restrictions)  
  
    [безопасность](#Security)  
  
-   **Для изменения задания используется:**  
  
    [Среда SQL Server Management Studio](#SSMS)  
  
    [Transact-SQL](#TSQL)  
  
    [Управляющие объекты SQL Server](#SMO)  
  
## <a name="BeforeYouBegin"></a>Перед началом  
  
### <a name="Restrictions"></a>Ограничения  
Главное задание агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не может быть ориентировано как на локальный, так и на удаленный сервер.  
  
### <a name="Security"></a>безопасность  
Если пользователь не является членом предопределенной роли сервера **sysadmin** , он может изменять только свои собственные задания. Дополнительные сведения см. в разделе [Implement SQL Server Agent Security](../../ssms/agent/implement-sql-server-agent-security.md).  
  
## <a name="SSMS"></a>Использование среды SQL Server Management Studio  
  
#### <a name="to-modify-a-job"></a>Изменение задания  
  
1.  В **обозревателе объектов** подключитесь к экземпляру компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]и разверните его.  
  
2.  Разверните узел **Агент SQL Server**, выберите раздел **Задания**, щелкните правой кнопкой мыши задание, которое нужно изменить, и выберите пункт **Свойства**.  
  
3.  В диалоговом окне **Свойства задания** обновите свойства, шаги, расписание, предупреждения и уведомления задания, воспользовавшись соответствующими страницами.  
  
## <a name="TSQL"></a>Использование Transact-SQL  
  
#### <a name="to-modify-a-job"></a>Изменение задания  
  
1.  В обозревателе объектов подключитесь к экземпляру компонента Database Engine и разверните его.  
  
2.  На панели инструментов нажмите кнопку **Создать запрос**.  
  
3.  В окне запроса используйте следующие системные хранимые процедуры для изменения задания.  
  
    -   Выполните процедуру [sp_update_job (Transact-SQL)](http://msdn.microsoft.com/cbdfea38-9e42-47f3-8fc8-5978b82e2623) , чтобы изменить атрибуты задания.  
  
    -   Выполните процедуру [sp_update_schedule (Transact-SQL)](http://msdn.microsoft.com/97b3119b-e43e-447a-bbfb-0b5499e2fefe) , чтобы изменить сведения о планировании для определения задания.  
  
    -   Выполните процедуру [sp_add_jobstep (Transact-SQL)](http://msdn.microsoft.com/97900032-523d-49d6-9865-2734fba1c755) , чтобы добавить новые шаги к заданию.  
  
    -   Выполните процедуру [sp_update_jobstep (Transact-SQL)](http://msdn.microsoft.com/e158802c-c347-4a5d-bf75-c03e5ae56e6b) , чтобы изменить существующие шаги задания.  
  
    -   Выполните процедуру [sp_delete_jobstep (Transact-SQL)](http://msdn.microsoft.com/421ede8e-ad57-474a-9fb9-92f70a3e77e3) , чтобы удалить шаг задания.  
  
    -   Дополнительные хранимые процедуры для изменения любого главного задания агента SQL Server.  
  
        -   Выполните процедуру [sp_delete_jobserver (Transact-SQL)](http://msdn.microsoft.com/6d63ed32-68cf-4d8f-aa40-05a3826e05b8) , чтобы удалить сервер, сопоставленный с заданием.  
  
        -   Выполните процедуру [sp_add_jobserver (Transact-SQL)](http://msdn.microsoft.com/485252cc-0081-490a-9bd1-cbbd68eea286) , чтобы сопоставить сервер с текущим заданием.  
  
## <a name="SMO"></a>Использование управляющих объектов SQL Server  
**Изменение задания**  
  
Воспользуйтесь классом **Job** на любом языке программирования, таком как Visual Basic, Visual C# или PowerShell. Дополнительные сведения см. в статье [Управляющие объекты SQL Server (SMO)](http://msdn.microsoft.com/library/ms162169.aspx).  
  
