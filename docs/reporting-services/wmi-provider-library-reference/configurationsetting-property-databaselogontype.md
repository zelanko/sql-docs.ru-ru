---
title: Свойство DatabaseLogonType (WMI MSReportServer_ConfigurationSetting) | Документы Майкрософт
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: wmi-provider-library-reference
ms.suite: pro-bi
ms.topic: conceptual
apiname:
- DatabaseLogonType
apilocation:
- reportingservices.mof
apitype: MOFDef
helpviewer_keywords:
- DatabaseLogonType property
ms.assetid: 6b592582-4c35-4029-ab86-982fff47d8d6
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 9980443ff67ffe481ec13c074b418ad436864358
ms.sourcegitcommit: d96b94c60d88340224371926f283200496a5ca64
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/30/2018
ms.locfileid: "43265774"
---
# <a name="configurationsetting-property---databaselogontype"></a>Свойство ConfigurationSetting — DatabaseLogonType
  Определяет, какая учетная запись используется для доступа к базе данных сервера отчетов: учетная запись службы [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, учетная запись пользователя Windows, либо имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Только для чтения.  
  
## <a name="syntax"></a>Синтаксис  
  
```vb  
Public Dim DatabaseLogonType As Integer  
```  
  
```csharp  
public int DatabaseLogonType;  
```  
  
## <a name="property-values"></a>Значения свойств  
 Объект **integer** представляет тип входа.  
  
## <a name="example-code"></a>Пример кода  
 [Класс MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-class.md)  
  
## <a name="remarks"></a>Remarks  
 Возможны следующие значения.  
  
-   0 для имени входа Windows  
  
-   1 для имени входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
-   2 для входа в качестве службы  
  
 Если указывается значение 0 (Windows), в свойстве [DatabaseLogonAccount](../../reporting-services/wmi-provider-library-reference/configurationsetting-property-databaselogonaccount.md) необходимо задать соответствующую учетную запись пользователя Windows.  
  
 Если указывается значение 1 (SQL Server), в свойстве [DatabaseLogonAccount](../../reporting-services/wmi-provider-library-reference/configurationsetting-property-databaselogonaccount.md) должно быть задано допустимое имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Если указывается значение 2 (служба Windows), сервер отчетов использует для доступа к своей базе данных учетную запись [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] и учетную запись службы Windows. Свойство DatabaseLogonAccount игнорируется.  
  
## <a name="requirements"></a>Требования  
 **Пространство имен:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>См. также:  
 [Элементы MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
