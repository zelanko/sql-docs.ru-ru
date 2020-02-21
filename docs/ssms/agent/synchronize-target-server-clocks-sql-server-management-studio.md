---
title: Синхронизация часов целевых серверов
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, target servers
- clocks [SQL Server]
- master servers [SQL Server], clock synchronization
- synchronization [SQL Server], target server clocks
- target servers [SQL Server], clock synchronization
ms.assetid: 4fb80502-d271-4d06-bcbc-bfbbceb5f2a2
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 01/19/2017
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 7fa715d0df6c94630564ede8a162a940542d7510
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "75257900"
---
# <a name="synchronize-target-server-clocks"></a>Синхронизация часов целевых серверов

[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Сейчас в [управляемом экземпляре базы данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия T-SQL между управляемым экземпляром базы данных SQL Azure и SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

В этом разделе описано, как в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] синхронизировать часы на целевом сервере с часами на главном сервере с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]. Синхронизация этих системных часов обслуживает расписания заданий.  

## <a name="BeforeYouBegin"></a>Перед началом  
  
### <a name="Security"></a>безопасность  
  
#### <a name="Permissions"></a>Permissions  
Необходимо членство в предопределенной роли сервера **sysadmin** .  
  
## <a name="SSMSProcedure"></a>Использование среды SQL Server Management Studio  
  
#### <a name="to-synchronize-target-server-clocks"></a>Синхронизация часов целевых серверов  
  
1.  В **обозревателе объектов** щелкните значок «плюс», чтобы развернуть сервер, где необходимо синхронизировать часы целевого сервера с часами главного сервера.  
  
2.  Щелкните правой кнопкой мыши элемент **Агент SQL Server**, укажите пункт **Администрирование нескольких серверов**, а затем выберите пункт **Управление целевыми серверами**.  
  
3.  В диалоговом окне **Управление целевыми серверами** нажмите кнопку **Отправить инструкции**.  
  
4.  В списке **Тип инструкции** выберите **Синхронизировать часы**.  
  
5.  В пункте **Адресаты**выполните одно из следующих действий:  
  
    -   Установите флажок **Все целевые серверы** , чтобы синхронизировать часы всех целевых серверов с часами главного сервера.  
  
    -   Установите флажок **Эти целевые серверы** , чтобы синхронизировать часы определенных серверов, затем выберите целевые серверы, часы которых необходимо синхронизировать с часами главного сервера.  
  
6.  После завершения нажмите кнопку **ОК**.  
  
## <a name="TsqlProcedure"></a>Использование Transact-SQL  
  
#### <a name="to-synchronize-target-server-clocks"></a>Синхронизация часов целевых серверов  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    USE msdb ;  
    GO  
    -- resynchronizes the SEATTLE1 target server  
    EXEC dbo.sp_resync_targetserver  
        N'SEATTLE1' ;  
    GO  
    ```  
  
Дополнительные сведения см. в разделе [sp_resync_targetserver (Transact-SQL)](https://msdn.microsoft.com/40e44df7-d3e3-44ee-b149-08aba629a21f).  
  
