---
title: rsInternalError — ошибка служб Reporting Services | Документы Майкрософт
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: troubleshooting
ms.topic: conceptual
helpviewer_keywords:
- rsInternalError
ms.assetid: 52613d52-fc78-4870-93f0-7d393ab9c335
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 113321ca016042adfb2c98ef1601f5e27dbd7933
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47825912"
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
 Чтобы определить причину появления этого сообщения, просмотрите файлы журналов сервера отчетов, которые находятся в папке \Microsoft SQL Server\MSRS12.\<Имя_экземпляра>\Reporting Services\LogFiles. Дополнительные сведения см. в разделе [Файлы и источники журналов служб Reporting Services](../../reporting-services/report-server/reporting-services-log-files-and-sources.md).  
  
 Для просмотра стека вызова щелкните правой кнопкой мыши на странице, где произошла ошибка, и выберите команду **Исходный код**. Для просмотра стека вызовов необходимы разрешения администратора на том компьютере, где возникла ошибка.  
  
 Если дополнительные сведения недоступны, можно повторить попытку запроса.  
  
## <a name="internal-only"></a>Только для внутреннего использования  
  
## <a name="see-also"></a>См. также:  
 [Запуск и остановка службы сервера отчетов](../../reporting-services/report-server/start-and-stop-the-report-server-service.md)  
  
  
