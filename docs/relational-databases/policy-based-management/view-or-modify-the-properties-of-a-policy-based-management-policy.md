---
title: Просмотр или изменение свойств политики управления на основе политик | Документация Майкрософт
ms.custom: ''
ms.date: 10/06/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, modify policies
- Policy-Based Management, view policies
ms.assetid: ba805504-5db5-4731-a8da-a0e89cb20c37
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: cf3bb62c4008b870c50c230a6140fff2a6b8b802
ms.sourcegitcommit: bfa10c54e871700de285d7f819095d51ef70d997
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/14/2019
ms.locfileid: "54254520"
---
# <a name="view-or-modify-the-properties-of-a-policy-based-management-policy"></a>Просмотр или изменение свойств политики управления на основе политик
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  В этом разделе описывается просмотр и изменение свойств политики управления на основе политик в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
  
####  <a name="Permissions"></a> Permissions  
 Требуется членство в роли PolicyAdministratorRole базы данных msdb.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-view-the-properties-of-all-policies-on-an-object"></a>Просмотр свойств всех политик в объекте  
  
1.  В обозревателе объектов щелкните правой кнопкой мыши сервер, базу данных или объект базы данных, укажите пункт **Политики** и выберите пункт **Просмотреть**. Дополнительные сведения о параметрах, доступных в диалоговом окне **Просмотр политик —**_имя_объекта_, см. в статье [Диалоговое окно "Просмотр политик"](../../relational-databases/policy-based-management/view-policies-dialog-box.md).  
  
2.  После завершения нажмите кнопку **Закрыть**.  
  
#### <a name="to-view-or-modify-a-specific-policys-properties"></a>Просмотр или изменение свойств отдельной политики  
  
1.  В **обозревателе объектов**щелкните знак "плюс", чтобы развернуть сервер, содержащий политику управления на основе политик, которую необходимо просмотреть или изменить.  
  
2.  Щелкните знак «плюс», чтобы развернуть папку **Управление** .  
  
3.  Щелкните знак «плюс», чтобы развернуть папку **Управление политиками**.  
  
4.  Щелкните знак «плюс», чтобы развернуть папку **Политики** .  
  
5.  Щелкните правой кнопкой политику, свойства которой необходимо просмотреть или изменить, и выберите пункт **Свойства**. Дополнительные сведения о параметрах, доступных в диалоговом окне **Открытие политики —**_имя_политики_, см. в статьях [Диалоговое окно "Создание новой политики" или "Открытие политики", страница "Общее"](../../relational-databases/policy-based-management/create-new-policy-or-open-policy-dialog-box-general-page.md) и [Диалоговое окно "Создание новой политики" или "Открытие политики", страница "Описание"](../../relational-databases/policy-based-management/create-new-policy-or-open-policy-dialog-box-description-page.md).  
  
6.  После завершения нажмите кнопку **ОК**.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-view-a-policys-properties"></a>Просмотр свойств политики  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    USE msdb;  
    GO  
    SELECT name,  
       execution_mode,  
       description,  
       is_enabled,  
       job_id  
    FROM syspolicy_policies;  
    GO  
    ```  
  
 Дополнительные сведения см. в статье [syspolicy_policies (Transact-SQL)](../../relational-databases/system-catalog-views/syspolicy-policies-transact-sql.md).  
  
  
