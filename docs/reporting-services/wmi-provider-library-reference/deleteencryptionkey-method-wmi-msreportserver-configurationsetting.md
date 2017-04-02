---
title: "Метод DeleteEncryptionKey (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs"
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
apiname: 
  - "DeleteEncryptionKey (WMI MSReportServer_ConfigurationSetting Class)"
apilocation: 
  - "reportingservices.mof"
apitype: "MOFDef"
helpviewer_keywords: 
  - "DeleteEncryptionKey, метод"
ms.assetid: ed2f25b6-6a63-468d-9279-a577ca01b096
caps.latest.revision: 20
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
---
# Метод DeleteEncryptionKey (WMI MSReportServer_ConfigurationSetting)
  Удаляет ключи шифрования из базы данных сервера отчетов.  
  
## Синтаксис  
  
```vb  
Public Sub DeleteEncryptionKeys(ByVal InstallationID As String, _  
    ByRef HRESULT As Int32, ByRef ExtendedErrors() As String)  
```  
  
```csharp  
public void DeleteEncryptionKeys(string InstallationID, out Int32 HRESULT,   
    out string[] ExtendedErrors);  
```  
  
## Параметры  
 *InstallationID*  
 Код установки сервера отчетов, который находится в таблице ключей в базе данных сервера отчетов.  
  
 *HRESULT*  
 [out] Значение, которое указывает, окончился ли вызов успехом или сбоем.  
  
 *ExtendedErrors[]*  
 [out] Массив строк, содержащий дополнительные ошибки, возвращенные в результате вызова.  
  
## Возвращаемое значение  
 Возвращает значение HRESULT, которое является признаком успешного или неуспешного завершения вызова метода. Значение 0 указывает, что вызов метода завершился успешно. Ненулевое значение указывает, что произошла ошибка.  
  
## Замечания  
 Метод *DeleteEncryptionKey* удаляет записи из таблицы ключей для любых серверов отчетов, у которых есть доступ к защищенным сведениям в базе данных сервера отчетов. Если указанный параметр *InstallationID* не соответствует коду установки в базе данных, то метод возвращает ошибку.  
  
## Требования  
 **Пространство имен:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## См. также  
 [Элементы MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  