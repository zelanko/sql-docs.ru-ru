---
title: Печать отчетов из других приложений (построитель отчетов и службы SSRS) | Документы Майкрософт
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: report-builder
ms.suite: pro-bi
ms.topic: conceptual
ms.assetid: a5560581-fd57-4a45-b7ea-43b21a8a7419
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: b11bbfb6ee1c0a1557215986d38b6151adf869a8
ms.sourcegitcommit: d96b94c60d88340224371926f283200496a5ca64
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/30/2018
ms.locfileid: "43280932"
---
# <a name="print-reports-from-other-applications-report-builder-and-ssrs"></a>Печать отчетов из других приложений (построитель отчетов и службы SSRS)
  Построитель отчетов поддерживает возможность экспорта, которая позволяет просматривать отчеты в других приложениях. При открытии отчета в браузере или в веб-приложении в его верхней части появляется панель инструментов отчета, в которой доступна команда **Экспорт** . Экспорт обеспечивает просмотр отчетов в других приложениях (например, экспортированный в [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)]отчет открывается именно в этом приложении). Рекомендуется экспортировать отчет для печати только в том случае, если это дает существенные преимущества при распечатывании.  
  
 Приложение, в которое производится экспорт отчета, должно быть установлено на компьютере. Например, при экспортировании в формат Adobe Acrobat Reader (PDF) необходимо сначала установить указанное приложение. При экспортировании в формат TIFF сервер отчетов открывает полученный файл с помощью приложения для просмотра, ассоциированного с файлами указанного формата. Использование какого-либо приложения зависит от используемой версии [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows. Обычно для указанных целей используется приложение Windows Picture and Fax Viewer. По умолчанию при просмотре используется разрешение экрана 96 точек на дюйм (dpi). При использовании Windows Picture and Fax Viewer можно увеличить разрешение до 300 либо 600 dpi (в зависимости от возможностей принтера). Дополнительные сведения об изменении разрешения см. в документации по продукту Windows.  
  
 При экспортировании в формат веб-архива (более известного как MHTML) отчет открывается в программе браузера, выбранного по умолчанию. При распечатывании отчета из браузера внизу каждой страницы добавляется информация о месторасположении отчета. В большинстве случаев указанную функцию браузера добавления информации о местоположении отчета можно отключить. Дополнительные сведения см. в документации по используемому веб-браузеру.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="see-also"></a>См. также:  
 [Печать отчета (построитель отчетов и службы SSRS)](../../reporting-services/report-builder/print-a-report-report-builder-and-ssrs.md)   
 [Печать отчетов из браузера с помощью элемента управления печатью (построитель отчетов и службы SSRS)](../../reporting-services/report-builder/print-reports-from-a-browser-with-the-print-control-report-builder-and-ssrs.md)   
 [Экспорт отчетов (построитель отчетов и службы SSRS)](../../reporting-services/report-builder/export-reports-report-builder-and-ssrs.md)   
 [Экспорт отчета в файл другого типа (построитель отчетов и службы SSRS)](http://msdn.microsoft.com/library/b577568b-ecbd-44c3-be88-31dab6fc38a2)   
 [Поиск, просмотр отчетов и управление ими (построитель отчетов и службы SSRS)](../../reporting-services/report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md)  
  
  
