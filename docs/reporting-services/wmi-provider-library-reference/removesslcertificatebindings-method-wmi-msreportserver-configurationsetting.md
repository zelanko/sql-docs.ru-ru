---
title: "Метод RemoveSSLCertificateBindings (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs"
ms.custom: ""
ms.date: "03/23/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "RemoveSSLCertificateBindings, метод"
ms.assetid: b8b484c9-04c4-4ae9-980e-67bbe5aa8481
caps.latest.revision: 12
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
---
# Метод RemoveSSLCertificateBindings (WMI MSReportServer_ConfigurationSetting)
  Удаляет привязку к SSL-сертификату.  
  
## Синтаксис  
  
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
  
## Параметры  
 *Приложение*  
 Имя приложения, для которого следует удалить привязку к сертификату.  
  
 *CertificateHash*  
 Хэш для сертификата.  
  
 *IPAddress*  
 IP-адрес для приложения.  
  
 *Порт*  
 Порт SSL, связанный с привязкой.  
  
 *lcid*  
 Локаль, используемая для возвращаемых сообщений об ошибке.  
  
 *Ошибка*  
 [out] Описания возникших ошибок.  
  
 *HRESULT*  
 [out] Значение, которое указывает, окончился ли вызов успехом или сбоем.  
  
## Возвращаемое значение  
 Возвращает значение *HRESULT* , являющееся признаком успешного или неуспешного завершение вызова метода. Значение 0 означает, что вызов метода завершился успешно; код ошибки означает, что произошла ошибка.  
  
## Замечания  
 При помощи этого метода выполняется удаление конкретной привязки, заданной в файле rsreportserver.config и, при указании дополнительных параметров, в файле HTTP.SYS.  
  
## Требования  
 **Пространство имен:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## См. также  
 [Элементы MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  