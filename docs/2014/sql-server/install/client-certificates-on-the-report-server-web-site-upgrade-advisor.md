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
ms.openlocfilehash: 563a64e695ef552a712a5678f56d38fdfbff619f
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85059356"
---
# <a name="client-certificates-on-the-report-server-web-site-upgrade-advisor"></a>Сертификаты клиента на веб-сайте сервера отчетов (советник по переходу)
  Помощник по обновлению обнаружил один или несколько клиентских сертификатов на сайте IIS, где расположены виртуальные каталоги сервера отчетов или диспетчера отчетов.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Собственный режим.|  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Описание  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]не [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] поддерживает использование сертификатов клиента для проверки подлинности пользователей. Обновление может быть продолжено, но обновленный сервер отчетов не будет использовать клиентские сертификаты.  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Если требуется проверка подлинности с помощью клиентских сертификатов, ее нужно реализовать в виде отдельного решения, например с помощью ISA Server.  
  
## <a name="see-also"></a>См. также:  
 [Reporting Services проблем обновления &#40;советник по переходу&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
