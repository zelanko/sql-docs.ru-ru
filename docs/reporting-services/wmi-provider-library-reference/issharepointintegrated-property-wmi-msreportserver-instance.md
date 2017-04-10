---
title: "Свойство IsSharePointIntegrated (WMI MSReportServer_Instance) | Microsoft Docs"
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
  - "IsSharePointIntegrated, свойство"
ms.assetid: e21d00ad-5d9a-4290-8d74-7eeeda39e1ed
caps.latest.revision: 13
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
---
# Свойство IsSharePointIntegrated (WMI MSReportServer_Instance)
  Указывает, находится ли сервер отчетов в режиме интеграции с SharePoint. Начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], это свойство всегда возвращает значение **False**, поскольку в режиме интеграции с SharePoint экземпляры служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] являются совместно используемыми службами SharePoint, которые не управляются поставщиками WMI.  
  
## Синтаксис  
  
```vb  
Public Dim IsSharePointIntegrated As Boolean  
```  
  
```csharp  
public Boolean IsSharePointIntegrated;  
```  
  
## Значения свойств  
 Значение **Boolean** показывает, работает ли сервер отчетов в режиме интеграции с SharePoint.  
  
## Требования  
 **Пространство имен:** [!INCLUDE[ssRSWMInmspc](../../includes/ssrswminmspc-md.md)]  
  
## См. также  
 [Элементы MSReportServer_Instance](../../reporting-services/wmi-provider-library-reference/msreportserver-instance-members.md)   
 [Класс MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-class.md)  
  
  