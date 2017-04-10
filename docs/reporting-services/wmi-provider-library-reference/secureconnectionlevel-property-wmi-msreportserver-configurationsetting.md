---
title: "Свойство SecureConnectionLevel (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs"
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
  - "SecureConnectionLevel"
apilocation: 
  - "reportingservices.mof"
apitype: "MOFDef"
helpviewer_keywords: 
  - "SecureConnectionLevel, свойство"
ms.assetid: fd5549e7-b874-41e2-866e-2f58caf6f733
caps.latest.revision: 19
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
---
# Свойство SecureConnectionLevel (WMI MSReportServer_ConfigurationSetting)
  Возвращает уровень безопасного соединения, заданный в файле RSReportServer.config. Только для чтения.  
  
## Синтаксис  
  
```vb  
Public Dim SecureConnectionLevel As Integer  
```  
  
```csharp  
public Integer SecureConnectionLevel;  
```  
  
## Значения свойств  
 Значение **Integer** , представляющее уровень безопасного соединения. Возвращаемые значения указывают, была произведена настройка SSL или нет. Значение, которое больше или равно 1, указывает на то, что протокол SSL включен. Значение 0 указывает на то, что протокол SSL отключен.  
  
## Пример кода  
 [Класс MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-class.md)  
  
## Требования  
 **Пространство имен:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## См. также  
 [Элементы MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  