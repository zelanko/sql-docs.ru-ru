---
title: Свойство RSWindowsExtendedProtectionLevel (WMI MSReportServer_ConfigurationSetting) | Документация Майкрософт
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 162ffe86-69c3-49d2-b9ed-49d097c05551
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c3c4fdbf8642715a895e8c345ccd171c53ca3509
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63020127"
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
  
## <a name="remarks"></a>Remarks  
 Возвращает строковое значение, указывающее уровень защиты, на поддержку которого настроен сервер отчетов. Если сервер отчетов, к которому подключен поставщик WMI, не поддерживает расширенную защиту, возвращается пустая строка (""). Допустимые значения приведены в следующем списке.  
  
 `"Off" | "Allow" | "Require"`  
  
## <a name="example-code"></a>Пример кода  
 [Класс MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-class.md)  
  
## <a name="see-also"></a>См. также:  
 [Свойство RSWindowsExtendedProtectionScenario (WMI MSReportServer_ConfigurationSetting)](rswindowsextendedprotectionscenario-property.md)   
 [Метод SetExtendedProtectionSettings (WMI MSReportServer_ConfigurationSetting)](configurationsetting-method-setextendedprotectionsettings.md)   
 [Расширенная защита для проверки подлинности с использованием служб Reporting Services](../security/extended-protection-for-authentication-with-reporting-services.md)   
 [Файл конфигурации RSReportServer](../report-server/rsreportserver-config-configuration-file.md)  
  
  
