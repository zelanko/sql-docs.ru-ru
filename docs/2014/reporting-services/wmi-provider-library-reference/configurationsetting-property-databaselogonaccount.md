---
title: Свойство DatabaseLogonAccount (WMI MSReportServer_ConfigurationSetting) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
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
caps.latest.revision: 24
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 6b94a45ed2c528972fffb79d2f8f51ad9bcba56d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37185767"
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
 Допустимые значения для этого свойства различаются в зависимости от значения [DatabaseLogonType](configurationsetting-property-databaselogontype.md) свойство.  
  
 Это свойство учитывается, если [DatabaseLogonType](configurationsetting-property-databaselogontype.md) свойству `2 (Service)`.  
  
## <a name="requirements"></a>Требования  
 **Пространство имен:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Элементы MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-members.md)  
  
  
