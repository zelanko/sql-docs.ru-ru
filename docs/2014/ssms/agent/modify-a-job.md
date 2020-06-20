---
title: Изменение задания | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], modifying
- modifying jobs
- SQL Server Agent jobs, modifying
ms.assetid: dd5e5f20-20c4-4ab9-a19a-db87577dcd43
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0d25830ad119a1f5f344a4dcf318c35bee5f86ca
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85062185"
---
# <a name="modify-a-job"></a>Изменение задания
  В этом разделе описывается изменение свойств [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] заданий агента в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , [!INCLUDE[tsql](../../includes/tsql-md.md)] или управляющие объекты SQL Server.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [Безопасность](#Security)  
  
-   **Для изменения задания используется:**  
  
     [Среда SQL Server Management Studio](#SSMS)  
  
     [Transact-SQL](#TSQL)  
  
     [Управляющие объекты SQL Server](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Ограничения  
 Главное задание агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не может быть ориентировано как на локальный, так и на удаленный сервер.  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
 Если пользователь не является членом предопределенной роли сервера **sysadmin** , он может изменять только свои собственные задания. Дополнительные сведения см. в разделе [Обеспечение безопасности агента SQL Server](implement-sql-server-agent-security.md).  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-modify-a-job"></a>Изменение задания  
  
1.  В **обозревателе объектов** подключитесь к экземпляру [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] и разверните его.  
  
2.  Разверните узел **Агент SQL Server**, выберите раздел **Задания**, щелкните правой кнопкой мыши задание, которое нужно изменить, и выберите пункт **Свойства**.  
  
3.  В диалоговом окне **Свойства задания** обновите свойства, шаги, расписание, предупреждения и уведомления задания, воспользовавшись соответствующими страницами.  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> Использование Transact-SQL  
  
#### <a name="to-modify-a-job"></a>Изменение задания  
  
1.  В обозревателе объектов подключитесь к экземпляру компонента Database Engine и разверните его.  
  
2.  На панели инструментов нажмите кнопку **Создать запрос**.  
  
3.  В окне запроса используйте следующие системные хранимые процедуры для изменения задания.  
  
    -   Выполните [sp_update_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-job-transact-sql) , чтобы изменить атрибуты задания.  
  
    -   Выполните [sp_update_schedule &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-schedule-transact-sql) , чтобы изменить сведения о расписании для определения задания.  
  
    -   Выполните [sp_add_jobstep &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql) , чтобы добавить новые шаги задания.  
  
    -   Выполните [sp_update_jobstep &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-jobstep-transact-sql) , чтобы изменить уже существующие шаги задания.  
  
    -   Выполните [sp_delete_jobstep &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-jobstep-transact-sql) , чтобы удалить шаг задания из задания.  
  
    -   Дополнительные хранимые процедуры для изменения любого главного задания агента SQL Server.  
  
        -   Выполните [sp_delete_jobserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-jobserver-transact-sql) , чтобы удалить сервер, который в настоящее время связан с заданием.  
  
        -   Выполните [sp_add_jobserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql) , чтобы связать сервер с текущим заданием.  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a>Использование управляющие объекты SQL Server  
 **Изменение задания**  
  
 Воспользуйтесь классом `Job` в любом языке программирования (Visual Basic, Visual C# или PowerShell). Дополнительные сведения см. в статье [Управляющие объекты SQL Server (SMO)](https://msdn.microsoft.com/library/ms162169.aspx).  
  
  
