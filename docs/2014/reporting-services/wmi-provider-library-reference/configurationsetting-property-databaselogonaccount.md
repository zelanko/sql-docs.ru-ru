---
title: Свойство DatabaseLogonAccount (WMI MSReportServer_ConfigurationSetting) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
api_name:
- DatabaseLogonAccount
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- DatabaseLogonAccount property
ms.assetid: 55f2863f-1ac1-4519-b512-e7f11c0ea5ea
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e98447aff31df0f95bc333fc643ab90a5b3f82ba
ms.sourcegitcommit: 8d6fb6bbe3491925909b83103c409effa006df88
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "59950791"
---
# <a name="databaselogonaccount-property-wmi-msreportserverconfigurationsetting"></a>Свойство DatabaseLogonAccount (WMI MSReportServer_ConfigurationSetting)
  Позволяет задать учетную запись входа, используемую сервером отчетов при соединении с его базой данных. Только для чтения.  
  
## <a name="syntax"></a>Синтаксис  
  
```vb  
Public Dim DatabaseLogonAccount As String  
```  
  
```csharp  
public string DatabaseLogonAccount;  
```  
  
## <a name="property-values"></a>Значения свойств  
 Объект `String`, который представляет имя учетной записи входа.  
  
## <a name="example-code"></a>Пример кода  
 [Класс MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-class.md)  
  
## <a name="remarks"></a>Примечания  
 Допустимые значения этого свойства различаются в зависимости от значения свойства [DatabaseLogonType](configurationsetting-property-databaselogontype.md) .  
  
 Это свойство учитывается, если [DatabaseLogonType](configurationsetting-property-databaselogontype.md) свойству `2 (Service)`.  
  
## <a name="requirements"></a>Требования  
 **Пространство имен:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>См. также:  
 [Элементы MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-members.md)  
  
  
