---
title: Просмотр или изменение свойств условия управления на основе политик | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Policy-Based Management, view policy conditions
- Policy-Based Management, modify policy conditions
ms.assetid: 890d7384-8444-4767-bb6f-f5debb155747
caps.latest.revision: 10
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 3d45f6a3a5fc4c5f139808778758d3d3c0cc1da7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36096136"
---
# <a name="view-or-modify-the-properties-of-a-policy-based-management-condition"></a>Просмотр или изменение свойств условия управления на основе политик
  В этом разделе описывается просмотр и изменение свойств условия управления на основе политик в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [безопасность](#Security)  
  
-   **Чтобы просмотреть или изменить свойства условия, с помощью:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Требуется членство в роли PolicyAdministratorRole базы данных msdb.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-view-or-modify-a-conditions-properties"></a>Просмотр или изменение свойств условия  
  
1.  В **обозревателе объектов**щелкните знак «плюс», чтобы развернуть сервер, содержащий условие, которое нужно просмотреть или изменить.  
  
2.  Щелкните знак «плюс», чтобы развернуть папку **Управление** .  
  
3.  Щелкните знак «плюс», чтобы развернуть папку **Управление политиками**.  
  
4.  Щелкните знак «плюс», чтобы развернуть папку **Условия** .  
  
5.  Щелкните правой кнопкой мыши условие, свойства которого необходимо просмотреть или изменить, и выберите пункт **Свойства**. Дополнительные сведения о параметрах, доступных в диалоговом окне **Открытие условия —***имя_условия*, см. в статьях [Диалоговое окно "Создание нового условия" или "Открытие условия", страница "Общее"](../../integration-services/general-page-of-integration-services-designers-options.md), [Диалоговое окно "Открытие условия", вкладка "Зависимые политики"](open-condition-dialog-box-dependent-policies-page.md), [Диалоговое окно "Создание нового условия" или "Открытие условия", страница "Описание"](create-new-condition-or-open-condition-dialog-box-description-page.md) и [Диалоговое окно "Расширенное редактирование" (условие)](advanced-edit-condition-dialog-box.md).  
  
6.  После завершения нажмите кнопку **ОК**.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-view-a-conditions-properties"></a>Просмотр свойств условия  
  
1.  В **обозревателе объектов** подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    USE msdb;  
    GO  
    SELECT name,  
       description,  
       facet,  
       expression,  
       is_name_condition,  
       obj_name  
    FROM syspolicy_conditions;  
    GO  
  
    ```  
  
 Дополнительные сведения см. в статье [syspolicy_conditions (Transact-SQL)](/sql/relational-databases/system-catalog-views/syspolicy-conditions-transact-sql).  
  
  
