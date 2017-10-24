---
title: "Интеграция службы Reporting Services в приложения | Документы Microsoft"
ms.custom: 
ms.date: 10/19/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: e20b96e38f798c19a74d5f3a32a25e429dc8ebeb
ms.openlocfilehash: 26e1da5a720aab965d014cada16f85086e0f70a0
ms.contentlocale: ru-ru
ms.lasthandoff: 10/20/2017

---
# <a name="integrating-reporting-services-into-applications"></a>Интеграция служб Reporting Services в приложения

[!INCLUDE [ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016](../../includes/ssrs-appliesto-2016.md)] [!INCLUDE[ssrs-appliesto-not-2017](../../includes/ssrs-appliesto-not-2017.md)] [!INCLUDE [ssrs-appliesto-not-pbirs](../../includes/ssrs-appliesto-not-pbirs.md)]

  Службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] представляют собой открытую и расширяемую платформу создания отчетов, которая позволяет предоставить разработчикам всеобъемлющий набор API для разработки решений.

> [!NOTE]
> Начиная с SQL Server 2017 г. Reporting Services, доступ к REST API доступен для разработки решений. Доступ к SOAP API является устаревшим. Дополнительные сведения см. в разделе [разработка с помощью API REST для служб Reporting Services](../developer/rest-api.md).
  
 Существует три способа интеграции [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в пользовательские приложения: сервер отчетов веб-службы, также известный как [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] API-Интерфейс SOAP, элементы управления ReportViewer для [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]и URL-адресов. В каждом из этих вариантов реализуется отдельный подход к интеграции служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в приложения.
  
## <a name="report-server-web-service"></a>Веб-служба сервера отчетов

 Веб-служба сервера отчетов является основным интерфейсом разработки приложений служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Эта веб-служба предоставляет все необходимые методы для интеграции служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в приложения, независимо от того, ведется ли разработка кода для управления каталогом отчетов или для подготовки отчетов в поддерживаемом формате. Примером такого приложения является диспетчер отчетов, который входит в состав [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]; он использует веб-службы для управления базой данных сервера отчетов.  
  
## <a name="reportviewer-controls-for-visual-studio"></a>Элементы управления ReportViewer для Visual Studio

 Элементы управления ReportViewer, доступными для [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] используются для интеграции средств просмотра отчетов в приложения. Имеется два элемента управления: один для приложений на основе Windows Forms, а другой — для приложений Web Forms. Каждый элемент управления обеспечивает возможность просмотра отчетов, развернутых на сервере отчетов, а также возможность отображения отчетов, существующих в среде, где сервер отчетов пока еще не установлен.  
  
## <a name="url-access"></a>доступ по URL-адресу  
 Доступ по URL-адресу представляет собой еще один метод интеграции средств просмотра отчетов в приложения; он используется в случаях, когда применение элементов управления ReportViewer не представляется возможным. Метод доступа по URL-адресу также позволяет отправлять пользователям ссылки на отчеты по электронной почте.  
  
## <a name="in-this-section"></a>В этом разделе

 [Интеграция служб Reporting Services с использованием протокола SOAP](../../reporting-services/application-integration/integrating-reporting-services-using-soap.md)  
 Описывает способ интеграции средств навигации по отчетам и управления отчетами служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в существующие бизнес-приложения с помощью веб-службы сервера отчетов.  
  
 [Интеграция служб Reporting Services с помощью элементов управления ReportViewer](../../reporting-services/application-integration/integrating-reporting-services-using-reportviewer-controls.md)  
 Описывает способ интеграции средств просмотра отчетов в существующие приложения с помощью элементов управления ReportViewer.  
  
 [Интеграция служб Reporting Services с использованием URL-адресов](../../reporting-services/application-integration/integrating-reporting-services-using-url-access.md)  
 Описывает способ интеграции средств навигации по отчетам служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в существующие бизнес-приложения с помощью доступа по URL-адресу.  
  
## <a name="next-steps"></a>Следующие шаги

Выбор с помощью URL-адресов или API-интерфейс SOAP, в разделе [Выбор между URL-адресов и SOAP в службах Reporting Services](choosing-between-url-access-and-soap.md).

Сведения о SQL Server 2017 г REST API служб Reporting Services см. в разделе [разработка с помощью API REST для служб Reporting Services](../developer/rest-api.md).

Остались вопросы? [Посетите форум служб Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231).
