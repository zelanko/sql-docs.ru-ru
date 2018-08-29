---
title: Удаление одного или нескольких заданий | Документация Майкрософт
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
- SQL Server Agent jobs, deleting
- dropping jobs
- jobs [SQL Server Agent], deleting
- deleting jobs
- removing jobs
ms.assetid: 67dcdad0-57b2-431c-b77f-4ffc926af93d
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 9635ff38cd0e87993255e40f0cfe3f82bb717e47
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/14/2018
ms.locfileid: "42776002"
---
# <a name="delete-one-or-more-jobs"></a>Удаление одного или нескольких заданий
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Сейчас в [управляемом экземпляре базы данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия T-SQL между управляемым экземпляром базы данных SQL Azure и SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

В этом разделе описано, как удалить задания агента [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)]или управляющих объектов SQL Server.  
  
**В этом разделе**  
  
-   **Перед началом работы**  
  
    [безопасность](#Security)  
  
-   **Для удаления заданий используется:**  
  
    [Среда SQL Server Management Studio](#SSMS)  
  
    [Transact-SQL](#TSQL)  
  
    [Управляющие объекты SQL Server](#SMO)  
  
## <a name="BeforeYouBegin"></a>Перед началом  
  
### <a name="Security"></a>безопасность  
Пользователь, не являющийся членом предопределенной роли сервера **sysadmin** , может удалять только те задания, которыми владеет.  
  
## <a name="SSMS"></a>Использование среды SQL Server Management Studio  
  
#### <a name="to-delete-a-job"></a>Удаление задания  
  
1.  В **обозревателе объектов** подключитесь к экземпляру компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]и разверните его.  
  
2.  Разверните узел **Агент SQL Server**, выберите раздел **Задания**, щелкните правой кнопкой мыши задание, которое необходимо удалить, и выберите команду **Удалить**.  
  
3.  В диалоговом окне **Удаление объекта** убедитесь, что выбрано задание, которое следует удалить.  
  
4.  Нажмите кнопку **ОК**.  
  
#### <a name="to-delete-multiple-jobs"></a>Удаление нескольких заданий  
  
1.  В **обозревателе объектов** подключитесь к экземпляру компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]и разверните его.  
  
2.  Разверните узел **Агент SQL Server**.  
  
3.  Щелкните правой кнопкой мыши **Монитор активности заданий**и выберите команду **Просмотреть активность заданий**.  
  
4.  В мониторе активности заданий выберите задания для удаления, щелкните правой кнопкой мыши выделенные задания и выберите команду **Удалить задания**.  
  
## <a name="TSQL"></a>Использование Transact-SQL  
  
#### <a name="to-delete-a-job"></a>Удаление задания  
  
1.  В **обозревателе объектов** подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    USE msdb ;  
    GO  
  
    EXEC sp_delete_job  
        @job_name = N'NightlyBackups' ;  
    GO  
    ```  
  
Дополнительные сведения см. в разделе [sp_delete_job (Transact-SQL)](http://msdn.microsoft.com/b85db6e4-623c-41f1-9643-07e5ea38db09).  
  
## <a name="SMO"></a>Использование управляющих объектов SQL Server  
**Удаление нескольких заданий**  
  
Воспользуйтесь классом **JobCollection** на любом языке программирования, таком как Visual Basic, Visual C# или PowerShell. Дополнительные сведения см. в статье [Управляющие объекты SQL Server (SMO)](http://msdn.microsoft.com/library/ms162169.aspx).  
  
