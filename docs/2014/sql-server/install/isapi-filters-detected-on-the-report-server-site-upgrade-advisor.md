---
title: На сайте сервера отчетов (Советник по переходу) обнаружены фильтры ISAPI | Документы Microsoft
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
- ISAPI filters
- report servers [Reporting Services], upgrade issues
ms.assetid: dd30560d-9e16-47c7-ba68-a9743a657e4e
caps.latest.revision: 12
author: markingmyname
ms.author: maghan
manager: jhubbard
ms.openlocfilehash: 18a9aab0737cb6d5127bbb3357d307c9c8f03aef
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36189171"
---
# <a name="isapi-filters-detected-on-the-report-server-site-upgrade-advisor"></a>На сайте сервера отчетов обнаружены фильтры ISAPI (советник по переходу)
  Помощник по обновлению обнаружил на веб-сайте, на котором размещен сервер отчетов и виртуальные каталоги диспетчера отчетов, один или несколько фильтров ISAPI. Фильтры ISAPI не поддерживаются в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] В машинном коде.|  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Описание  
 Перед обновлением проверьте, используются ли приложениями служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] фильтры ISAPI на сайте. Если фильтр ISAPI не требуется, сервер отчетов можно обновлять. Программа установки создаст URL-адреса по умолчанию без поддержки фильтров ISAPI, выполняющихся на сервере IIS. Если фильтр ISAPI необходим, не производите обновление, пока не найдете альтернативный способ размещения фильтра ISAPI (например, можно использовать сервер ISA или продолжить размещение фильтра ISA на сервере IIS). Сервер отчетов поддерживает использование HTTP-модулей ASP.NET в качестве замены для фильтров ISAPI в некоторых сценариях. Дополнительные сведения см. в документации Windows или в MSDN.  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Найдите и используйте отдельное решение для размещения фильтров ISAPI, необходимых для работы развертывания.  
  
## <a name="see-also"></a>См. также  
 [Проблемы обновления служб Reporting Services &#40;помощник по обновлению&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  