---
title: Просмотр сведений о предупреждении | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, alerts
- viewing alerts
- alerts [SQL Server], viewing
- displaying alerts
- status information [SQL Server], alerts
ms.assetid: a0e3a8c4-e3c2-42a5-b2f8-aa06061d3fa6
author: stevestein
ms.author: sstein
ms.openlocfilehash: ee72512a507299e71f13fee689709a9403bb04e4
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85058654"
---
# <a name="view-information-about-an-alert"></a>Просмотр сведений о предупреждении
  В этом разделе описывается Просмотр сведений об [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] оповещениях агента в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)] .  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Безопасность](#Security)  
  
-   **Просмотр сведений о предупреждении**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 По умолчанию только члены предопределенной роли сервера **sysadmin** могут просматривать сведения о предупреждении. Другим пользователям должна быть предоставлена предопределенная роль базы данных **SQLAgentOperatorRole** в базе данных **msdb** .  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-view-information-about-an-alert"></a>Просмотр сведений о предупреждении  
  
1.  В **обозревателе объектов** щелкните знак «плюс», чтобы развернуть сервер, на котором необходимо просмотреть сведения о предупреждении.  
  
2.  Щелкните знак "плюс", чтобы развернуть **Агент SQL Server**.  
  
3.  Чтобы развернуть папку **Предупреждения** , щелкните значок "плюс".  
  
4.  Щелкните правой кнопкой мыши предупреждение, в котором содержатся сведения для просмотра, и выберите пункт **Свойства**.  
  
     Для получения дополнительных сведений о допустимых параметрах, содержащихся в диалоговом окне _Свойства предупреждения_**имя_предупреждения** , см. следующие разделы:  
  
    -   [Свойства предупреждения — новое оповещение &#40;общие&#41;страницы](../../integration-services/general-page-of-integration-services-designers-options.md)  
  
    -   [Свойства предупреждения — страница "создание ответа" &#40;"предупреждение"&#41;](alert-properties-new-alert-response-page.md)  
  
    -   [Свойства предупреждения: страница "новые параметры &#40;предупреждений"&#41;](alert-properties-new-alert-options-page.md)  
  
    -   [Свойства предупреждения (страница "Журнал")](alert-properties-history-page.md)  
  
5.  По окончании нажмите кнопку **ОК**.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-view-information-about-an-alert"></a>Просмотр сведений о предупреждении  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    -- reports information about the Demo: Sev. 25 Errors alert  
    -- This example assumes that the 'Demo: Sev. 25 Errors' alert exists.  
    USE msdb ;  
    GO  
  
    EXEC sp_help_alert @alert_name = 'Demo: Sev. 25 Errors'  
    GO  
    ```  
  
 Дополнительные сведения см. в разделе [sp_help_alert &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-alert-transact-sql).  
  
  
