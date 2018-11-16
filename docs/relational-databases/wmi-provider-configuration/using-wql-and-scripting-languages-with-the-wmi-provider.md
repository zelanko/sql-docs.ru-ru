---
title: Использование WQL и языков сценариев с поставщиком WMI | Документация Майкрософт
ms.custom: ''
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
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 01758e9dadcb0090a7bd55ec99375ce122633859
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/15/2018
ms.locfileid: "51676153"
---
# <a name="using-wql-and-scripting-languages-with-the-wmi-provider"></a>Использование WQL и языков сценариев с поставщиком WMI
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Управляющие приложения получают доступ к службам [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и сетевым настройкам, используя поставщик инструментария управления Windows (WMI) для объектов управления конфигурацией двумя способами.  
  
-   С помощью редактора WQL или средства создания запросов, например WBEMTest.exe, создается запрос к набору объектов на языке WQL (языке запросов к инструментарию управления Windows).  
  
-   С помощью языка для создания сценариев (например, VBScript).  
  
 Другой способ — управлять службами и сетевыми настройками [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] программным образом, используя управляемые объекты WMI в SMO. Дополнительные сведения о программировании WMI управляемых объектов, см. в разделе [управление службами и сетевыми настройками с помощью поставщика WMI](../../relational-databases/server-management-objects-smo/tasks/managing-services-and-network-settings-by-using-wmi-provider.md).  
  
 Поставщик WMI для управления конфигурацией может осуществляться с помощью [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager и [!INCLUDE[msCoName](../../includes/msconame-md.md)] консоли управления. Дополнительные сведения о доступе к поставщику WMI с помощью пользовательского интерфейса см. в разделе [разделы руководства по управлению службами &#40;диспетчер конфигурации SQL Server&#41;](https://msdn.microsoft.com/library/78dee169-df0c-4c95-9af7-bf033bc9fdc6).  
  
## <a name="see-also"></a>См. также  
 [Доступ к поставщику WMI для управления конфигурацией с использованием WQL](../../relational-databases/wmi-provider-configuration/access-wmi-provider-for-configuration-management-using-wql.md)   
 [Изменение расширенных свойств службы SQL Server с помощью VBScript](../../relational-databases/wmi-provider-configuration/access-wmi-provider-for-configuration-management-using-vbscript.md)  
  
  
