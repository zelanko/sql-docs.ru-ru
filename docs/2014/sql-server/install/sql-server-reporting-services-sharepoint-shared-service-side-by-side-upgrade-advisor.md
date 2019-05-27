---
title: Microsoft SQL Server Reporting Services общей службы SharePoint — установленные параллельно (Советник по переходу) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 6ae1017e-129b-4702-9ea7-00ac9b024062
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: cfa2eb99a475cb8f8bce8a0a1101edd767997aef
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66091858"
---
# <a name="microsoft-sql-server-reporting-services-sharepoint-shared-service-is-installed-side-by-side-upgrade-advisor"></a>Общая служба Microsoft SQL Server Reporting Services SharePoint установлена параллельно (советник по переходу)
  Помощник по обновлению обнаружил [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] общей службой SharePoint установлена параллельно с предыдущей версии [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Режиме интеграции с SharePoint.|  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Описание  
 Помощник по обновлению обнаружил [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint Общая служба устанавливается параллельно с предыдущей версии [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] не, основанный на архитектуре общих служб SharePoint. Поскольку на компьютере параллельно установлены старая и новая версии служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], связанных с технологиями SharePoint, обновление заблокировано.  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Чтобы продолжить обновление, необходимо удалить одну из существующих установок служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. После удаления одной из установок служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] повторно запустите помощник по обновлению, чтобы убедиться в отсутствии других проблем обновления.  
  
  
