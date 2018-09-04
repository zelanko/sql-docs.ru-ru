---
title: Критические изменения в службах SQL Server Reporting Services в SQL Server 2016 | Документы Майкрософт
ms.date: 07/02/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: reporting-services
ms.suite: pro-bi
ms.topic: conceptual
helpviewer_keywords:
- Me.Value references
- Reporting Services, backward compatibility
- breaking changes [Reporting Services]
ms.assetid: 39c7aafd-dcb9-4317-b8f7-d15828eb4f9a
author: markingmyname
ms.author: maghan
ms.openlocfilehash: bb8bd3ab583e4bd0c23d0c879a5a3ee09359adfe
ms.sourcegitcommit: d96b94c60d88340224371926f283200496a5ca64
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/30/2018
ms.locfileid: "43269770"
---
# <a name="breaking-changes-in-sql-server-reporting-services-in-sql-server-2016"></a>Критические изменения в службах SQL Server Reporting Services в выпуске SQL Server 2016

[!INCLUDE [ssrs-appliesto](../includes/ssrs-appliesto.md)] [!INCLUDE [ssrs-appliesto-2016](../includes/ssrs-appliesto-2016.md)] [!INCLUDE [ssrs-appliesto-not-2017](../includes/ssrs-appliesto-not-2017.md)] [!INCLUDE [ssrs-appliesto-not-pbirs](../includes/ssrs-appliesto-not-pbirs.md)]

[!INCLUDE [ssrs-previous-versions](../includes/ssrs-previous-versions.md)]

В этом разделе описаны критические изменения в службах [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]. Эти изменения могут нарушать работу приложений, скриптов или механизмов, основанных на более ранних версиях [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Такие проблемы могут возникать при обновлении либо в пользовательских скриптах или отчетах.

## <a name="security-extensions"></a>Модули безопасности

Чтобы настраиваемые модули безопасности работали с новым [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)], требуется внести некоторые изменения. Модули безопасности должны использовать интерфейс IAuthenticationExtension2.

## <a name="wmi-provider"></a>Поставщик WMI

Имя приложения [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)] изменяется с "ReportManager" на "ReportServerWebApp".

## <a name="next-steps"></a>Следующие шаги

[Изменения в работе служб SQL Server Reporting Services в SQL Server 2016](../reporting-services/behavior-changes-to-sql-server-reporting-services-in-sql-server-2016.md)  
[Новые возможности служб Reporting Services (SSRS)](../reporting-services/what-s-new-in-sql-server-reporting-services-ssrs.md)   
[Нерекомендуемые функции служб SQL Server Reporting Services в SQL Server 2016](../reporting-services/deprecated-features-in-sql-server-reporting-services-ssrs.md)    
[Неподдерживаемые возможности в SQL Server Reporting Services в SQL Server 2016](../reporting-services/discontinued-functionality-to-sql-server-reporting-services-in-sql-server.md)  

Остались вопросы? [Посетите форум служб Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231).
