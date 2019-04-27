---
title: Метод ListSSLCertificateBindings (WMI MSReportServer_ConfigurationSetting) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- ListSSLCertificateBindings method
ms.assetid: d12d280c-9b6f-47a8-bcd9-34cde31c8886
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9b8505017ca0b279a6cc1d7782bff66b120d2851
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62646822"
---
# <a name="listsslcertificatebindings-method-wmi-msreportserverconfigurationsetting"></a>Метод ListSSLCertificateBindings (WMI MSReportServer_ConfigurationSetting)
  Возвращает список SSL-сертификатов, установленных на компьютере.  
  
## <a name="syntax"></a>Синтаксис  
  
```vb  
Public Sub ListSSLCertificateBindings(ByVal LCID As Int32, ByRef Application() As String, _  
    ByRef CertificateHash() As String, ByRef IPAddresses() As String, ByRef Port() As Int32, _  
    ByRef Errors() As String, ByRef Length As Int32, _  
    ByRef HRESULT As Int32)  
```  
  
```csharp  
public void ListSSLCertificateBindings(Int32 Lcid, out string[] Application,   
    out string[] CertificateHash,out string[] IPAddress,   
    out Int32[] Port, out string Errors,   
    out Int32 length, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>Параметры  
 *LCID*  
 Локаль, используемая для возвращаемых сообщений об ошибке.  
  
 *Application[]*  
 [out] Приложения, которые имеют привязки к сертификатам.  
  
 *CertificateHash[]*  
 [out] Значения хэша для сертификата.  
  
 *IPAddress[]*  
 [out] IP-адрес для приложений.  
  
 *Port[]*  
 [out] Номер порта сохраняется в привязке в файле rsreportserver.config.  
  
 *Errors[]*  
 [out] Описания возникших ошибок.  
  
 *Длина*  
 [out] Длина массива, возвращаемого методом.  
  
 *HRESULT*  
 [out] Значение, которое указывает, окончился ли вызов успехом или сбоем.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение *HRESULT* , являющееся признаком успешного или неуспешного завершение вызова метода. Значение 0 указывает, что вызов метода завершился успешно. Ненулевое значение указывает, что произошла ошибка.  
  
## <a name="remarks"></a>Примечания  
  
## <a name="requirements"></a>Требования  
 **Пространство имен:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>См. также:  
 [Элементы MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-members.md)  
  
  
