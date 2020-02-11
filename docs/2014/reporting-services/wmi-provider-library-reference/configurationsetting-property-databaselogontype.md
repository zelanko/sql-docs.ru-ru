---
title: Свойство DatabaseLogonType (WMI MSReportServer_ConfigurationSetting) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- DatabaseLogonType
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- DatabaseLogonType property
ms.assetid: 6b592582-4c35-4029-ab86-982fff47d8d6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b58c380b85e412554eb47315dfe356d3bff08d03
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66097822"
---
# <a name="databaselogontype-property-wmi-msreportserver_configurationsetting"></a>Свойство DatabaseLogonType (WMI MSReportServer_ConfigurationSetting)
  Определяет, какая учетная запись используется для доступа к базе данных сервера отчетов: учетная запись службы [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, учетная запись пользователя Windows, либо имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Только для чтения.  
  
## <a name="syntax"></a>Синтаксис  
  
```vb  
Public Dim DatabaseLogonType As Integer  
```  
  
```csharp  
public int DatabaseLogonType;  
```  
  
## <a name="property-values"></a>Значения свойств  
 Объект `integer` представляет тип входа.  
  
## <a name="example-code"></a>Пример кода  
 [Класс MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-class.md)  
  
## <a name="remarks"></a>Remarks  
 Возможны следующие значения.  
  
-   0 для имени входа Windows  
  
-   1 для имени входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
-   2 для входа в качестве службы  
  
 Если указывается значение 0 (Windows), в свойстве [DatabaseLogonAccount](configurationsetting-property-databaselogonaccount.md) необходимо задать соответствующую учетную запись пользователя Windows.  
  
 Если указывается значение 1 (SQL Server), в свойстве [DatabaseLogonAccount](configurationsetting-property-databaselogonaccount.md) должно быть задано допустимое имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Если указывается значение 2 (служба Windows), сервер отчетов использует для доступа к своей базе данных учетную запись [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] и учетную запись службы Windows. Свойство DatabaseLogonAccount игнорируется.  
  
## <a name="requirements"></a>Требования  
 **Пространство имен:**[!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>См. также:  
 [Элементы MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-members.md)  
  
  
