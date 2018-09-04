---
title: Метод ListReportServersInDatabase (WMI MSReportServer_ConfigurationSetting) | Документы Майкрософт
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: wmi-provider-library-reference
ms.suite: pro-bi
ms.topic: conceptual
apiname:
- ListReportServersInDatabase (WMI MSReportServer_ConfigurationSetting Class)
apilocation:
- reportingservices.mof
apitype: MOFDef
helpviewer_keywords:
- ListReportServersInDatabase method
ms.assetid: a4bf5968-c46f-484f-a510-65e2dde65a0d
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 16c9bbfbd26f51fb32083a4376b76175b5ec4580
ms.sourcegitcommit: d96b94c60d88340224371926f283200496a5ca64
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/30/2018
ms.locfileid: "43278413"
---
# <a name="configurationsetting-method---listreportserversindatabase"></a>Метод ConfigurationSetting — ListReportServersInDatabase
  Возвращает список установок сервера отчетов, которые находятся в базе данных сервера отчетов независимо от наличия доступа к защищенным сведениям.  
  
## <a name="syntax"></a>Синтаксис  
  
```vb  
Public Sub ListReportServersInDatabase(ByRef MachineNames() As String, _  
    ByRef InstanceNames() As String, ByRef InstallationIDs() As String, _  
    ByRef IsInitialized() As Boolean, ByRef Length As Int32, _  
    ByRef HRESULT As Int32, ByRef ExtendedErrors() As String)  
```  
  
```csharp  
public void ListReportServersInDatabase (out string[] MachineNames,   
    out string[] InstanceNames, out string[] InstallationIDs,   
    out Boolean[] IsInitialized,out Int32 Length, out Int32 HRESULT,    
    out string[] ExtendedErrors);  
```  
  
## <a name="parameters"></a>Параметры  
 *MachineNames[]*  
 [out] Массив, который содержит имена компьютеров, где установлен сервер отчетов в базе данных.  
  
 *InstanceNames[]*  
 [out] Массив, который содержит имена экземпляров каждого установленного сервера отчетов в базе данных.  
  
 *InstallationIDs[]*  
 [out] Массив, который содержит коды установки каждого установленного сервера отчетов в базе данных.  
  
 *IsInitialized[]*  
 [out] Массив, который содержит состояние инициализации каждого установленного сервера отчетов в базе данных.  
  
 *Длина*  
 [out] Длина массивов, возвращаемых методом. Все возвращенные массивы имеют одинаковую длину.  
  
 *HRESULT*  
 [out] Значение, которое указывает, окончился ли вызов успехом или сбоем.  
  
 *ExtendedErrors[]*  
 [out] Массив строк, содержащий дополнительные ошибки, возвращенные в результате вызова.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение *HRESULT* , являющееся признаком успешного или неуспешного завершение вызова метода. Значение 0 указывает, что вызов метода завершился успешно. Ненулевое значение указывает, что произошла ошибка.  
  
## <a name="remarks"></a>Remarks  
 Метод ListReportServersInDatabase выводит список установленных серверов отчетов, которые имеются в базе данных сервера отчетов, независимо от наличия у них доступа к защищенным сведениям, и возвращает сопоставленный набор массивов с данными о каждом установленном сервере отчетов.  
  
## <a name="requirements"></a>Требования  
 **Пространство имен:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>См. также:  
 [Элементы MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
