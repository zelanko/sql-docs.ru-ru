---
title: Использование WQL и языков сценариев с поставщиком WMI для управления конфигурацией | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- queries [WMI]
- scripts [WMI]
- query language [WMI]
- WMI Query Language [WMI]
- WQL [WMI]
- WMI Provider for Configuration Management, WQL
- WMI Provider for Configuration Management, scripts
ms.assetid: c1e64905-3c2b-4974-88f4-abf17cf7e289
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: cc9994d4429e82f2bdd4f40797df1c5f628c6500
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68195825"
---
# <a name="using-wql-and-scripting-languages-with-the-wmi-provider-for-configuration-management"></a>Использование WQL и языков сценариев с поставщиком WMI для управления конфигурациями
  Управляющие приложения получают доступ к службам [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и сетевым настройкам, используя поставщик инструментария управления Windows (WMI) для объектов управления конфигурацией двумя способами.  
  
-   С помощью редактора WQL или средства создания запросов, например WBEMTest.exe, создается запрос к набору объектов на языке WQL (языке запросов к инструментарию управления Windows).  
  
-   С помощью языка для создания сценариев (например, VBScript).  
  
 Другой способ — управлять службами и сетевыми настройками [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] программным образом, используя управляемые объекты WMI в SMO. Дополнительные сведения о программировании управляемых WMI объектов см. в разделе [Управление службами и сетевыми параметрами с помощью поставщика WMI](../server-management-objects-smo/tasks/managing-services-and-network-settings-by-using-wmi-provider.md).  
  
 Доступ к поставщику WMI для управления конфигурацией можно получить с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] помощью Configuration Manager [!INCLUDE[msCoName](../../includes/msconame-md.md)] и консоли управления. Дополнительные сведения о доступе к поставщику WMI из пользовательского интерфейса см. [в разделах руководства по управлению службами &#40;диспетчер конфигурации SQL Server&#41;](../../database-engine/managing-services-how-to-topics-sql-server-configuration-manager.md).  
  
## <a name="see-also"></a>См. также:  
 [Доступ к поставщику WMI для управления конфигурацией с помощью WQL](access-wmi-provider-for-configuration-management-using-wql.md)   
 [изменить расширенные свойства службы SQL Server с помощью VBScript](access-wmi-provider-for-configuration-management-using-vbscript.md)  
  
  
