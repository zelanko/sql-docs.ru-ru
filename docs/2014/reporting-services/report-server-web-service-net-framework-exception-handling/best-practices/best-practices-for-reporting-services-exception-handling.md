---
title: Рекомендации по обработке исключений в службах Reporting Services | Документы Майкрософт
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
- exceptions [Reporting Services], best practices
ms.assetid: 72fecf28-f02e-4338-b50f-0b21f520302d
caps.latest.revision: 33
author: douglaslM
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 4827af143c1eca89b4873387fc4db9fd454c06c1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36188167"
---
# <a name="best-practices-for-reporting-services-exception-handling"></a>Рекомендации по обработке исключений в службах Reporting Services
  При разработке приложений служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] существует несколько методик, которые можно использовать для избежания возникновения исключений или сокращения их количества. При возникновении исключений пользователю следует выводить ясное и четкое сообщение об ошибке; кроме того, следует добавить обработку исключений, чтобы приложения не завершались неожиданно.  
  
 Приложение, посылающее запросы веб-службе сервера отчетов должно выполнять следующие действия.  
  
-   Оно должно избегать вызова исключений методом предотвращения создания как можно большего количества недопустимых запросов.  
  
-   Оно должно по возможности перехватывать исключения и предоставлять определенные коды обработки ошибок.  
  
-   Оно должно обрабатывать варианты ошибок, не выдающие исключений.  
  
## <a name="in-this-section"></a>в этом разделе  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Предотвращение использования недопустимых запросов](preventing-invalid-requests.md)|Описывает методики предотвращения отправки недопустимых запросов на сервер отчетов.|  
|[Использование блоков Try-Catch](using-try-and-catch-blocks.md)|Описывает, как можно увеличить надежность приложения с использованием блоков TRY и CATCH.|  
|[Обработка предупреждений и ситуаций, не вызывающих исключения](handling-warnings-and-cases-that-do-not-cause-exceptions.md)|Объясняет, как следует обрабатывать ошибки, которые не приводят к формированию исключения службами [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].|  
|[Использование свойства Detail для обработки определенных ошибок](using-the-detail-property-to-handle-specific-errors.md)|Описывает, как можно программным образом обрабатывать определенные ошибки с помощью свойства **Detail** объекта **SoapException**.|  
  
## <a name="see-also"></a>См. также  
 [Свойство Detail](../soapexception-class/detail-property.md)   
 [Введение в обработку исключений в службах Reporting Services](../introducing-exception-handling-in-reporting-services.md)   
 [Класс SoapException в службах Reporting Services](../soapexception-class/reporting-services-soapexception-class.md)  
  
  