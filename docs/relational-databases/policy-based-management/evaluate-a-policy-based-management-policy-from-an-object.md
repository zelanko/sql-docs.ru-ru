---
title: Вычисление политики управления на основе политик на основе объекта
description: Узнайте, как оценить политику на основе экземпляра SQL Server, базы данных или объекта базы данных с помощью SQL Server Management Studio (SSMS).
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, evaluate policy
ms.assetid: b9e9d646-4894-4dee-a02a-0c71a8dc020e
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: a6d57bbeca2d5393504192683bcf1738374fbc4c
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "75558301"
---
# <a name="evaluate-a-policy-based-management-policy-from-an-object"></a>Вычисление политики управления на основе политик на основе объекта
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  В этом разделе описывается, как вычислить политику на основе экземпляра сервера, базы данных или объекта базы данных в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [Безопасность](#Security)  
  
-   **Вычисление политики на основе объекта с помощью:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Ограничения  
  
-   Режим выполнения определяется как часть политики и не может быть изменен в диалоговом окне **Вычисление политик** .  
  
-   Диалоговое окно **Вычисление политик** показывает только политики, соответствующие объекту базы данных.  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Требуется членство в роли PolicyAdministratorRole базы данных msdb.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-evaluate-a-policy-from-an-object"></a>Вычисление политики на основе объекта  
  
1.  В обозревателе объектов щелкните правой кнопкой мыши экземпляр сервера, базу данных или объект базы данных, укажите **Политики**и выберите пункт **Вычислить**.  
  
2.  В диалоговом окне **Вычисление политик** выберите одну или несколько политик, затем нажмите кнопку **Вычислить** для запуска политики в режиме вычисления. Создает отчет о соответствии политике для набора целей, но не изменяет конфигурацию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и не обеспечивает соблюдение политики в дальнейшем. Для целевых объектов, не соответствующих выбранным политикам и имеющих свойства, которые можно перенастроить с помощью управления на основе политик, соответствие политике можно включить принудительно, нажав кнопку **Применить**. Дополнительные сведения о параметрах, доступных в диалоговом окне **Вычисление политик** , см. в разделах [Evaluate Policies Dialog Box, Policy Selection Page](../../relational-databases/policy-based-management/evaluate-policies-dialog-box-policy-selection-page.md), [Evaluate Policies Dialog Box, Evaluation Results Page](../../relational-databases/policy-based-management/evaluate-policies-dialog-box-evaluation-results-page.md)и [Results Detailed View Dialog Box](../../relational-databases/policy-based-management/results-detailed-view-dialog-box.md).  
  
3.  После завершения нажмите кнопку **Закрыть**.  
  
  
