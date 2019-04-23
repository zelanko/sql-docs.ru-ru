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
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: cce9098bb9716294ae7b8c3cdf7095d668b8fad9
ms.sourcegitcommit: 8d6fb6bbe3491925909b83103c409effa006df88
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "59945560"
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
  
 `"Off | Allow | Require"`  
  
 *ExtendedProtectionScenario*  
 Устанавливает свойство RSWindowsExtendedProtectionScenario в файле RSReportserver.config. Значение является обязательным и не зависит от регистра.  
  
 Допустимые значения приведены в следующем списке.  
  
 `"Any" | "Proxy" | "Direct"`  
  
## <a name="remarks"></a>Примечания  
 Свойства RSWindowsExtendedProtectionLevel и RSWindowsExtendedProtectionScenario используются в том случае, если параметр AuthenticationTypes в файле RSReportServer.config имеет значение RSWindowNTLM, RSWindowsNegotiate или RSWindowsKerberos. Настройка этих свойств влияет на проверку подлинности пользователей и клиентского программного обеспечения на сервере отчетов. Рекомендуется ознакомиться с документацией по расширенной защите, прежде чем устанавливать ExtendedProtectionLevel в значение `Allow` или `Require`.  
  
 Для установки параметра ExtendedProtectionLevel пользователь должен быть членом группы BUILTIN\Administrators на сервере отчетов.  
  
## <a name="requirements"></a>Требования  
 **Пространство имен:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Свойство RSWindowsExtendedProtectionScenario (WMI MSReportServer_ConfigurationSetting)](rswindowsextendedprotectionscenario-property.md)   
 [Свойство RSWindowsExtendedProtectionLevel (WMI MSReportServer_ConfigurationSetting)](rswindowsextendedprotectionlevel-property.md)   
 [Расширенная защита для проверки подлинности с использованием служб Reporting Services](../security/extended-protection-for-authentication-with-reporting-services.md)   
 [Файл конфигурации RSReportServer](../report-server/rsreportserver-config-configuration-file.md)  
  
  
