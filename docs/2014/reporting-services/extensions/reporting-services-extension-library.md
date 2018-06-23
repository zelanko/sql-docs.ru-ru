---
title: Библиотека модулей служб Reporting Services | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- namespaces [Reporting Services]
- Reporting Services, extending
- extensions [Reporting Services], library
- library [Reporting Services]
ms.assetid: e8eff470-64d6-41c3-b98b-5ec916c121c3
caps.latest.revision: 33
author: douglaslM
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 4f7ec58e860d75a24eea2162639ba458a067f73b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36087788"
---
# <a name="reporting-services-extension-library"></a>Библиотека модулей служб Reporting Services
  Библиотека модулей служб Reporting Services — это набор классов, интерфейсов и типов значений, включенных в службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Эта библиотека предоставляет доступ к системным функциям и предназначена в качестве основы для расширения компонентов служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] с помощью приложений [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)].  
  
## <a name="namespaces"></a>Пространства имен  
 Библиотека модулей служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] содержит следующие пространства имен.  
  
 <xref:Microsoft.ReportingServices.DataProcessing>  
 Содержит классы и интерфейсы, которые позволяют строить компоненты, расширяющие возможности служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] по обработке данных.  
  
 <xref:Microsoft.ReportingServices.Interfaces>  
 Содержит классы и интерфейсы, которые позволяют создавать и отправлять пользователям нестандартные уведомления с помощью собственных модулей доставки, а также строить настраиваемые модули безопасности для служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
 `Microsoft.ReportingServices.ReportRendering`  
 Содержит классы и интерфейсы, которые позволяют расширить возможности служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] по подготовке отчетов к просмотру. С помощью элементов этого пространства имен вместе с элементами пространства имен <xref:Microsoft.ReportingServices.Interfaces> можно строить пользовательские модули подготовки отчетов для служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
## <a name="see-also"></a>См. также  
 [Модули Reporting Services](reporting-services-extensions.md)  
  
  