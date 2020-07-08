---
title: Настройка общих свойств управления на основе политик
description: Узнайте, как настроить свойства для управления на основе политик с помощью SQL Server Management Studio (SSMS) или Transact-SQL (T-SQL).
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql13.swb.dmf.PolicyManagement.f1
helpviewer_keywords:
- Policy-Based Management, configure properties
ms.assetid: 6d1e0e37-29ea-408a-a055-384984d884be
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 694094bd1290742ae0644c72d5d7620ebcfc0a44
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85654856"
---
# <a name="configure-the-general-properties-of-policy-based-management"></a>Настройка общих свойств управления на основе политик
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  В этом разделе описывается настройка свойств для управления на основе политик в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Безопасность](#Security)  
  
-   **Для настройки управления на основе политик используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Требуется членство в предопределенной роли базы данных PolicyAdministratorRole.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-configure-policy-based-management"></a>Настройка управления на основе политик  
  
1.  В **обозревателе объектов**щелкните знак "плюс", чтобы развернуть сервер, на котором необходимо настроить свойства управления на основе политик.  
  
2.  Щелкните знак «плюс», чтобы развернуть папку **Управление** .  
  
3.  Щелкните правой кнопкой мыши элемент **Управление политиками** и выберите пункт **Свойства**.  
  
     В диалоговом окне **Свойства управления политиками** доступны следующие параметры.  
  
     **Enabled**  
     Указывает, включено ли управление на основе политик.  
  
     **HistoryRetentionInDays**  
     Указывает число дней, в течение которых хранится журнал вычисления политик. Если это значение равно 0 (по умолчанию), то журнал автоматически не удаляется.  
  
     **LogOnSuccess**  
     Указывает, регистрирует ли управление на основе политик успешное вычисление политик.  
  
    -   Если это значение равно false (по умолчанию), то регистрируются только вычисления политик, завершившиеся ошибками.  
  
    -   Если это значение равно true, то регистрируются и успешные вычисления, и вычисления, завершившиеся ошибками.  
  
4.  После завершения нажмите кнопку **ОК**.  

##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
  
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
  
  
