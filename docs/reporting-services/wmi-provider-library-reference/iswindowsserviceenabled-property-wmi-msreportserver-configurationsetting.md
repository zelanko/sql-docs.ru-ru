---
title: "Свойство IsWindowsServiceEnabled (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs"
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
  - "IsWindowsServiceEnabled"
apilocation: 
  - "reportingservices.mof"
apitype: "MOFDef"
helpviewer_keywords: 
  - "IsWindowsServiceEnabled, свойство"
ms.assetid: b1b75d72-6220-43fe-abfb-f967f3972d00
caps.latest.revision: 18
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
---
# Свойство IsWindowsServiceEnabled (WMI MSReportServer_ConfigurationSetting)
  Указывает, включена ли служба Windows сервера отчетов. Только для чтения.  
  
## Синтаксис  
  
```vb  
Public Dim IsWindowsServiceEnabled As Boolean  
```  
  
```csharp  
public boolean IsWindowsServiceEnabled;  
```  
  
## Значения свойств  
 **Логическое** значение только для чтения. Значение **true** показывает, что служба Windows сервера отчетов включена.  
  
## Пример кода  
 [Класс MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-class.md)  
  
## Требования  
 **Пространство имен:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## См. также  
 [Элементы MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  