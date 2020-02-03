---
title: Реализация модуля подготовки отчетов | Документы Майкрософт
ms.date: 03/16/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: extensions
ms.topic: reference
helpviewer_keywords:
- rendering extensions [Reporting Services]
- custom rendering extensions [Reporting Services]
- transformations [Reporting Services]
- extensions [Reporting Services], rendering
- rendering extensions [Reporting Services], implementing
ms.assetid: 4a5c64f5-2391-4597-ba3f-81d265b23703
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: a72144df0f560feb6da0b954cbd7053832d46c87
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "63193702"
---
# <a name="implementing-a-rendering-extension"></a>Реализация модуля подготовки отчетов
  Модуль подготовки отчетов – это компонент или модуль сервера отчетов, преобразующий данные отчета и сведения о макете в формат, определяемый устройством отображения. Службы SQL Server Reporting Services включают шесть модулей подготовки отчетов: HTML, Excel, Word, CSV или текст, XML, изображения и PDF. Можно создать дополнительные модули подготовки для создания отчетов в других форматах.  
  
> [!NOTE]  
>  Чтобы определить доступные модули подготовки отчетов, можно просмотреть список установленных модулей подготовки отчетов в файле RSReportServer.config.  
  
## <a name="in-this-section"></a>в этом разделе  
 [Общие сведения о модулях подготовки отчетов](../../../reporting-services/extensions/rendering-extension/rendering-extensions-overview.md)  
 Представляет способ написания пользовательских модулей подготовки отчетов для служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].  
  
 [Реализация интерфейса IRenderingExtension](../../../reporting-services/extensions/rendering-extension/implementing-the-irenderingextension-interface.md)  
 Описывает атрибуты модуля подготовки отчетов.  
  
 [Развертывание модуля подготовки отчетов](../../../reporting-services/extensions/rendering-extension/deploying-a-rendering-extension.md)  
 Описывает способ развертывания модуля подготовки отчетов на сервере отчетов.  
  
 [Удаление модуля подготовки отчетов](../../../reporting-services/extensions/rendering-extension/removing-a-rendering-extension.md)  
 Описывает способ удаления модуля подготовки отчетов с сервера отчетов.  
  
## <a name="see-also"></a>См. также:  
 [Модули служб Reporting Services](../../../reporting-services/extensions/reporting-services-extensions.md)   
 [Библиотека модулей Reporting Services](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
