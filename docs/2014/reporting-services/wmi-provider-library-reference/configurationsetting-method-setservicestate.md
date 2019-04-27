---
title: Метод SetServiceState (WMI MSReportServer_ConfigurationSetting) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
api_name:
- SetServiceState (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- SetServiceState method
ms.assetid: 9e1ee42d-b388-4929-89c7-8741b956c3be
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b24f8c609aea85acea9cd702459d78f105e7efc2
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62646621"
---
# <a name="setservicestate-method-wmi-msreportserverconfigurationsetting"></a>Метод SetServiceState (WMI MSReportServer_ConfigurationSetting)
  Включает и выключает службу Windows и веб-службу сервера отчетов.  
  
## <a name="syntax"></a>Синтаксис  
  
```vb  
Public Sub SetServiceState(ByVal EnableWindowsService As Boolean, _  
    ByVal EnableWebService As Boolean, ByVal EnableReportManager As Boolean, _  
    ByRef HRESULT As Int32)  
```  
  
```csharp  
public void SetSecureConnectionLevel(Boolean EnableWindowsService,  
    Boolean EnableWebService, Boolean EnableReportManager, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>Параметры  
 *EnableWindowsService*  
 Значение `Boolean`, которое показывает состояние службы Windows. Значение `true` запускает службу Windows сервера отчетов; значение `false` останавливает службу Windows.  
  
 *EnableWebService*  
 Объект `Boolean` значение, указывающее состояние [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] веб-службы. Значение `true` запускает веб-службу сервера отчетов; значение `false` останавливает веб-службу.  
  
 *EnableReportManager*  
 Значение `Boolean`, которое показывает требуемое состояние диспетчера отчетов.  
  
 *HRESULT*  
 [out] Значение, которое указывает, окончился ли вызов успехом или сбоем.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение *HRESULT* , являющееся признаком успешного или неуспешного завершение вызова метода. Значение 0 указывает, что вызов метода завершился успешно. Ненулевое значение указывает, что произошла ошибка.  
  
## <a name="remarks"></a>Примечания  
  
## <a name="requirements"></a>Требования  
 **Пространство имен:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>См. также:  
 [Элементы MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-members.md)  
  
  
