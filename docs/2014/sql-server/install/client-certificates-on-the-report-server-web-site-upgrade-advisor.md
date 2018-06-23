---
title: Сертификаты клиента на веб-сайт сервера отчетов (Советник по переходу) | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- report servers [Reporting Services], upgrade issues
ms.assetid: 5ecce26b-99df-4109-8e51-d150d369dff7
caps.latest.revision: 12
author: markingmyname
ms.author: maghan
manager: jhubbard
ms.openlocfilehash: 4d08cf58e6908aa8aba187e1e192a05b85b95c96
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36096994"
---
# <a name="client-certificates-on-the-report-server-web-site-upgrade-advisor"></a>Сертификаты клиента на веб-сайте сервера отчетов (советник по переходу)
  Помощник по обновлению обнаружил один или несколько клиентских сертификатов на сайте IIS, где расположены виртуальные каталоги сервера отчетов или диспетчера отчетов.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в основном режиме.|  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Описание  
 Службы [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] не поддерживают использование клиентских сертификатов для проверки подлинности пользователей. Обновление может быть продолжено, но обновленный сервер отчетов не будет использовать клиентские сертификаты.  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Если требуется проверка подлинности с помощью клиентских сертификатов, ее нужно реализовать в виде отдельного решения, например с помощью ISA Server.  
  
## <a name="see-also"></a>См. также  
 [Проблемы обновления служб Reporting Services &#40;помощник по обновлению&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  