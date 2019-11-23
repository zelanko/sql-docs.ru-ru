---
title: Обнаружена группа веб-служб сервера отчетов SQL Server 2005 (советник по переходу) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- deployment [Reporting Services]
ms.assetid: 699d24eb-7756-4b41-9294-ef1a94b2f267
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: bfeff5eae569b481edfcc1cacc89c26e44edaece
ms.sourcegitcommit: ffe2fa1b22e6040cdbd8544fb5a3083eed3be852
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/04/2019
ms.locfileid: "71952375"
---
# <a name="sql-server-2005-report-server-web-service-group-detected-upgrade-advisor"></a>Обнаружена группа веб-служб сервера отчетов SQL Server 2005 (советник по переходу)
  Советник по переходу обнаружил, что [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] экземпляр связан с группой веб-служб сервера отчетов [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в основном режиме.|  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Описание  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] не использует группу веб-служб сервера отчетов [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. При обновлении с [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] эта группа служб удаляется, а пользовательские списки управления доступом (ACL) для этой группы или пользователи, входящие в группу, при обновлении не сохраняются.  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Перед обновлением выполните резервное копирование всех списков управления доступом или пользователей, относящихся к группе веб-служб сервера отчетов [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. Для этого можно использовать программу командной строки **icacls. exe** в [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] с пакетом обновления 2 (SP2) или более поздней версии или программу командной строки Cacls. exe в операционных системах Windows до [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] с пакетом обновления 2 (SP2). Дополнительные сведения о синтаксисе этих средств см. в документации по продукту Windows. После успешного завершения установки примените пользовательские списки управления доступом или пользователей к группе Windows сервера отчетов [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] для конкретного экземпляра сервера отчетов. Группа Windows сервера отчетов [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] имеет форму SQLServerReportServerUser $\<*computer_name* *>$\<instance_name >.*  
  
## <a name="see-also"></a>См. также статью  
 [Советник по переходу Reporting Services проблем &#40;обновления&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
