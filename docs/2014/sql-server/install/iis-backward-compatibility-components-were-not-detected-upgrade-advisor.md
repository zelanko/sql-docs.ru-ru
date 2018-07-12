---
title: Обратная совместимость служб IIS, компоненты не были обнаружены (Советник по переходу) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- IIS [Reporting Services]
ms.assetid: e794185a-0a77-480a-9aea-d09f8760a6b8
caps.latest.revision: 10
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 689ca199202b594376a4d0785992123f6016e384
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37177231"
---
# <a name="iis-backward-compatibility-components-were-not-detected-upgrade-advisor"></a>Не найдены компоненты обратной совместимости служб IIS (советник по переходу)
  Помощник по обновлению не обнаружил компонентов и настроек служб IIS, которые содержат информацию, используемую программой настройки для создания новых URL-адресов служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в основном режиме.|  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Описание  
 Службы IIS включают компоненты, которые предоставляют информацию о виртуальных каталогах сервера отчетов и диспетчера отчетов. Эти компоненты не установлены на компьютере, на котором размещен сервер отчетов. Обновление может быть продолжено, но URL-адреса сервера отчетов и диспетчера отчетов повторно созданы не будут.  
  
## <a name="corrective-action"></a>Действие по исправлению  
 После окончания обновления задайте URL-адреса сервера отчетов и диспетчера отчетов при помощи программы настройки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. В диспетчере служб IIS удалите виртуальные каталоги, в которых больше нет необходимости.  
  
 Дополнительные сведения см. в разделе [задан URL-адрес &#40;диспетчер конфигурации служб SSRS&#41; ](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md) в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.  
  
## <a name="see-also"></a>См. также  
 [Проблемы обновления служб Reporting Services &#40;помощник по обновлению&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
