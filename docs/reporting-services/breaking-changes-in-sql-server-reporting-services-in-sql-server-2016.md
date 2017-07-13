---
title: "Критические изменения в SQL Server Reporting Services в SQL Server 2016 | Документы Microsoft"
ms.date: 07/02/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Me.Value references
- Reporting Services, backward compatibility
- breaking changes [Reporting Services]
ms.assetid: 39c7aafd-dcb9-4317-b8f7-d15828eb4f9a
caps.latest.revision: 121
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: dcf26be9dc2e502b2d01f5d05bcb005fd7938017
ms.openlocfilehash: 6348d05b8dbe6c8ab1a682388b4e69ce438e6a12
ms.contentlocale: ru-ru
ms.lasthandoff: 07/03/2017

---

# Критические изменения в службах SQL Server Reporting Services в выпуске SQL Server 2016
<a id="breaking-changes-in-sql-server-reporting-services-in-sql-server-2016" class="xliff"></a>

[!INCLUDE [ssrs-appliesto](../includes/ssrs-appliesto.md)] [!INCLUDE [ssrs-appliesto-2016](../includes/ssrs-appliesto-2016.md)] [!INCLUDE [ssrs-appliesto-not-2017](../includes/ssrs-appliesto-not-2017.md)] [!INCLUDE [ssrs-appliesto-not-pbirs](../includes/ssrs-appliesto-not-pbirs.md)]

[!INCLUDE [ssrs-previous-versions](../includes/ssrs-previous-versions.md)]

В этом разделе описаны критические изменения в службах [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]. Эти изменения могут нарушать работу приложений, скриптов или механизмов, основанных на более ранних версиях [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Такие проблемы могут возникать при обновлении либо в пользовательских скриптах или отчетах.

## Модули безопасности
<a id="security-extensions" class="xliff"></a>

Чтобы настраиваемые модули безопасности работали с новым [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)], требуется внести некоторые изменения. Модули безопасности должны использовать интерфейс IAuthenticationExtension2.

## Поставщик WMI
<a id="wmi-provider" class="xliff"></a>

Имя приложения [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)] изменяется с "ReportManager" на "ReportServerWebApp".

## Следующие шаги
<a id="next-steps" class="xliff"></a>

[Изменения в работе служб SQL Server Reporting Services в SQL Server 2016](../reporting-services/behavior-changes-to-sql-server-reporting-services-in-sql-server-2016.md)  
[Новые возможности служб Reporting Services (SSRS)](../reporting-services/what-s-new-in-sql-server-reporting-services-ssrs.md)   
[Устаревшие функции служб SQL Server Reporting Services в SQL Server 2016](../reporting-services/deprecated-features-in-sql-server-reporting-services-ssrs.md)    
[Неподдерживаемые возможности в службах SQL Server Reporting Services в версии SQL Server 2016](../reporting-services/discontinued-functionality-to-sql-server-reporting-services-in-sql-server.md)  

Дополнительные вопросы? [Попробуйте задать вопрос на форуме служб Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)
