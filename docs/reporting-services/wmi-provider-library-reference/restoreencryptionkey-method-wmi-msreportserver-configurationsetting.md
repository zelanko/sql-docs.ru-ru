---
title: "Метод RestoreEncryptionKey (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs"
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
  - "RestoreEncryptionKey (WMI MSReportServer_ConfigurationSetting Class)"
apilocation: 
  - "reportingservices.mof"
apitype: "MOFDef"
helpviewer_keywords: 
  - "RestoreEncryptionKey, метод"
ms.assetid: 37e949f5-15af-4858-848a-f482ee94fcd9
caps.latest.revision: 18
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
---
# Метод RestoreEncryptionKey (WMI MSReportServer_ConfigurationSetting)
  Повторно применяет заданный ключ шифрования к базе данных сервера отчетов.  
  
## Синтаксис  
  
```vb  
Public Sub RestoreEncryptionKey(ByRef KeyFile() As Integer, _  
    ByRef Length As Int32, ByVal Password As String, _  
    ByRef HRESULT As Int32, ByRef ExtendedErrors() As String)  
```  
  
```csharp  
public void RestoreEncryptionKey(out Byte[] KeyFile, out Int32 Length,   
            string Password, out Int32 HRESULT, out string[] ExtendedErrors);  
```  
  
## Параметры  
 *KeyFile[]*  
 [out] Массив, содержащий зашифрованный ключ шифрования.  
  
 *Длина*  
 [out] Длина массива, возвращаемого методом.  
  
 *Пароль*  
 Строка, которая используется для шифрования ключа шифрования.  
  
 *HRESULT*  
 [out] Значение, которое указывает, окончился ли вызов успехом или сбоем.  
  
 *ExtendedErrors[]*  
 [out] Массив строк, содержащий дополнительные ошибки, возвращенные в результате вызова.  
  
## Возвращаемое значение  
 Возвращает значение *HRESULT* , являющееся признаком успешного или неуспешного завершение вызова метода. Значение 0 указывает, что вызов метода завершился успешно. Ненулевое значение указывает, что произошла ошибка.  
  
## Замечания  
 Если в базе данных сервера отчетов уже есть запись для сервера отчетов, то она удаляется. Затем создается новая запись с использованием ключа шифрования и открытого ключа сервера отчетов.  
  
 Этот метод наиболее эффективен при вызове после метода [DeleteEncryptionKey](../../reporting-services/wmi-provider-library-reference/deleteencryptionkey-method-wmi-msreportserver-configurationsetting.md) , который очищает список ключей шифрования.  
  
## Требования  
 **Пространство имен:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## См. также  
 [Элементы MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  