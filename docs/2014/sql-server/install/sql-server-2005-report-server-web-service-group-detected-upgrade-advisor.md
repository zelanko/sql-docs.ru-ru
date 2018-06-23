---
title: Обнаружена группа веб-служб сервера отчетов SQL Server 2005 (Советник по переходу) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- deployment [Reporting Services]
ms.assetid: 699d24eb-7756-4b41-9294-ef1a94b2f267
caps.latest.revision: 15
author: markingmyname
ms.author: maghan
manager: jhubbard
ms.openlocfilehash: 7d3affeac1976b82ba269c4d86eac94cdc04335f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36195063"
---
# <a name="sql-server-2005-report-server-web-service-group-detected-upgrade-advisor"></a>Обнаружена группа веб-служб сервера отчетов SQL Server 2005 (советник по переходу)
  Советник по переходу обнаружил, что [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] экземпляра, связанного с [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] группы веб-сервера отчетов служб.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в основном режиме.|  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Описание  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] не используйте [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] группы веб-сервера отчетов служб. При обновлении с [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] эта группа служб удаляется, а пользовательские списки управления доступом (ACL) для этой группы или пользователи, входящие в группу, при обновлении не сохраняются.  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Перед обновлением выполните резервное копирование всех списков управления доступом или пользователей, относящихся к группе веб-служб сервера отчетов [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. Чтобы сделать это, можно использовать **Icacls.exe** средство командной строки в [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] SP2 и более поздних версиях или средство командной строки Cacls.exe в операционных системах Windows до версии [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] SP2. Дополнительные сведения о синтаксисе этих средств см. в документации по продукту Windows. После успешного завершения установки примените пользовательские списки управления доступом или пользователей к группе Windows сервера отчетов [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] для конкретного экземпляра сервера отчетов. [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Группы Windows сервера отчетов принимает форму SQLServerReportServerUser$\<*имя_компьютера*>$\<*имя_экземпляра*>.  
  
## <a name="see-also"></a>См. также  
 [Проблемы обновления служб Reporting Services &#40;помощник по обновлению&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  