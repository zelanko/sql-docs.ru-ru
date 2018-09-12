---
title: Синхронизация часов на целевых серверах (SQL Server Management Studio) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, target servers
- clocks [SQL Server]
- master servers [SQL Server], clock synchronization
- synchronization [SQL Server], target server clocks
- target servers [SQL Server], clock synchronization
ms.assetid: 4fb80502-d271-4d06-bcbc-bfbbceb5f2a2
caps.latest.revision: 23
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 35b86d27387aae047eddaef4cdae46efe4116c66
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/06/2018
ms.locfileid: "43810190"
---
# <a name="synchronize-target-server-clocks-sql-server-management-studio"></a>Синхронизация часов на целевых серверах (SQL Server Management Studio)
  В этом разделе описано, как в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] синхронизировать часы на целевом сервере с часами на главном сервере с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]. Синхронизация этих системных часов обслуживает расписания заданий.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [безопасность](#Security)  
  
-   **Синхронизация часов целевого сервера с помощью:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Необходимо членство в предопределенной роли сервера **sysadmin** .  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-synchronize-target-server-clocks"></a>Синхронизация часов целевых серверов  
  
1.  В **обозревателе объектов** щелкните значок «плюс», чтобы развернуть сервер, где необходимо синхронизировать часы целевого сервера с часами главного сервера.  
  
2.  Щелкните правой кнопкой мыши элемент **Агент SQL Server**, укажите пункт **Администрирование нескольких серверов**, а затем выберите пункт **Управление целевыми серверами**.  
  
3.  В диалоговом окне **Управление целевыми серверами** нажмите кнопку **Отправить инструкции**.  
  
4.  В списке **Тип инструкции** выберите **Синхронизировать часы**.  
  
5.  В пункте **Адресаты**выполните одно из следующих действий:  
  
    -   Установите флажок **Все целевые серверы** , чтобы синхронизировать часы всех целевых серверов с часами главного сервера.  
  
    -   Установите флажок **Эти целевые серверы** , чтобы синхронизировать часы определенных серверов, затем выберите целевые серверы, часы которых необходимо синхронизировать с часами главного сервера.  
  
6.  После завершения нажмите кнопку **ОК**.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-synchronize-target-server-clocks"></a>Синхронизация часов целевых серверов  
  
1.  В **обозревателе объектов** подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
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
  
 Дополнительные сведения см. в разделе [sp_resync_targetserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-resync-targetserver-transact-sql).  
  
  
