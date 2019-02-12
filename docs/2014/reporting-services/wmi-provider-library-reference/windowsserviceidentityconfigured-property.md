---
title: Свойство WindowsServiceIdentityConfigured (WMI MSReportServer_ConfigurationSetting) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
api_name:
- WindowsServiceIdentityConfigured
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- WindowsServiceIdentityConfigured property
ms.assetid: ebf8e559-7fe4-4a01-9810-85f18fc04596
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 9dc4532b3b7afadf4049fc99296b83c8ae04511a
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/11/2019
ms.locfileid: "56029747"
---
# <a name="windowsserviceidentityconfigured-property-wmi-msreportserverconfigurationsetting"></a>Свойство WindowsServiceIdentityConfigured (WMI MSReportServer_ConfigurationSetting)
  Возвращает удостоверение, для выполнения с которым была в последний раз настроена служба Windows сервера отчетов. Только для чтения.  
  
## <a name="syntax"></a>Синтаксис  
  
```vb  
Public Dim WindowsServiceIdentityConfigured As String  
```  
  
```csharp  
public string WindowsServiceIdentityConfigured;  
```  
  
## <a name="property-values"></a>Значения свойств  
 Значение `String`, содержащее удостоверение, которое в прошлый раз использовалось для выполнения службы Windows сервера отчетов.  
  
## <a name="example-code"></a>Пример кода  
 [Класс MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-class.md)  
  
## <a name="requirements"></a>Требования  
 **Пространство имен:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>См. также:  
 [Элементы MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-members.md)  
  
  
