---
title: Доступ к поставщику WMI с помощью WQL и сценариев
description: Узнайте, как получить доступ к службам SQL Server и сетевым параметрам с помощью поставщика WMI с помощью редактора WQL или средства запросов или языка сценариев.
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
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
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 52bc3bc300b1f6412ba2a4cdd3ce55ba5ca93aee
ms.sourcegitcommit: 783b35f6478006d654491cb52f6edf108acf2482
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/09/2020
ms.locfileid: "91891254"
---
# <a name="using-wql-and-scripting-languages-with-the-wmi-provider"></a>Использование WQL и языков сценариев с поставщиком WMI
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Управляющие приложения получают доступ к службам [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и сетевым настройкам, используя поставщик инструментария управления Windows (WMI) для объектов управления конфигурацией двумя способами.  
  
-   С помощью редактора WQL или средства создания запросов, например WBEMTest.exe, создается запрос к набору объектов на языке WQL (языке запросов к инструментарию управления Windows).  
  
-   С помощью языка для создания сценариев (например, VBScript).  
  
 Другой способ — управлять службами и сетевыми настройками [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] программным образом, используя управляемые объекты WMI в SMO. Дополнительные сведения о программировании управляемых WMI объектов см. в разделе [Управление службами и сетевыми параметрами с помощью поставщика WMI](../../relational-databases/server-management-objects-smo/tasks/managing-services-and-network-settings-by-using-wmi-provider.md).  
  
 Доступ к поставщику WMI для управления конфигурацией можно получить с помощью [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager и [!INCLUDE[msCoName](../../includes/msconame-md.md)] консоли управления. Дополнительные сведения о доступе к поставщику WMI из пользовательского интерфейса см. [в разделах руководства по управлению службами &#40;диспетчер конфигурации SQL Server&#41;](../../database-engine/configure-windows/scm-services-connect-to-another-computer.md).  
  
## <a name="see-also"></a>См. также:  
 [Доступ к поставщику WMI для управления конфигурацией с помощью WQL](../../relational-databases/wmi-provider-configuration/access-wmi-provider-for-configuration-management-using-wql.md)   
 [Доступ к поставщику WMI с помощью VBScript](../../relational-databases/wmi-provider-configuration/access-wmi-provider-for-configuration-management-using-vbscript.md)  
  
