---
title: Клиентские сертификаты на веб-сайте сервера отчетов (советник по переходу) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- report servers [Reporting Services], upgrade issues
ms.assetid: 5ecce26b-99df-4109-8e51-d150d369dff7
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 5588930efbadf785e78aa115ad0021bce64bd7f7
ms.sourcegitcommit: ffe2fa1b22e6040cdbd8544fb5a3083eed3be852
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/04/2019
ms.locfileid: "71952601"
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
 [Советник по переходу Reporting Services проблем &#40;обновления&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
