---
title: "Метод ListIPAddresses (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs"
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
  - "ListIPAddresses, метод"
ms.assetid: 7e7cf182-fba0-4604-a474-098461e23e9d
caps.latest.revision: 12
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
---
# Метод ListIPAddresses (WMI MSReportServer_ConfigurationSetting)
  Список IP-адресов для компьютера, на котором размещен сервер отчетов.  
  
## Синтаксис  
  
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
  
## Параметры  
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
  
## Возвращаемое значение  
 Возвращает значение *HRESULT* , являющееся признаком успешного или неуспешного завершение вызова метода. Значение 0 означает, что вызов метода завершился успешно; код ошибки означает, что произошла ошибка.  
  
## Замечания  
 Строки*IPVersion* имеют значения V4 и V6.  
  
 Если *IsDhcpEnabled* = **True**, то *IPAddress* является динамическим. Его не следует использовать для привязок SSL.  
  
## Требования  
 **Пространство имен:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## См. также  
 [Элементы MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  