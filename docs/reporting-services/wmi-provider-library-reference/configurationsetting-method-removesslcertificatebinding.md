---
title: Метод RemoveSSLCertificateBindings (WMI MSReportServer_ConfigurationSetting) | Документы Майкрософт
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: wmi-provider-library-reference
ms.topic: conceptual
helpviewer_keywords:
- RemoveSSLCertificateBindings method
ms.assetid: b8b484c9-04c4-4ae9-980e-67bbe5aa8481
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 11aaa38d8fb06c288399c253d530c1bd8440e597
ms.sourcegitcommit: 8ffc23126609b1cbe2f6820f9a823c5850205372
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2020
ms.locfileid: "81634567"
---
# <a name="configurationsetting-method---removesslcertificatebinding"></a>Метод ConfigurationSetting — RemoveSSLCertificateBinding
  Удаляет привязку к TLS/SSL-сертификату.  
  
## <a name="syntax"></a>Синтаксис  
  
```vb  
Public Sub RemoveSSLCertificateBinding(ByVal Application As String, _  
    ByVal CertificateHash As String, ByVal IPAddress As String, _  
    ByVal Port As Int32, ByVal Lcid As Int32, _  
    ByRef [Error] As String, ByRef HRESULT As Int32)  
```  
  
```csharp  
public void RemoveSSLCertificateBindings(string Application,  
    string CertificateHash, string IPAddress, Int32 Port, Int32 Lcid,  
    out string Error, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>Параметры  
 *Приложение*  
 Имя приложения, для которого следует удалить привязку к сертификату.  
  
 *CertificateHash*  
 Хэш для сертификата.  
  
 *IPAddress*  
 IP-адрес для приложения.  
  
 *порт*.  
 Порт TLS, связанный с привязкой.  
  
 *lcid*  
 Локаль, используемая для возвращаемых сообщений об ошибке.  
  
 *Error*  
 [out] Описания возникших ошибок.  
  
 *HRESULT*  
 [out] Значение, которое указывает, окончился ли вызов успехом или сбоем.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение *HRESULT* , являющееся признаком успешного или неуспешного завершение вызова метода. Значение 0 означает, что вызов метода завершился успешно; код ошибки означает, что произошла ошибка.  
  
## <a name="remarks"></a>Remarks  
 При помощи этого метода выполняется удаление конкретной привязки, заданной в файле rsreportserver.config и, при указании дополнительных параметров, в файле HTTP.SYS.  
  
## <a name="requirements"></a>Требования  
 **Пространство имен:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>См. также:  
 [Элементы MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
