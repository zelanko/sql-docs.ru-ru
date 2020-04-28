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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "71952375"
---
# <a name="sql-server-2005-report-server-web-service-group-detected-upgrade-advisor"></a>Обнаружена группа веб-служб сервера отчетов SQL Server 2005 (советник по переходу)
  Советник по переходу обнаружил [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , что экземпляр связан с [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] группой веб-служб сервера отчетов.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Собственный режим.|  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Описание  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] не использует группу веб [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] -служб сервера отчетов. При обновлении с [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] эта группа служб удаляется, а пользовательские списки управления доступом (ACL) для этой группы или пользователи, входящие в группу, при обновлении не сохраняются.  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Перед обновлением выполните резервное копирование всех списков управления доступом или пользователей, относящихся к группе веб-служб сервера отчетов [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. Для этого можно использовать программу командной строки **icacls. exe** в [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] SP2 и более поздних версиях или программу командной строки Cacls. exe в операционных системах Windows до версии [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] с пакетом обновления 2 (SP2). Дополнительные сведения о синтаксисе этих средств см. в документации по продукту Windows. После успешного завершения установки примените пользовательские списки управления доступом или пользователей к группе Windows сервера отчетов [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] для конкретного экземпляра сервера отчетов. Группа [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Windows сервера отчетов имеет форму SQLServerReportServerUser $\<*computer_name*>$\<*instance_name*>.  
  
## <a name="see-also"></a>См. также:  
 [Reporting Services проблем обновления &#40;советник по переходу&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
