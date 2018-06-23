---
title: Метод ListSSLCertificateBindings (WMI MSReportServer_ConfigurationSetting) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ListSSLCertificateBindings method
ms.assetid: d12d280c-9b6f-47a8-bcd9-34cde31c8886
caps.latest.revision: 12
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 208e408bf2add9144f792c96c7cd4cf6b9671338
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36102573"
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
  
## <a name="see-also"></a>См. также  
 [Элементы MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-members.md)  
  
  