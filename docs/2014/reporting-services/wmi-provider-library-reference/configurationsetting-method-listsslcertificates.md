---
title: Метод ListSSLCertificates (WMI MSReportServer_ConfigurationSetting) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- ListSSLCertificates method
ms.assetid: 88cd0936-b202-4ab8-90f2-d9c3f66d37f4
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: a83096e8b1fe3eed9e0df513931b812125955f61
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48221724"
---
# <a name="listsslcertificates-method-wmi-msreportserverconfigurationsetting"></a>Метод ListSSLCertificates (WMI MSReportServer_ConfigurationSetting)
  Возвращает список сертификатов на компьютере с сервером отчетов.  
  
## <a name="syntax"></a>Синтаксис  
  
```vb  
Public Sub CreateSSLCertificateBinding (ByRef CertificateHash() as String, _  
    ByRef CertName() as String, ByRef HostName() as String, ByRef Length as Int32, _   
    ByRef HRESULT as Int32)  
```  
  
```csharp  
public void ListSSLCertificates(out string[] CertificateHash,   
    out string[] CertName, out string[] Hostname, out Int32 length,   
    out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>Параметры  
 *CertificateHash[]*  
 [out] Хэши сертификатов.  
  
 *CertName[]*  
 [out] Имена сертификата.  
  
 *HostName[]*  
 [out] Имена узлов для сертификатов.  
  
 *Длина*  
 [out] Представляет длину массивов *CertificateHash*, *CertName* и *HostName* .  
  
 *HRESULT*  
 [out] Значение, которое указывает, окончился ли вызов успехом или сбоем.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение *HRESULT* , являющееся признаком успешного или неуспешного завершение вызова метода. Значение 0 означает, что вызов метода завершился успешно; код ошибки означает, что произошла ошибка.  
  
## <a name="remarks"></a>Примечания  
  
## <a name="requirements"></a>Требования  
 **Пространство имен:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Элементы MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-members.md)  
  
  
