---
title: Свойство RSWindowsExtendedProtectionLevel (WMI MSReportServer_ConfigurationSetting) | Документы Microsoft
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 162ffe86-69c3-49d2-b9ed-49d097c05551
caps.latest.revision: 5
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 9e96011dc05f0bc21708f8759aa715dbc4ca79a5
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36193925"
---
# <a name="rswindowsextendedprotectionlevel-property-wmi-msreportserverconfigurationsetting"></a>Свойство RSWindowsExtendedProtectionLevel (WMI MSReportServer_ConfigurationSetting)
  Возвращает строковое значение, указывающее уровень защиты, на поддержку которого настроен сервер отчетов. Это свойство доступно только для чтения.  
  
## <a name="syntax"></a>Синтаксис  
  
```vb  
Public Dim RSWindowsExtendedProtectionLevel As String  
```  
  
```csharp  
public string RSWindowsExtendedProtectionLevel;  
```  
  
## <a name="remarks"></a>Примечания  
 Возвращает строковое значение, указывающее уровень защиты, на поддержку которого настроен сервер отчетов. Если сервер отчетов, к которому подключен поставщик WMI, не поддерживает расширенную защиту, возвращается пустая строка («»). Допустимые значения приведены в следующем списке.  
  
 `“Off” | “Allow” | “Require”`  
  
## <a name="example-code"></a>Пример кода  
 [Класс MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-class.md)  
  
## <a name="see-also"></a>См. также  
 [Свойство RSWindowsExtendedProtectionScenario &#40;WMI MSReportServer_ConfigurationSetting&#41;](rswindowsextendedprotectionscenario-property.md)   
 [Метод SetExtendedProtectionSettings (WMI MSReportServer_ConfigurationSetting)](configurationsetting-method-setextendedprotectionsettings.md)   
 [Расширенная защита для проверки подлинности с использованием служб Reporting Services](../security/extended-protection-for-authentication-with-reporting-services.md)   
 [Файл конфигурации RSReportServer](../report-server/rsreportserver-config-configuration-file.md)  
  
  