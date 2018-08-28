---
title: Изменение целевых серверов для задания | Документация Майкрософт
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
- modifying target servers
- SQL Server Agent jobs, target servers
- target servers [SQL Server], modifying
ms.assetid: 9dbe24f2-acec-4aa2-920c-e8e96efa18e4
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 6afb07f9ab495fdb3246b6ec9e89df70225095f0
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/14/2018
ms.locfileid: "42776129"
---
# <a name="modify-the-target-servers-for-a-job"></a>Modify the Target Servers for a Job
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Сейчас в [управляемом экземпляре базы данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия T-SQL между управляемым экземпляром базы данных SQL Azure и SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

В этом разделе описывается изменение целевых серверов для заданий агента [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
**В этом разделе**  
  
-   **Перед началом работы**  
  
    [безопасность](#Security)  
  
-   **Для изменения целевых серверов для задания используется:**  
  
    [Среда SQL Server Management Studio](#SSMSProcedure)  
  
    [Transact-SQL](#TsqlProcedure)  
  
## <a name="BeforeYouBegin"></a>Перед началом  
  
### <a name="Security"></a>безопасность  
  
#### <a name="Permissions"></a>Permissions  
По умолчанию данную хранимую процедуру могут выполнять члены предопределенной роли сервера sysadmin. Другим пользователям должна быть предоставлена одна из следующих предопределенных ролей базы данных агента SQL Server в базе данных msdb.  
  
1.  **SQLAgentUserRole**  
  
2.  **SQLAgentReaderRole**  
  
3.  SQLAgentOperatorRole  
  
## <a name="SSMSProcedure"></a>Использование среды SQL Server Management Studio  
  
#### <a name="to-modify-the-target-servers-for-a-job"></a>Изменение целевых серверов для задания  
  
1.  В **обозревателе объектов** подключитесь к экземпляру компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]и разверните его.  
  
2.  Разверните **Агент SQL Server**, **Задания**, затем щелкните правой кнопкой мыши задание и выберите пункт **Свойства**.  
  
3.  В диалоговом окне **Свойства задания** выберите страницу **Цели**, а затем выберите пункт **Выбрать локальный сервер в качестве целевого**или пункт **Выбрать несколько серверов в качестве целевых**.  
  
    При выборе пункта **Выбрать несколько серверов в качестве целевых**необходимо обозначить серверы, которые будут целевыми для задания, пометив флажки слева от имен соответствующих серверов. Убедитесь в том, что флажки серверов, которые не будут являться целевыми для задания, не помечены.  
  
## <a name="TsqlProcedure"></a>Использование Transact-SQL  
  
#### <a name="to-modify-the-target-servers-for-a-job"></a>Изменение целевых серверов для задания  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере многосерверное задание Weekly Sales Backups назначается серверу SEATTLE2.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_add_jobserver  
    @job_name = N'Weekly Sales Backups',   
    @server_name = N'SEATTLE2' ;   
GO  
```  
  
Дополнительные сведения см. в разделе [sp_add_jobserver (Transact-SQL)](http://msdn.microsoft.com/485252cc-0081-490a-9bd1-cbbd68eea286).  
  
## <a name="see-also"></a>См. также:  
[Автоматизация администрирования в масштабах предприятия](../../ssms/agent/automated-administration-across-an-enterprise.md)  
  
