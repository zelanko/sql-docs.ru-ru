---
title: На сайте сервера отчетов (Советник по переходу) обнаружены фильтры ISAPI | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- ISAPI filters
- report servers [Reporting Services], upgrade issues
ms.assetid: dd30560d-9e16-47c7-ba68-a9743a657e4e
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 7b30b585fc0448f04be2ee98c23f53794675fefe
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63301437"
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
  
  
