---
title: "Критические изменения в службах SQL Server Reporting Services в выпуске SQL Server 2016 | Microsoft Docs"
ms.date: "03/15/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ссылки на Me.Value"
  - "Службы Reporting Services, обратная совместимость"
  - "критические изменения [службы Reporting Services]"
ms.assetid: 39c7aafd-dcb9-4317-b8f7-d15828eb4f9a
caps.latest.revision: 121
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 116
---
# Критические изменения в службах SQL Server Reporting Services в выпуске SQL Server 2016
  В этом разделе описаны критические изменения в службах [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]. Эти изменения могут нарушать работу приложений, скриптов или механизмов, основанных на более ранних версиях [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Такие проблемы могут возникать при обновлении либо в пользовательских скриптах или отчетах.  
  
  ## Модули безопасности
  
  Чтобы настраиваемые модули безопасности работали с новым [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)], требуется внести некоторые изменения. Модули безопасности должны использовать интерфейс IAuthenticationExtension2.
  
  ## Поставщик WMI
  
  Имя приложения [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)] изменяется с "ReportManager" на "ReportServerWebApp".
  
## См. также:  
 [Изменения в работе служб SQL Server Reporting Services в выпуске SQL Server 2016](http://msdn.microsoft.com/ru-ru/2a767f0f-84f2-4099-8784-1e37790f858e)   
 [Новые возможности служб Reporting Services (SSRS)](../Topic/What's%20New%20in%20Reporting%20Services%20\(SSRS\).md)   
 [Нерекомендуемые функции служб SQL Server Reporting Services в SQL Server 2016](http://msdn.microsoft.com/ru-ru/3876c01e-f81d-4cce-9104-5106a8c369e6)   
 [Неподдерживаемые возможности в службах SQL Server Reporting Services в версии SQL Server 2016](http://msdn.microsoft.com/ru-ru/d529cc96-3483-480b-9bfc-bd28b1d0ef52)  
  
  