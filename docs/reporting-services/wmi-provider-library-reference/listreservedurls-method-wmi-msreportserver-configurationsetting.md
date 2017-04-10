---
title: "Метод ListReservedURLs (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs"
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
  - "ListReservedURLs, метод"
ms.assetid: 32335af1-5eae-4420-a0ef-b1e8a3267166
caps.latest.revision: 11
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
---
# Метод ListReservedURLs (WMI MSReportServer_ConfigurationSetting)
  Выводит список URL-адресов, зарезервированных для всех приложений на сервере отчетов.  
  
## Синтаксис  
  
```vb  
Public Sub ListReservedUrls(ByRef Application() as String, ByRef UrlString() as String, _  
    ByRef Account() as String, ByRef AccountSID() as String, _  
    ByRef length() as Int32, ByRef HRESULT as Int32)  
```  
  
```csharp  
public void ListReservedUrls(out string[] Application, out string[] UrlString,  
        out string[] Account, out string[] AccountSID,  
        out int[] Length, out int[] HRESULT);  
```  
  
## Параметры  
 *Application[]*  
 [out] Приложения, которые имеют резервирование URL-адресов.  
  
 *UrlString[]*  
 [out] Зарезервированные URL-адреса.  
  
 *Account[]*  
 [out] Имена учетной записи, связанные с учетной записью для резервирования URL-адресов.  
  
 *AccountSID[]*  
 [out] Идентификаторы безопасности, связанные с учетной записью для резервирования URL-адресов.  
  
 *Длина*  
 [out] Длина массивов, возвращаемых методом.  
  
 *HRESULT*  
 [out] Значение, которое указывает, окончился ли вызов успехом или сбоем.  
  
## Возвращаемое значение  
 Возвращает значение *HRESULT* , являющееся признаком успешного или неуспешного завершение вызова метода. Значение 0 означает, что вызов метода завершился успешно; код ошибки означает, что произошла ошибка.  
  
## Замечания  
  
## Требования  
 **Пространство имен:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## См. также  
 [Элементы MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  