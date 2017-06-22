---
title: "Метод SetExtendedProtectionSettings (WMI MSReportServer_ConfigurationSetting) | Документы Microsoft"
ms.custom: 
ms.date: 03/20/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2d8e7232-42f4-41b6-98eb-c856f6c85d8c
caps.latest.revision: 7
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: c40a79e943e9021e10eb321a45d3a14c0fce1582
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="configurationsetting-method---setextendedprotectionsettings"></a>Метод ConfigurationSetting - SetExtendedProtectionSettings
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
  
## <a name="remarks"></a>Замечания  
 Свойства RSWindowsExtendedProtectionLevel и RSWindowsExtendedProtectionScenario используются в том случае, если параметр AuthenticationTypes в файле RSReportServer.config имеет значение RSWindowNTLM, RSWindowsNegotiate или RSWindowsKerberos. Настройка этих свойств влияет на проверку подлинности пользователей и клиентского программного обеспечения на сервере отчетов. Рекомендуется ознакомиться с документацией по расширенной защите, прежде чем устанавливать ExtendedProtectionLevel в значение **Allow** или **Require**.  
  
 Для установки параметра ExtendedProtectionLevel пользователь должен быть членом группы BUILTIN\Administrators на сервере отчетов.  
  
## <a name="requirements"></a>Требования  
 **Пространство имен:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Свойство RSWindowsExtendedProtectionScenario (WMI MSReportServer_ConfigurationSetting)](../../reporting-services/wmi-provider-library-reference/rswindowsextendedprotectionscenario-property.md)   
 [Свойство RSWindowsExtendedProtectionLevel (WMI MSReportServer_ConfigurationSetting)](../../reporting-services/wmi-provider-library-reference/rswindowsextendedprotectionlevel-property.md)   
 [Расширенная защита для проверки подлинности служб Reporting Services](../../reporting-services/security/extended-protection-for-authentication-with-reporting-services.md)   
 [Файл конфигурации RsReportServer.config](../../reporting-services/report-server/rsreportserver-config-configuration-file.md)  
  
  
