---
title: Свойство IsWindowsServiceEnabled (WMI MSReportServer_ConfigurationSetting) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
api_name:
- IsWindowsServiceEnabled
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- IsWindowsServiceEnabled property
ms.assetid: b1b75d72-6220-43fe-abfb-f967f3972d00
caps.latest.revision: 18
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 0d4ca95b48903214cebbbb1548eaa3535c0584c2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36188613"
---
# <a name="iswindowsserviceenabled-property-wmi-msreportserverconfigurationsetting"></a>Свойство IsWindowsServiceEnabled (WMI MSReportServer_ConfigurationSetting)
  Указывает, включена ли служба Windows сервера отчетов. Только для чтения.  
  
## <a name="syntax"></a>Синтаксис  
  
```vb  
Public Dim IsWindowsServiceEnabled As Boolean  
```  
  
```csharp  
public boolean IsWindowsServiceEnabled;  
```  
  
## <a name="property-values"></a>Значения свойств  
 **Логическое** значение только для чтения. Значение `true` показывает, что служба Windows сервера отчетов включена.  
  
## <a name="example-code"></a>Пример кода  
 [Класс MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-class.md)  
  
## <a name="requirements"></a>Требования  
 **Пространство имен:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Элементы MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-members.md)  
  
  