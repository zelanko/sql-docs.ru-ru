---
title: Виртуальные каталоги не указаны (советник по переходу) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- virtual directories [Reporting Services]
ms.assetid: 7d32b560-49d6-4558-b5d6-9127067f82d6
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 79ab9c0d18f20bcfd6f549918cc1501a1d8e1e49
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85065108"
---
# <a name="virtual-directories-are-unspecified-upgrade-advisor"></a>Виртуальные каталоги не указаны (советник по переходу)
  Помощник по обновлению не обнаружил настроек виртуального каталога для веб-службы сервера отчетов или диспетчера отчетов. После завершения обновления необходимо настроить резервирования URL-адресов для сервера отчетов с помощью диспетчера конфигурации служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Собственный режим.|  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Описание  
 При обновлении установки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] резервируются новые URL-адреса для веб-службы сервера отчетов и диспетчера отчетов. Помощник по обновлению не нашел в настройках обновляемого экземпляра виртуальные каталоги для веб-службы сервера отчетов или диспетчера отчетов. У помощника по обновлению недостаточно информации, чтобы зарезервировать URL-адреса для обновленного сервера отчетов. Процесс обновления может быть продолжен, но виртуальные каталоги для сервера отчетов и диспетчера отчетов после новой установки не будут определены.  
  
## <a name="corrective-action"></a>Действие по исправлению  
 После окончания обновления задайте URL-адреса сервера отчетов и диспетчера отчетов при помощи диспетчера конфигурации служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. В диспетчере служб IIS удалите все виртуальные каталоги, в которых больше нет необходимости.  
  
 Дополнительные сведения см. в разделе [Настройка URL-адреса &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md) [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] электронной документации по.  
  
## <a name="see-also"></a>См. также:  
 [Reporting Services проблем обновления &#40;советник по переходу&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
