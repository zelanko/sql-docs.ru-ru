---
title: Метод SetExtendedProtectionSettings (WMI MSReportServer_ConfigurationSetting) | Документы Майкрософт
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 2d8e7232-42f4-41b6-98eb-c856f6c85d8c
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 81b0ea8c7142f33ef9fc91622d899e54f21fe756
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48076220"
---
# <a name="setextendedprotectionsettings-method-wmi-msreportserverconfigurationsetting"></a>Метод SetExtendedProtectionSettings (WMI MSReportServer_ConfigurationSetting)
  Метод SetExtendedProtectionSettings устанавливает значения для свойств RSWindowsExtendedProtectionLevel и RSWindowsExtendedProtectionScenario в RSReportServer.config в файле конфигурации служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
## <a name="syntax"></a>Синтаксис  
  
```vb  
Public Sub SetExtendedProtectionSettings( _  
        ByVal ExtendedProtectionLevel As String, _  
        ByVal ExtendedProtectionScenario As String, _  
        ByRef Warnings() As String, _  
        ByRef Length As Int32, _  
        ByRef HRESULT As Int32)  
```  
  
```csharp  
public void SetExtendedProtectionSettings(  
            string ExtendedProtectionLevel,  
            string ExtendedProtectionScenario,  
            out string[] Warnings,  
            out Int32 Length,  
            out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>Параметры  
 *ExtendedProtectionLevel*  
 Устанавливает свойство RSWindowsExtendedProtectionLevel в файле RSRreportserver.config. Значение является обязательным и не зависит от регистра.  
  
 Допустимые значения приведены в следующем списке.  
  
 `”Off | Allow | Require”`  
  
 *ExtendedProtectionScenario*  
 Устанавливает свойство RSWindowsExtendedProtectionScenario в файле RSReportserver.config. Значение является обязательным и не зависит от регистра.  
  
 Допустимые значения приведены в следующем списке.  
  
 `”Any” | “Proxy” | “Direct”`  
  
## <a name="remarks"></a>Примечания  
 Свойства RSWindowsExtendedProtectionLevel и RSWindowsExtendedProtectionScenario используются в том случае, если параметр AuthenticationTypes в файле RSReportServer.config имеет значение RSWindowNTLM, RSWindowsNegotiate или RSWindowsKerberos. Настройка этих свойств влияет на проверку подлинности пользователей и клиентского программного обеспечения на сервере отчетов. Рекомендуется ознакомиться с документацией по расширенной защите, прежде чем устанавливать extendedprotectionlevel в значение либо `Allow` или `Require`.  
  
 Для установки параметра ExtendedProtectionLevel пользователь должен быть членом группы BUILTIN\Administrators на сервере отчетов.  
  
## <a name="requirements"></a>Требования  
 **Пространство имен:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Свойство RSWindowsExtendedProtectionScenario &#40;WMI MSReportServer_ConfigurationSetting&#41;](rswindowsextendedprotectionscenario-property.md)   
 [Свойство RSWindowsExtendedProtectionLevel &#40;WMI MSReportServer_ConfigurationSetting&#41;](rswindowsextendedprotectionlevel-property.md)   
 [Расширенная защита для проверки подлинности с использованием служб Reporting Services](../security/extended-protection-for-authentication-with-reporting-services.md)   
 [Файл конфигурации RSReportServer](../report-server/rsreportserver-config-configuration-file.md)  
  
  
