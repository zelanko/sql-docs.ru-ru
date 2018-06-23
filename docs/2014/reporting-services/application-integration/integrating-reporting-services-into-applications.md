---
title: Интеграция служб Reporting Services в приложения | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- integrating reports [Reporting Services]
- custom applications [SSRS]
- Reporting Services, application integration
- application integration [Reporting Services]
- reports [Reporting Services], integrating
ms.assetid: 49eb539c-d89b-4291-839a-0ec1a65cd270
caps.latest.revision: 56
author: douglaslM
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 3a27e580a6558b6574b1bdb166f6bdbfb250f01c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36087077"
---
# <a name="integrating-reporting-services-into-applications"></a>Интеграция служб Reporting Services в приложения
  Службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] представляют собой открытую и расширяемую платформу создания отчетов, которая позволяет предоставить разработчикам всеобъемлющий набор API для разработки решений.  
  
 Предусмотрены три способа интеграции служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в пользовательские приложения: веб-служба сервера отчетов, которую также называют SOAP API [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], элементы управления ReportViewer для [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)] и средства доступа по URL-адресу. В каждом из этих вариантов реализуется отдельный подход к интеграции служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в приложения.  
  
## <a name="report-server-web-service"></a>веб-служба сервера отчетов  
 Веб-служба сервера отчетов является основным интерфейсом разработки приложений служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Эта веб-служба предоставляет все необходимые методы для интеграции служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в приложения, независимо от того, ведется ли разработка кода для управления каталогом отчетов или для подготовки отчетов в поддерживаемом формате. Примером такого приложения может служить диспетчер отчетов, входящий в комплект поставки службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]; в нем веб-служба используется для управления базой данных сервера отчетов.  
  
## <a name="reportviewer-controls-for-visual-studio"></a>Элементы управления ReportViewer для Visual Studio  
 Элементы управления ReportViewer, включенные в состав [!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)], используются для интеграции средств просмотра отчетов в приложения. Имеется два элемента управления: один для приложений на основе Windows Forms, а другой — для приложений Web Forms. Каждый элемент управления обеспечивает возможность просмотра отчетов, развернутых на сервере отчетов, а также возможность отображения отчетов, существующих в среде, где сервер отчетов пока еще не установлен.  
  
## <a name="url-access"></a>Доступ по URL-адресу  
 Доступ по URL-адресу представляет собой еще один метод интеграции средств просмотра отчетов в приложения; он используется в случаях, когда применение элементов управления ReportViewer не представляется возможным. Метод доступа по URL-адресу также позволяет отправлять пользователям ссылки на отчеты по электронной почте.  
  
## <a name="in-this-section"></a>в этом разделе  
 [Интеграция служб Reporting Services с использованием протокола SOAP](../application-integration/integrating-reporting-services-using-soap.md)  
 Описывает способ интеграции средств навигации по отчетам и управления отчетами служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в существующие бизнес-приложения с помощью веб-службы сервера отчетов.  
  
 [Интеграция служб Reporting Services с помощью элементов управления ReportViewer](../application-integration/integrating-reporting-services-using-reportviewer-controls.md)  
 Описывает способ интеграции средств просмотра отчетов в существующие приложения с помощью элементов управления ReportViewer.  
  
 [Интеграция служб Reporting Services с использованием URL-адресов](../application-integration/integrating-reporting-services-using-url-access.md)  
 Описывает способ интеграции средств навигации по отчетам служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в существующие бизнес-приложения с помощью доступа по URL-адресу.  
  
## <a name="see-also"></a>См. также  
 [Диспетчер отчетов &#40;собственный режим служб SSRS&#41;](../../../2014/reporting-services/report-manager-ssrs-native-mode.md)   
 [Выбор между URL-адресов и SOAP](../../../2014/reporting-services/application-integration/choosing-between-url-access-and-soap.md)   
 [Технический справочник (службы SSRS)](../../../2014/reporting-services/technical-reference-ssrs.md)   
 [Веб-службы сервера отчетов](../report-server-web-service/report-server-web-service.md)  
  
  