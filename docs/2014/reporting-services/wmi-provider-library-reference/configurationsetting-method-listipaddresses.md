---
title: Метод ListIPAddresses (WMI MSReportServer_ConfigurationSetting) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- ListIPAddresses method
ms.assetid: 7e7cf182-fba0-4604-a474-098461e23e9d
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 3b8dc70cf1502363585abd7f1be5de7c72c6256a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48062644"
---
# <a name="listipaddresses-method-wmi-msreportserverconfigurationsetting"></a>Метод ListIPAddresses (WMI MSReportServer_ConfigurationSetting)
  Список IP-адресов для компьютера, на котором размещен сервер отчетов.  
  
## <a name="syntax"></a>Синтаксис  
  
```vb  
Public Sub ListIPAddresses (ByRef IPAddress() as String, _  
    ByRef IPVersion()as String, ByRef IsDhcpEnabled () as Boolean, _   
    ByRef Length as Int32, ByRef HRESULT as Int32)  
```  
  
```csharp  
public void ListIPAddresses (out string[] IPAddress,   
    out string[] IPVersion, out bool[] isDhcpEnabled, out int length,   
    out int HRESULT);  
```  
  
## <a name="parameters"></a>Параметры  
 *IPAddress[]*  
 [out] Список IP-адресов для компьютера.  
  
 *IPVersion[]*  
 [out] Версия IP-адресов.  
  
 *IsDhcpEnabled[]*  
 [out] Показывает, используется ли для получения IP-адресов DHCP.  
  
 *Длина*  
 [out] Длина массива, возвращаемого методом.  
  
 *HRESULT*  
 [out] Значение, которое указывает, окончился ли вызов успехом или сбоем.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение *HRESULT* , являющееся признаком успешного или неуспешного завершение вызова метода. Значение 0 означает, что вызов метода завершился успешно; код ошибки означает, что произошла ошибка.  
  
## <a name="remarks"></a>Примечания  
 Строки*IPVersion* имеют значения V4 и V6.  
  
 Если *IsDhcpEnabled* — `True`, *IPAddress* является динамическим. Его не следует использовать для привязок SSL.  
  
## <a name="requirements"></a>Требования  
 **Пространство имен:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Элементы MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-members.md)  
  
  
