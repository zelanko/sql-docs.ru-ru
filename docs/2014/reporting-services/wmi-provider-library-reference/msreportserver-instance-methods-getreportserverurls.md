---
title: Метод GetReportServerUrls (WMI MSReportServer_Instance) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- GetReportServerUrls method
ms.assetid: 4865e32c-0114-465a-be8c-be223a7bc09e
caps.latest.revision: 11
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 9b2963bad73fce65f252ad44ed857f6006978c2f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37313206"
---
# <a name="getreportserverurls-method-wmi-msreportserverinstance"></a>Метод GetReportServerUrls (WMI MSReportServer_Instance)
  Возвращает список URL-адресов, которые пользователи могут использовать для доступа к серверу отчетов и диспетчеру отчетов.  
  
## <a name="syntax"></a>Синтаксис  
  
```vb  
Public Sub GetReportServerUrls (ByRef ApplicationName() As String, ByRef URLs()_  
    As String, ByRef Length As Int32, ByRef HRESULT As Int32)  
```  
  
```csharp  
public void GetReportServerUrls(out string[] applicationName,   
    out string[] URLs, out int length, out int HRESULT);  
```  
  
## <a name="parameters"></a>Параметры  
 *ApplicationName[]*  
 Массив, который содержит установленные приложения. Значения: либо `ReportServerWebService` или `ReportManager`.  
  
 *URLs[]*  
 Массив, который содержит успешно зарегистрированные URL-адреса.  
  
 *Длина*  
 Целое значение, представляющее длину возвращенных массивов.  
  
 *HRESULT*  
 Значение, показывающее успешное завершение или код ошибки.  
  
## <a name="return-values"></a>Возвращаемые значения  
  
## <a name="remarks"></a>Примечания  
 Методы, доступные в управляющих объектах WMI, вызываются с помощью функции InvokeMethod. Дополнительные сведения см. в разделе «Выполнение методов в управляющих объектах» документации по инструментарию WMI платформы [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework.  
  
## <a name="requirements"></a>Требования  
 **Пространство имен:** [!INCLUDE[ssRSWMInmspc](../../includes/ssrswminmspc-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Элементы MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-members.md)  
  
  
