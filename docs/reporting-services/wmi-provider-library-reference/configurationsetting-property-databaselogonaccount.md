---
title: Свойство DatabaseLogonAccount (WMI MSReportServer_ConfigurationSetting) | Документы Майкрософт
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: wmi-provider-library-reference
ms.suite: pro-bi
ms.topic: conceptual
apiname:
- DatabaseLogonAccount
apilocation:
- reportingservices.mof
apitype: MOFDef
helpviewer_keywords:
- DatabaseLogonAccount property
ms.assetid: 55f2863f-1ac1-4519-b512-e7f11c0ea5ea
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 30aa804ea5c4622e11c711282667c35381095afe
ms.sourcegitcommit: d96b94c60d88340224371926f283200496a5ca64
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/30/2018
ms.locfileid: "43264747"
---
# <a name="configurationsetting-property---databaselogonaccount"></a>Свойство ConfigurationSetting — DatabaseLogonAccount
  Позволяет задать учетную запись входа, используемую сервером отчетов при соединении с его базой данных. Только для чтения.  
  
## <a name="syntax"></a>Синтаксис  
  
```vb  
Public Dim DatabaseLogonAccount As String  
```  
  
```csharp  
public string DatabaseLogonAccount;  
```  
  
## <a name="property-values"></a>Значения свойств  
 Объект **String** , который представляет имя учетной записи входа.  
  
## <a name="example-code"></a>Пример кода  
 [Класс MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-class.md)  
  
## <a name="remarks"></a>Remarks  
 Допустимые значения этого свойства различаются в зависимости от значения свойства [DatabaseLogonType](../../reporting-services/wmi-provider-library-reference/configurationsetting-property-databaselogontype.md) .  
  
 Это свойство пропускается, если свойство [DatabaseLogonType](../../reporting-services/wmi-provider-library-reference/configurationsetting-property-databaselogontype.md) имеет значение **2 (Служба)**.  
  
## <a name="requirements"></a>Требования  
 **Пространство имен:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>См. также:  
 [Элементы MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
