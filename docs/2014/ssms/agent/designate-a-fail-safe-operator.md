---
title: Назначение резервного оператора | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, operators
- fail-safe operator [SQL Server]
- jobs [SQL Server Agent], operators
- notifications [SQL Server], job status
ms.assetid: 0f4eb513-5c0a-4523-974e-e85c1deeb57f
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 54ec71df8efab1f60bfb7a5b9af448705e349d28
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "68211426"
---
# <a name="designate-a-fail-safe-operator"></a>Назначение резервного оператора
  Резервный оператор — это пользователь, который получает предупреждение, если нужный оператор недоступен. В этом разделе описывается, как настроить резервный оператор для получения [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] уведомлений об оповещениях агента [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] в с [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]помощью.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [Безопасность](#Security)  
  
-   **Назначение резервного оператора с помощью:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Ограничения  
  
-   Параметры пейджера и **команды net send** будут удалены из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] агента в следующей версии [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Старайтесь не использовать эти функции в новых разработках и предусмотрите соответствующие изменения в приложениях, которые используют их в настоящее время.  
  
-   Обратите внимание, что для использования компонента Database Mail для отправки операторам уведомлений по электронной почте и на пейджер агент SQL Server необходимо настроить для использования компонента Database Mail. Дополнительные сведения см. в разделе [Назначить предупреждения для оператора](assign-alerts-to-an-operator.md).  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] обеспечивает доступный графический способ управления заданиями и рекомендуется для создания и управления инфраструктурой заданий.  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Только члены предопределенной роли сервера **sysadmin** могут назначать резервных операторов.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-designate-a-fail-safe-operator"></a>Назначение резервного оператора  
  
1.  В **обозревателе объектов** щелкните знак "плюс", чтобы развернуть сервер, который содержит оператора агента SQL Server, назначаемого в качестве резервного.  
  
2.  Щелкните правой кнопкой мыши **Агент SQL Server** и выберите пункт **свойства**.  

3.  В диалоговом окне **свойства агент SQL Server —**_server_name_ в разделе **Выбор страницы**выберите **система предупреждений**.  
 
4.  В разделе **Резервный оператор**выберите **Включить резервный оператор**.  
  
5.  В списке **Оператор** выберите оператор, который необходимо сделать резервным.  
  
6.  Установите некоторые или все указанные флажки для выбора способа уведомления оператора: **Электронная почта**, **Пейджер**или **Net send**.  
  
7.  По окончании нажмите кнопку **ОК**.  
  
  
