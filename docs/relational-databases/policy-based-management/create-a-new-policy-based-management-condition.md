---
title: Создание условия управления на основе политик | Документация Майкрософт
ms.custom: ''
ms.date: 08/01/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, creating policy conditions
ms.assetid: 8a612f7e-6c70-49db-a4de-48431e097cc5
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 5f15fc35f7dc8bba16a786a5db86fc8c2f3da0f1
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47821322"
---
# <a name="create-a-new-policy-based-management-condition"></a>Создание нового условия управления на основе политик
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  В этом разделе описывается создание условия управления на основе политик в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Безопасность](#Security)  
  
-   **Для создания условия используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Требуется членство в роли PolicyAdministratorRole базы данных msdb.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-create-a-condition"></a>Создание условия  
  
1.  В **обозревателе объектов**щелкните знак "плюс", чтобы развернуть сервер, на котором необходимо создать условие управления на основе политик.  
  
2.  Щелкните знак «плюс», чтобы развернуть папку **Управление** .  
  
3.  Щелкните знак «плюс», чтобы развернуть папку **Управление политиками**.  
  
4.  Чтобы развернуть папку **Аспекты** , щелкните знак «плюс».  
  
5.  Щелкните правой кнопкой мыши аспект, в котором требуется создать новое условие, и выберите команду **Создать условие**.  
  
6.  В диалоговом окне **Создание нового условия** в поле **Имя** введите имя нового условия.  
  
7.  Подтвердите правильность аспекта в списке **Аспект** или выберите другой аспект.  
  
8.  Создайте выражения условия в разделе **Выражение**, выбрав свойство аспекта в окне **Поле** , связанный оператор и значение. При добавлении нескольких выражений их можно объединить с помощью операторов **And** или **Or**. Дополнительные сведения о доступных параметрах данного диалогового окна см. в разделах [Диалоговое окно "Создание нового условия" или "Открытие условия", страница "Общие"](../../relational-databases/policy-based-management/create-new-condition-or-open-condition-dialog-box-general-page.md), [Диалоговое окно "Создание нового условия" или "Открытие условия", страница "Описание"](../../relational-databases/policy-based-management/create-new-condition-or-open-condition-dialog-box-description-page.md) и [Диалоговое окно "Расширенное редактирование" (условие)](../../relational-databases/policy-based-management/advanced-edit-condition-dialog-box.md).  
  
9. После завершения нажмите кнопку **ОК**.  
  
  
