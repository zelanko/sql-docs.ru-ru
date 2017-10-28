---
title: "rsInternalError - ошибка службы Reporting Services | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- rsInternalError
ms.assetid: 52613d52-fc78-4870-93f0-7d393ab9c335
caps.latest.revision: 23
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.translationtype: Machine Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 7265597c2376d62b6d3e42c55c8d87e45f6d869e
ms.contentlocale: ru-ru
ms.lasthandoff: 08/09/2017

---
# <a name="rsinternalerror---reporting-services-error"></a>rsInternalError - Ошибка службы Reporting Services
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|Идентификатор события|rsInternalError|  
|Источник события|Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings|  
|Компонент|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|  
|Текст сообщения|Произошла внутренняя ошибка на сервере отчетов. Дополнительные подробности см. в журнале ошибок.|  
  
## <a name="explanation"></a>Объяснение  
 Это общее сообщение об ошибке, за которым часто следует более описательное сообщение об ошибке, предоставляющее больше сведений.  
  
 Внутренние ошибки случаются редко. При возникновении такой ошибки дополнительные сведения можно получить в журналах трассировки сервера отчетов. Помимо этого, если вы работаете на компьютере, где произошла ошибка, под учетной записью локального администратора, можно также просмотреть стек вызовов.  
  
## <a name="user-action"></a>Действие пользователя  
 Чтобы определить причину появления этого сообщения, просмотрите файлы журналов сервера отчетов, которые находятся в \Microsoft SQL Server\MSRS12. \<имя_экземпляра > \Reporting Services\LogFiles. Дополнительные сведения см. в разделе [Файлы и источники журналов служб Reporting Services](../../reporting-services/report-server/reporting-services-log-files-and-sources.md).  
  
 Для просмотра стека вызова щелкните правой кнопкой мыши на странице, где произошла ошибка, и выберите команду **Исходный код**. Для просмотра стека вызовов необходимы разрешения администратора на том компьютере, где возникла ошибка.  
  
 Если дополнительные сведения недоступны, можно повторить попытку запроса.  
  
## <a name="internal-only"></a>Только для внутреннего использования  
  
## <a name="see-also"></a>См. также  
 [Запуск и остановка службы сервера отчетов](../../reporting-services/report-server/start-and-stop-the-report-server-service.md)  
  
  

