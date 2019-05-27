---
title: Метод GetReportServerUrls (WMI MSReportServer_Instance) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- GetReportServerUrls method
ms.assetid: 4865e32c-0114-465a-be8c-be223a7bc09e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f600d7bf2515cb77c587e5c9c3d5f8d1db1e343f
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66097190"
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
 Массив, который содержит установленные приложения. Значения: либо `ReportServerWebService`, либо `ReportManager`.  
  
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
  
## <a name="see-also"></a>См. также:  
 [Элементы MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-members.md)  
  
  
