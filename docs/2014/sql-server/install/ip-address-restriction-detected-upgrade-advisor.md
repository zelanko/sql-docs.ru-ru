---
title: Обнаружено ограничение IP-адресов (советник по переходу) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- report servers [Reporting Services], upgrade issues
ms.assetid: 9a154455-c68f-4403-a3a7-b90f4d35eecb
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 487ced9f103fd10a581841595111f01a5710bd15
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "71952081"
---
# <a name="ip-address-restriction-detected-upgrade-advisor"></a>Обнаружено ограничение по IP-адресу (советник по переходу)
  Помощник по обновлению обнаружил одно ограничение IP-адреса или более на веб-сайте IIS, на котором размещается сервер отчетов или виртуальные каталоги диспетчера отчетов. Службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] не поддерживают собственную реализацию ограничений IP-адреса.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Собственной.|  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Описание  
 Программа установки не может определить ограничений IP-адреса на URL-адреса, созданные для обновленного сервера отчетов. Обновление может быть продолжено, но ограничения IP-адреса не будут наложены на URL-адреса служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
## <a name="corrective-action"></a>Действие по исправлению  
 После обновления для разрешения или запрещения запросов к серверу отчетов с конкретных IP-адресов используйте сервер ISA, брандмауэр или другое решение.  
  
## <a name="see-also"></a>См. также:  
 [Reporting Services проблем обновления &#40;советник по переходу&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
