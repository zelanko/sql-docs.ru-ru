---
title: "Настройка общих свойств управления на основе политик | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: performance-monitor
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.swb.dmf.PolicyManagement.f1
helpviewer_keywords: Policy-Based Management, configure properties
ms.assetid: 6d1e0e37-29ea-408a-a055-384984d884be
caps.latest.revision: "8"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f8e22ab529092938b72daeda4689b8366c2ea0c1
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="configure-the-general-properties-of-policy-based-management"></a>Настройка общих свойств управления на основе политик
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] В этом разделе описывается настройка свойств для управления на основе политик в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы выполните следующие действия.**  
  
     [Безопасность](#Security)  
  
-   **Для настройки управления на основе политик используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Security"></a> Безопасность  
  
####  <a name="Permissions"></a> Разрешения  
 Требуется членство в предопределенной роли базы данных PolicyAdministratorRole.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-configure-policy-based-management"></a>Настройка управления на основе политик  
  
1.  В **обозревателе объектов**щелкните знак "плюс", чтобы развернуть сервер, на котором необходимо настроить свойства управления на основе политик.  
  
2.  Щелкните знак «плюс», чтобы развернуть папку **Управление** .  
  
3.  Щелкните правой кнопкой мыши элемент **Управление политиками** и выберите пункт **Свойства**.  
  
     В диалоговом окне **Свойства управления политиками** доступны следующие параметры.  
  
     **Активировано**  
     Указывает, включено ли управление на основе политик.  
  
     **HistoryRetentionInDays**  
     Указывает число дней, в течение которых хранится журнал вычисления политик. Если это значение равно 0 (по умолчанию), то журнал автоматически не удаляется.  
  
     **LogOnSuccess**  
     Указывает, регистрирует ли управление на основе политик успешное вычисление политик.  
  
    -   Если это значение равно false (по умолчанию), то регистрируются только вычисления политик, завершившиеся ошибками.  
  
    -   Если это значение равно true, то регистрируются и успешные вычисления, и вычисления, завершившиеся ошибками.  
  
4.  После завершения нажмите кнопку **ОК**.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-configure-policy-based-management"></a>Настройка управления на основе политик  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    -- enables Policy-Based Management   
    USE msdb;  
    GO  
    EXEC dbo.sp_syspolicy_configure   
         @name = N'Enabled',   
         @value = 1;  
    GO  
    ```  
  
 Дополнительные сведения см. в разделе [sp_syspolicy_configure (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-syspolicy-configure-transact-sql.md).  
  
  
