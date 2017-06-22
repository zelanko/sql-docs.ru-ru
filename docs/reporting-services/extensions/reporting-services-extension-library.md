---
title: "Библиотека служб Reporting Services расширения | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
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
helpviewer_keywords:
- namespaces [Reporting Services]
- Reporting Services, extending
- extensions [Reporting Services], library
- library [Reporting Services]
ms.assetid: e8eff470-64d6-41c3-b98b-5ec916c121c3
caps.latest.revision: 33
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: b9a1ce1e388575d6d5b9b46a00dbc85ae8cde84b
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="reporting-services-extension-library"></a>Библиотека модулей служб Reporting Services
  Библиотека модулей служб Reporting Services — это набор классов, интерфейсов и типов значений, включенных в службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Эта библиотека предоставляет доступ к функциональным возможностям системы и обеспечивают основу, на котором [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] приложений можно использовать для расширения [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] компонентов.  
  
## <a name="namespaces"></a>Пространства имен  
 Библиотека модулей служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] содержит следующие пространства имен.  
  
 <xref:Microsoft.ReportingServices.DataProcessing>  
 Содержит классы и интерфейсы, которые позволяют строить компоненты, расширяющие возможности служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] по обработке данных.  
  
 <xref:Microsoft.ReportingServices.Interfaces>  
 Содержит классы и интерфейсы, которые позволяют создавать и отправлять пользователям нестандартные уведомления с помощью собственных модулей доставки, а также строить настраиваемые модули безопасности для служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
 **Microsoft.ReportingServices.ReportRendering**  
 Содержит классы и интерфейсы, которые позволяют расширить возможности служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] по подготовке отчетов к просмотру. С помощью элементов этого пространства имен вместе с элементами пространства имен <xref:Microsoft.ReportingServices.Interfaces> можно строить пользовательские модули подготовки отчетов для служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
## <a name="see-also"></a>См. также:  
 [Модули служб Reporting Services](../../reporting-services/extensions/reporting-services-extensions.md)  
  
  
