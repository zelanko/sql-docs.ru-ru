---
title: "Свойство WindowsServiceIdentityConfigured (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "WindowsServiceIdentityConfigured"
apilocation: 
  - "reportingservices.mof"
apitype: "MOFDef"
helpviewer_keywords: 
  - "WindowsServiceIdentityConfigured, свойство"
ms.assetid: ebf8e559-7fe4-4a01-9810-85f18fc04596
caps.latest.revision: 17
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 17
---
# Свойство WindowsServiceIdentityConfigured (WMI MSReportServer_ConfigurationSetting)
  Возвращает удостоверение, для выполнения с которым была в последний раз настроена служба Windows сервера отчетов. Только для чтения.  
  
## Синтаксис  
  
```vb  
Public Dim WindowsServiceIdentityConfigured As String  
```  
  
```csharp  
public string WindowsServiceIdentityConfigured;  
```  
  
## Значения свойств  
 Значение **String** , содержащее удостоверение, которое в прошлый раз использовалось для выполнения службы Windows сервера отчетов.  
  
## Пример кода  
 [Класс MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-class.md)  
  
## Требования  
 **Пространство имен:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## См. также  
 [Элементы MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  