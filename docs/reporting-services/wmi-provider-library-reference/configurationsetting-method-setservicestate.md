---
title: Метод SetServiceState (WMI MSReportServer_ConfigurationSetting) | Документы Майкрософт
ms.date: 03/17/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: wmi-provider-library-reference
ms.topic: conceptual
apiname:
- SetServiceState (WMI MSReportServer_ConfigurationSetting Class)
apilocation:
- reportingservices.mof
apitype: MOFDef
helpviewer_keywords:
- SetServiceState method
ms.assetid: 9e1ee42d-b388-4929-89c7-8741b956c3be
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 83aa9fb906fc71b1dfb7fd3d036c119d9b4e41e2
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "65580990"
---
# <a name="configurationsetting-method---setservicestate"></a>Метод ConfigurationSetting — SetServiceState
  Включает и выключает службу Windows и веб-службу сервера отчетов.  
  
## <a name="syntax"></a>Синтаксис  
  
```vb  
Public Sub SetServiceState(ByVal EnableWindowsService As Boolean, _  
    ByVal EnableWebService As Boolean, ByVal EnableReportManager As Boolean, _  
    ByRef HRESULT As Int32)  
```  
  
```csharp  
public void SetServiceState(Boolean EnableWindowsService,  
    Boolean EnableWebService, Boolean EnableReportManager, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>Параметры  
 *EnableWindowsService*  
 **Логическое** значение, которое показывает состояние службы Windows. Значение **true** запускает службу Windows сервера отчетов; значение **false** останавливает службу Windows.  
  
 *EnableWebService*  
 **Логическое** значение, которое показывает состояние веб-службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Значение **true** запускает веб-службу сервера отчетов; значение **false** останавливает веб-службу.  
  
 *EnableReportManager*  
 **Логическое** значение, которое показывает требуемое состояние диспетчера отчетов.
 
 > [!NOTE] 
 > Этот параметр считается устаревшим, начиная с SQL Server 2016 Reporting Services с накопительным пакетом обновления 2. Веб-портал всегда будет включен. Значение будет пропущено.
  
 *HRESULT*  
 [out] Значение, которое указывает, окончился ли вызов успехом или сбоем.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение *HRESULT* , являющееся признаком успешного или неуспешного завершение вызова метода. Значение 0 указывает, что вызов метода завершился успешно. Ненулевое значение указывает, что произошла ошибка.  
  
## <a name="remarks"></a>Remarks  
  
## <a name="requirements"></a>Требования  
 **Пространство имен:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>См. также:  
 [Элементы MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
