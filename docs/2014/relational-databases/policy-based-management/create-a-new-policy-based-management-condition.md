---
title: Создание условия управления на основе политик | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, creating policy conditions
ms.assetid: 8a612f7e-6c70-49db-a4de-48431e097cc5
caps.latest.revision: 10
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: a91826b90b59ddf2c6d5da2a71ce25b2f3c896cd
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/06/2018
ms.locfileid: "43808550"
---
# <a name="create-a-new-policy-based-management-condition"></a>Создание нового условия управления на основе политик
  В этом разделе описывается создание условия управления на основе политик в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
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
  
8.  Создайте выражения условия в разделе **Выражение**, выбрав свойство аспекта в окне **Поле** , связанный оператор и значение. При добавлении нескольких выражений их можно объединить с помощью операторов **And** или **Or**. Дополнительные сведения о доступных параметрах данного диалогового окна см. в разделах [Диалоговое окно "Создание нового условия" или "Открытие условия", страница "Общие"](../../integration-services/general-page-of-integration-services-designers-options.md), [Диалоговое окно "Создание нового условия" или "Открытие условия", страница "Описание"](create-new-condition-or-open-condition-dialog-box-description-page.md) и [Диалоговое окно "Расширенное редактирование" (условие)](advanced-edit-condition-dialog-box.md).  
  
9. После завершения нажмите кнопку **ОК**.  
  
  
