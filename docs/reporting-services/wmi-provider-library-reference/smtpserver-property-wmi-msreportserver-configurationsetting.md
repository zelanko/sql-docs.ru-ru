---
title: "Свойство SMTPServer (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs"
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
  - "SMTPServer"
apilocation: 
  - "reportingservices.mof"
apitype: "MOFDef"
helpviewer_keywords: 
  - "SMTPServer, свойство"
ms.assetid: 8bcceeba-e1a0-44ef-bda1-600c6925e1db
caps.latest.revision: 18
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
---
# Свойство SMTPServer (WMI MSReportServer_ConfigurationSetting)
  Возвращает свойство SMTP-сервера из файла конфигурации сервера отчетов. Только для чтения.  
  
## Синтаксис  
  
```vb  
Public Dim SMTPServer As String  
```  
  
```csharp  
public string SMTPServer;  
```  
  
## Значения свойств  
 Доступный только для чтения объект **String**, который содержит значение свойства **SMTPServer** из файла RSReportServer.config.  
  
## Пример кода  
 [Класс MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-class.md)  
  
## Требования  
 **Пространство имен:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## См. также  
 [Элементы MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  