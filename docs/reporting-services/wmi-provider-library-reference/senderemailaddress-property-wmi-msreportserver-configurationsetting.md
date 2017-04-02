---
title: "Свойство SenderEmailAddress (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs"
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
  - "SenderEmailAddress"
apilocation: 
  - "reportingservices.mof"
apitype: "MOFDef"
helpviewer_keywords: 
  - "SenderEmailAddress, свойство"
ms.assetid: 087de0ab-6505-48c6-80f3-bd493f76282d
caps.latest.revision: 17
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
---
# Свойство SenderEmailAddress (WMI MSReportServer_ConfigurationSetting)
  Возвращает адрес, используемый для отправки электронной почты с сервера отчетов. Только для чтения.  
  
## Синтаксис  
  
```vb  
Public Dim SenderEmailAddress As String  
```  
  
```csharp  
public string SenderEmailAddress;  
```  
  
## Значения свойств  
 Доступный только для чтения, объект **String**, представляющий адрес электронной почты, используемый сервером отчетов.  
  
## Пример кода  
 [Класс MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-class.md)  
  
## Требования  
 **Пространство имен:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## См. также  
 [Элементы MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  