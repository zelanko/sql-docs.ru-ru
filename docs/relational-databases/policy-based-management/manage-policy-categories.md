---
title: "Управление категориями политик | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.swb.dmf.policycategories.f1
ms.assetid: d188a819-731f-4029-98aa-780d3299a0ce
caps.latest.revision: "18"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1ec36fc06a5245ff1f4910016e3af2d60db7b4fc
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="manage-policy-categories"></a>Управление категориями политики
  В этом разделе описывается применение любой политики или всех доступных политик в категории ко всему экземпляру [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы выполните следующие действия.**  
  
     [Ограничения](#Restrictions)  
  
     [Безопасность](#Security)  
  
-   **Для применения политик категории к экземпляру SQL Server используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
  
-   Если при использовании [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]флажок **Обязательные подписки базы данных** не установлен, каждую категорию политики будет необходимо индивидуально применить к каждому участку сервера, например базам данных или таблицам.  
  
-   Если указать несуществующую категорию политики, то во время выполнения хранимой процедуры будет создана новая категория политики и подписка будет обязательной для всех баз данных. Если затем очистить обязательную подписку для новой категории, то подписка будет применяться только к базе данных, указанной в аргументе *target_object*. Дополнительные сведения об изменении параметра обязательной подписки см. в разделе [sp_syspolicy_update_policy_category (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-syspolicy-update-policy-category-transact-sql.md).  
  
###  <a name="Security"></a> Безопасность  
  
####  <a name="Permissions"></a> Разрешения  
 Эта хранимая процедура выполняется в контексте текущего владельца хранимой процедуры.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-apply-category-policies-to-a-sql-server-instance"></a>Применение политик категории к экземпляру SQL Server  
  
1.  В **обозревателе объектов**щелкните знак «плюс», чтобы развернуть сервер, к которому нужно применить политики категории.  
  
2.  Щелкните знак «плюс», чтобы развернуть папку **Управление** .  
  
3.  Щелкните правой кнопкой мыши элемент **Управление политиками** и выберите пункт **Управление категориями**.  
  
     В диалоговом окне **Управление категориями политики** доступны следующие данные.  
  
     **Название**  
     Имя категории политики.  
  
     **Обязательные подписки базы данных**  
     Заставляет все базы данных в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] применять политики из категории политики.  
  
4.  Установите или снимите флажки в разделе **Обязательные подписки базы данных** , чтобы применить ту или иную категорию политики к экземпляру SQL Server.  
  
5.  После завершения нажмите кнопку **ОК**.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-apply-category-policies-to-a-sql-server-instance"></a>Применение политик категории к экземпляру SQL Server  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    USE msdb;  
    GO  
    -- configures the specified database to subscribe to a policy category that is named 'Table Naming Policies'.  
    EXEC dbo.sp_syspolicy_add_policy_category_subscription @target_type = N'DATABASE'  
    , @target_object = N'AdventureWorks2012'  
    , @policy_category = N'Table Naming Policies';  
    GO  
    ```  
  
 Дополнительные сведения см. в разделе [sp_syspolicy_add_policy_category_subscription (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-syspolicy-add-policy-category-subscription-transact-sql.md).  
  
  
