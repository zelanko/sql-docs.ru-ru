---
title: "Реализация модуля подготовки отчетов | Документы Microsoft"
ms.custom: 
ms.date: 03/16/2017
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
- rendering extensions [Reporting Services]
- custom rendering extensions [Reporting Services]
- transformations [Reporting Services]
- extensions [Reporting Services], rendering
- rendering extensions [Reporting Services], implementing
ms.assetid: 4a5c64f5-2391-4597-ba3f-81d265b23703
caps.latest.revision: 34
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 68e74b4a67a1edc6517c9e6b2b0160ce2db258b9
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="implementing-a-rendering-extension"></a>Реализация модуля подготовки отчетов
  Модуль подготовки отчетов – это компонент или модуль сервера отчетов, преобразующий данные отчета и сведения о макете в формат, определяемый устройством отображения. SQL Server Reporting Services включают шесть модулей подготовки отчетов: HTML, Excel, Word, CSV или текст, XML, изображения и PDF. Можно создать дополнительные модули подготовки для создания отчетов в других форматах.  
  
> [!NOTE]  
>  Чтобы определить доступные модули подготовки отчетов, можно просмотреть список установленных модулей подготовки отчетов в файле RSReportServer.config.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Общие сведения о модулях подготовки отчетов](../../../reporting-services/extensions/rendering-extension/rendering-extensions-overview.md)  
 Представляет способ написания пользовательских модулей подготовки отчетов для служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].  
  
 [Реализация интерфейса IRenderingExtension](../../../reporting-services/extensions/rendering-extension/implementing-the-irenderingextension-interface.md)  
 Описывает атрибуты модуля подготовки отчетов.  
  
 [Развертывание модуля подготовки отчетов](../../../reporting-services/extensions/rendering-extension/deploying-a-rendering-extension.md)  
 Описывает способ развертывания модуля подготовки отчетов на сервере отчетов.  
  
 [Удаление модуля подготовки отчетов](../../../reporting-services/extensions/rendering-extension/removing-a-rendering-extension.md)  
 Описывает способ удаления модуля подготовки отчетов с сервера отчетов.  
  
## <a name="see-also"></a>См. также:  
 [модули служб Reporting Services](../../../reporting-services/extensions/reporting-services-extensions.md)   
 [Библиотека служб Reporting Services расширения](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
