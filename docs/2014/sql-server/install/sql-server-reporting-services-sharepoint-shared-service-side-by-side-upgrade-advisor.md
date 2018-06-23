---
title: Microsoft SQL Server SharePoint общей службы Reporting Services — установлены параллельно (Советник по переходу) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6ae1017e-129b-4702-9ea7-00ac9b024062
caps.latest.revision: 6
author: markingmyname
ms.author: maghan
manager: jhubbard
ms.openlocfilehash: 79f07ede92ee840ed50631c10d22bf4b015cf29b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36098124"
---
# <a name="microsoft-sql-server-reporting-services-sharepoint-shared-service-is-installed-side-by-side-upgrade-advisor"></a>Общая служба Microsoft SQL Server Reporting Services SharePoint установлена параллельно (советник по переходу)
  Помощник по обновлению обнаружил [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] общей службе SharePoint установлена параллельно с предыдущей версии [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Режиме интеграции с SharePoint.|  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Описание  
 Помощник по обновлению обнаружил [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint Общая служба устанавливается параллельно с предыдущей версией [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , не основанный на архитектура общей службы SharePoint. Поскольку на компьютере параллельно установлены старая и новая версии служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], связанных с технологиями SharePoint, обновление заблокировано.  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Чтобы продолжить обновление, необходимо удалить одну из существующих установок служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. После удаления одной из установок служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] повторно запустите помощник по обновлению, чтобы убедиться в отсутствии других проблем обновления.  
  
  