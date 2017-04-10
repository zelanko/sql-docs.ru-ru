---
title: "Свойство DatabaseQueryTimeout (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs"
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
  - "DatabaseQueryTimeout Property"
apilocation: 
  - "reportingservices.mof"
apitype: "MOFDef"
helpviewer_keywords: 
  - "DatabaseQueryTimeout, свойство"
ms.assetid: 96faed97-9799-4bbf-a66f-fdd532d3eace
caps.latest.revision: 35
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
---
# Свойство DatabaseQueryTimeout (WMI MSReportServer_ConfigurationSetting)
  Задает число секунд, которое должно пройти до того, как сервер отчетов предположит, что при выполнении команды произошла ошибка или выполнение заняло слишком много времени. Сервер отчетов привязывает запросы по времени к каталогу SQL, а не к источнику данных для отчета. Read/write.  
  
## Синтаксис  
  
```vb  
Public Dim DatabaseQueryTimeout As UInt32  
```  
  
```csharp  
public UInt32 DatabaseQueryTimeout;  
```  
  
## Значения свойств  
 Объект 32-разрядного беззнакового **целого числа**, показывающий время в секундах, которое отводится на выполнение запроса.  
  
## Пример кода  
 [Класс MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-class.md)  
  
## Требования  
 **Пространство имен:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## См. также  
 [Элементы MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  