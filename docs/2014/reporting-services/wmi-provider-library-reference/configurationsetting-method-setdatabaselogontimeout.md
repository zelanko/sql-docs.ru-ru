---
title: Метод SetDatabaseLogonTimeout (WMI MSReportServer_ConfigurationSetting) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
api_name:
- SetDatabaseLogonTimeout (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- SetDatabaseLogonTimeout method
ms.assetid: b8773596-5b98-4355-a4ab-4412e1317c67
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 1d3d01b2042d163fdee45a87b7341a1a3b6dd3ce
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48126806"
---
# <a name="setdatabaselogontimeout-method-wmi-msreportserverconfigurationsetting"></a>Метод SetDatabaseLogonTimeout (WMI MSReportServer_ConfigurationSetting)
  Задает значение времени ожидания по умолчанию для подключений к базе данных сервера отчетов.  
  
## <a name="syntax"></a>Синтаксис  
  
```vb  
Public Sub SetDatabaseLogonTimeout(LogonTimeout as Int32, _  
    ByRef HRESULT as Int32)  
```  
  
```csharp  
public void SetDatabaseLogonTimeout(Int32 LogonTimeout,   
    out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>Параметры  
 *LogonTimeout*  
 Значение времени ожидания по умолчанию в секундах для подключений к базе данных сервера отчетов.  
  
 *HRESULT*  
 [out] Значение, которое указывает, окончился ли вызов успехом или сбоем.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение *HRESULT* , являющееся признаком успешного или неуспешного завершение вызова метода. Значение 0 указывает, что вызов метода завершился успешно. Ненулевое значение указывает, что произошла ошибка.  
  
## <a name="requirements"></a>Требования  
 **Пространство имен:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Элементы MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-members.md)  
  
  
