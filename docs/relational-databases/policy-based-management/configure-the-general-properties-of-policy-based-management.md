---
title: Настройка общих свойств управления на основе политик | Документация Майкрософт
ms.custom: ''
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
ms.openlocfilehash: 7f7a0deba22f3799a3e4f4a293d9bb39322e2511
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68109724"
---
# <a name="configure-the-general-properties-of-policy-based-management"></a>Настройка общих свойств управления на основе политик
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  В этом разделе описывается настройка свойств для управления на основе политик в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [безопасность](#Security)  
  
-   **Для настройки управления на основе политик используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Требуется членство в предопределенной роли базы данных PolicyAdministratorRole.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
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

[!INCLUDE[freshInclude](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

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
  
  
