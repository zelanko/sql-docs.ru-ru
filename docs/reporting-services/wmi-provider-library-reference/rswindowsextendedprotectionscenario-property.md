---
title: Свойство RSWindowsExtendedProtectionScenario | Документы Майкрософт
ms.date: 03/20/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: wmi-provider-library-reference
ms.topic: conceptual
ms.assetid: 5ac7ab80-9adf-4f65-abfa-fedf53b082b5
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 712b7ec6894cf1c974c00865fc6baa40e9b2a5c9
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47620472"
---
# <a name="rswindowsextendedprotectionscenario-property"></a>Свойство RSWindowsExtendedProtectionScenario
  Возвращает строковое значение, определяющее сценарий расширенной защиты, поддержка которого настроена на сервере отчетов.  
  
## <a name="syntax"></a>Синтаксис  
  
```vb  
Public Dim RSWindowsExtendedProtectionScenario As String  
```  
  
```csharp  
public string RSWindowsExtendedProtectionScenario;  
```  
  
## <a name="remarks"></a>Remarks  
 Возвращает строковое значение, определяющее сценарий расширенной защиты, поддержка которого настроена на сервере отчетов. Если сервер отчетов, к которому подключен поставщик WMI, не поддерживает расширенную защиту, возвращается пустая строка («»).  
  
 Допустимые значения приведены в следующем списке.  
  
 `”Any | Proxy | Direct”`  
  
## <a name="example-code"></a>Пример кода  
 [Класс MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-class.md)  
  
## <a name="see-also"></a>См. также:  
 [Свойство RSWindowsExtendedProtectionLevel (WMI MSReportServer_ConfigurationSetting)](../../reporting-services/wmi-provider-library-reference/rswindowsextendedprotectionlevel-property.md)   
 [Метод SetExtendedProtectionSettings (WMI MSReportServer_ConfigurationSetting)](../../reporting-services/wmi-provider-library-reference/configurationsetting-method-setextendedprotectionsettings.md)   
 [Расширенная защита для проверки подлинности с использованием служб Reporting Services](../../reporting-services/security/extended-protection-for-authentication-with-reporting-services.md)   
 [Файл конфигурации RsReportServer.config](../../reporting-services/report-server/rsreportserver-config-configuration-file.md)  
  
  
