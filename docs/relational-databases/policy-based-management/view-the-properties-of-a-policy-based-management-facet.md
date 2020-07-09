---
title: Просмотр свойств аспекта управления на основе политик
description: Узнайте, как просматривать свойства аспекта управления на основе политик в SQL Server с помощью SQL Server Management Studio (SSMS).
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, view facet properties
ms.assetid: 022a244c-c2e7-4467-b9a2-c7a27859be22
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: d2aa58294e23f32ebfc1a43d300ab54cd6622aa4
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85774070"
---
# <a name="view-the-properties-of-a-policy-based-management-facet"></a>Просмотр свойств аспекта управления на основе политик
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  В этом разделе описывается просмотр свойств аспекта управления на основе политик в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Безопасность](#Security)  
  
-   **Просмотр свойств аспекта с помощью:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Требуется членство в роли PolicyAdministratorRole базы данных msdb.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-view-the-properties-of-a-facet"></a>Просмотр свойств аспекта  
  
1.  В **обозревателе объектов**щелкните знак «плюс», чтобы развернуть сервер, содержащий аспект, который нужно просмотреть.  
  
2.  Щелкните знак «плюс», чтобы развернуть папку **Управление** .  
  
3.  Щелкните знак «плюс», чтобы развернуть папку **Управление политиками**.  
  
4.  Чтобы развернуть папку **Аспекты** , щелкните знак «плюс».  
  
5.  Щелкните правой кнопкой мыши аспект, свойства которого необходимо просмотреть, и выберите пункт **Свойства**. Дополнительные сведения о параметрах, доступных в диалоговом окне **Свойства аспекта —** _имя_аспекта_, см. в статьях [Диалоговое окно "Свойства аспекта", вкладка "Общие"](../../relational-databases/policy-based-management/facet-properties-dialog-box-general-page.md), [Диалоговое окно "Свойства аспекта", вкладка "Зависимые политики"](../../relational-databases/policy-based-management/facet-properties-dialog-box-dependent-policies-page.md) и [Диалоговое окно "Свойства аспекта", вкладка "Зависимые условия"](../../relational-databases/policy-based-management/facet-properties-dialog-box-dependent-conditions-page.md).  
  
6.  После завершения нажмите кнопку **Закрыть**.  

