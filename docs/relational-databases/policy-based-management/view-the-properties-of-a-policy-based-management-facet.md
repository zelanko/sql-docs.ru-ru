---
title: Просмотр свойств аспекта управления на основе политик | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, view facet properties
ms.assetid: 022a244c-c2e7-4467-b9a2-c7a27859be22
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: e620f2a6fa6377b5a90770d94d53cd8983d3ec15
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47638032"
---
# <a name="view-the-properties-of-a-policy-based-management-facet"></a>Просмотр свойств аспекта управления на основе политик
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  В этом разделе описывается просмотр свойств аспекта управления на основе политик в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [безопасность](#Security)  
  
-   **Просмотр свойств аспекта с помощью:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Требуется членство в роли PolicyAdministratorRole базы данных msdb.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-view-the-properties-of-a-facet"></a>Просмотр свойств аспекта  
  
1.  В **обозревателе объектов**щелкните знак «плюс», чтобы развернуть сервер, содержащий аспект, который нужно просмотреть.  
  
2.  Щелкните знак «плюс», чтобы развернуть папку **Управление** .  
  
3.  Щелкните знак «плюс», чтобы развернуть папку **Управление политиками**.  
  
4.  Чтобы развернуть папку **Аспекты** , щелкните знак «плюс».  
  
5.  Щелкните правой кнопкой мыши аспект, свойства которого необходимо просмотреть, и выберите пункт **Свойства**. Дополнительные сведения о параметрах, доступных в диалоговом окне **Свойства аспекта —***имя_аспекта*, см. в статьях [Диалоговое окно "Свойства аспекта", вкладка "Общие"](../../relational-databases/policy-based-management/facet-properties-dialog-box-general-page.md), [Диалоговое окно "Свойства аспекта", вкладка "Зависимые политики"](../../relational-databases/policy-based-management/facet-properties-dialog-box-dependent-policies-page.md) и [Диалоговое окно "Свойства аспекта", вкладка "Зависимые условия"](../../relational-databases/policy-based-management/facet-properties-dialog-box-dependent-conditions-page.md).  
  
6.  После завершения нажмите кнопку **Закрыть**.  
  
  
