---
title: Свойство RSWindowsExtendedProtectionScenario (WMI MSReportServer_ConfigurationSetting) | Документация Майкрософт
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 5ac7ab80-9adf-4f65-abfa-fedf53b082b5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 60a61ca96aafe0e475d28023276c561f49c13cde
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66096983"
---
# <a name="rswindowsextendedprotectionscenario-property-wmi-msreportserver_configurationsetting"></a>Свойство RSWindowsExtendedProtectionScenario (WMI MSReportServer_ConfigurationSetting)
  Возвращает строковое значение, определяющее сценарий расширенной защиты, поддержка которого настроена на сервере отчетов.  
  
## <a name="syntax"></a>Синтаксис  
  
```vb  
Public Dim RSWindowsExtendedProtectionScenario As String  
```  
  
```csharp  
public string RSWindowsExtendedProtectionScenario;  
```  
  
## <a name="remarks"></a>Remarks  
 Возвращает строковое значение, определяющее сценарий расширенной защиты, поддержка которого настроена на сервере отчетов. Если сервер отчетов, к которому подключен поставщик WMI, не поддерживает расширенную защиту, возвращается пустая строка ("").  
  
 Допустимые значения приведены в следующем списке.  
  
 `"Any | Proxy | Direct"`  
  
## <a name="example-code"></a>Пример кода  
 [Класс MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-class.md)  
  
## <a name="see-also"></a>См. также:  
 [Свойство RSWindowsExtendedProtectionLevel (WMI MSReportServer_ConfigurationSetting)](rswindowsextendedprotectionlevel-property.md)   
 [Метод SetExtendedProtectionSettings (WMI MSReportServer_ConfigurationSetting)](configurationsetting-method-setextendedprotectionsettings.md)   
 [Расширенная защита для проверки подлинности с использованием служб Reporting Services](../security/extended-protection-for-authentication-with-reporting-services.md)   
 [RSReportServer Configuration File](../report-server/rsreportserver-config-configuration-file.md)  
  
  
