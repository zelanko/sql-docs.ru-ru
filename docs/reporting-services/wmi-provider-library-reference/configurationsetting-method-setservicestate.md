---
title: "Метод SetServiceState (WMI MSReportServer_ConfigurationSetting) | Документы Microsoft"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SetServiceState (WMI MSReportServer_ConfigurationSetting Class)
apilocation:
- reportingservices.mof
apitype: MOFDef
helpviewer_keywords:
- SetServiceState method
ms.assetid: 9e1ee42d-b388-4929-89c7-8741b956c3be
caps.latest.revision: 20
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 8964b2b0886ffd0483e48c8e9baf91ab9b2dae3d
ms.contentlocale: ru-ru
ms.lasthandoff: 08/09/2017

---
# <a name="configurationsetting-method---setservicestate"></a>Метод ConfigurationSetting - SetServiceState
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
 > Этот параметр рекомендуется к использованию на момент служб SQL Server 2016 Reporting накопительное обновление 2. Всегда будет включено на веб-портале. Значение будет игнорироваться.
  
 *HRESULT*  
 [out] Значение, которое указывает, окончился ли вызов успехом или сбоем.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение *HRESULT* , являющееся признаком успешного или неуспешного завершение вызова метода. Значение 0 указывает, что вызов метода завершился успешно. Ненулевое значение указывает, что произошла ошибка.  
  
## <a name="remarks"></a>Замечания  
  
## <a name="requirements"></a>Требования  
 **Пространство имен:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Элементы MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  

