---
title: Просмотр свойств аспекта управления на основе политик | Документация Майкрософт
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
- Policy-Based Management, view facet properties
ms.assetid: 022a244c-c2e7-4467-b9a2-c7a27859be22
caps.latest.revision: 7
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 1f4ecdd5b25cf790bb81f4cbabd024870c6a670e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36086672"
---
# <a name="view-the-properties-of-a-policy-based-management-facet"></a>Просмотр свойств аспекта управления на основе политик
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
  
5.  Щелкните правой кнопкой мыши аспект, свойства которого необходимо просмотреть, и выберите пункт **Свойства**. Дополнительные сведения о параметрах, доступных в диалоговом окне **Свойства аспекта —***имя_аспекта*, см. в статьях [Диалоговое окно "Свойства аспекта", вкладка "Общие"](../../integration-services/general-page-of-integration-services-designers-options.md), [Диалоговое окно "Свойства аспекта", вкладка "Зависимые политики"](facet-properties-dialog-box-dependent-policies-page.md) и [Диалоговое окно "Свойства аспекта", вкладка "Зависимые условия"](facet-properties-dialog-box-dependent-conditions-page.md).  
  
6.  После завершения нажмите кнопку **Закрыть**.  
  
  