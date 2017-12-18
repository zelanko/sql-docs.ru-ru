---
title: "Вычисление политики управления на основе политик в контексте объекта | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: performance-monitor
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Policy-Based Management, evaluate policy
ms.assetid: b9e9d646-4894-4dee-a02a-0c71a8dc020e
caps.latest.revision: "8"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ca375a36ec9bf94be1daba1217bba47e88b90e4e
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="evaluate-a-policy-based-management-policy-from-an-object"></a>Вычисление политики управления на основе политик на основе объекта
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] В этом разделе описывается, как вычислить политику на основе экземпляра сервера, базы данных или объекта базы данных в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы выполните следующие действия.**  
  
     [Ограничения](#Restrictions)  
  
     [Безопасность](#Security)  
  
-   **Вычисление политики на основе объекта с помощью:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
  
-   Режим выполнения определяется как часть политики и не может быть изменен в диалоговом окне **Вычисление политик** .  
  
-   Диалоговое окно **Вычисление политик** показывает только политики, соответствующие объекту базы данных.  
  
###  <a name="Security"></a> Безопасность  
  
####  <a name="Permissions"></a> Разрешения  
 Требуется членство в роли PolicyAdministratorRole базы данных msdb.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-evaluate-a-policy-from-an-object"></a>Вычисление политики на основе объекта  
  
1.  В обозревателе объектов щелкните правой кнопкой мыши экземпляр сервера, базу данных или объект базы данных, укажите **Политики**и выберите пункт **Вычислить**.  
  
2.  В диалоговом окне **Вычисление политик** выберите одну или несколько политик, затем нажмите кнопку **Вычислить** для запуска политики в режиме вычисления. Создает отчет о соответствии политике для набора целей, но не изменяет конфигурацию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и не обеспечивает соблюдение политики в дальнейшем. Для целевых объектов, не соответствующих выбранным политикам и имеющих свойства, которые можно перенастроить с помощью управления на основе политик, соответствие политике можно включить принудительно, нажав кнопку **Применить**. Дополнительные сведения о параметрах, доступных в диалоговом окне **Вычисление политик** , см. в разделах [Evaluate Policies Dialog Box, Policy Selection Page](../../relational-databases/policy-based-management/evaluate-policies-dialog-box-policy-selection-page.md), [Evaluate Policies Dialog Box, Evaluation Results Page](../../relational-databases/policy-based-management/evaluate-policies-dialog-box-evaluation-results-page.md)и [Results Detailed View Dialog Box](../../relational-databases/policy-based-management/results-detailed-view-dialog-box.md).  
  
3.  После завершения нажмите кнопку **Закрыть**.  
  
  
