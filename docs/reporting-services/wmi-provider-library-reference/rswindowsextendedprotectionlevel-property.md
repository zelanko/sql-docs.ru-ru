---
title: Свойство RSWindowsExtendedProtectionLevel | Документы Майкрософт
ms.date: 03/20/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: wmi-provider-library-reference
ms.topic: conceptual
ms.assetid: 162ffe86-69c3-49d2-b9ed-49d097c05551
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 7854821a9f43bc234490d915ff75339e250f6c39
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "65571076"
---
# <a name="rswindowsextendedprotectionlevel-property"></a>Свойство RSWindowsExtendedProtectionLevel
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
 [Класс MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-class.md)  
  
## <a name="see-also"></a>См. также:  
 [Свойство RSWindowsExtendedProtectionScenario (WMI MSReportServer_ConfigurationSetting)](../../reporting-services/wmi-provider-library-reference/rswindowsextendedprotectionscenario-property.md)   
 [Метод SetExtendedProtectionSettings (WMI MSReportServer_ConfigurationSetting)](../../reporting-services/wmi-provider-library-reference/configurationsetting-method-setextendedprotectionsettings.md)   
 [Расширенная защита для проверки подлинности с использованием служб Reporting Services](../../reporting-services/security/extended-protection-for-authentication-with-reporting-services.md)   
 [Файл конфигурации RsReportServer.config](../../reporting-services/report-server/rsreportserver-config-configuration-file.md)  
  
  
