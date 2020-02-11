---
title: Реализация модуля подготовки отчетов | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
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
manager: kfile
ms.openlocfilehash: 03deb7c818de8d875f69b585ae6015fc178e707d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62986755"
---
# <a name="implementing-a-rendering-extension"></a>Реализация модуля подготовки отчетов
  Модуль подготовки отчетов – это компонент или модуль сервера отчетов, преобразующий данные отчета и сведения о макете в формат, определяемый устройством отображения. Службы SQL Server Reporting Services включают шесть модулей подготовки отчетов: HTML, Excel, Word, CSV или текст, XML, изображения и PDF. Можно создать дополнительные модули подготовки для создания отчетов в других форматах.  
  
> [!NOTE]  
>  Чтобы определить доступные модули подготовки отчетов, можно просмотреть список установленных модулей подготовки отчетов в файле RSReportServer.config.  
  
## <a name="in-this-section"></a>в этом разделе  
 [Общие сведения о модулях подготовки отчетов](rendering-extensions-overview.md)  
 Представляет способ написания пользовательских модулей подготовки отчетов для служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].  
  
 [Реализация интерфейса IRenderingExtension](implementing-the-irenderingextension-interface.md)  
 Описывает атрибуты модуля подготовки отчетов.  
  
 [Развертывание модуля подготовки отчетов](deploying-a-rendering-extension.md)  
 Описывает способ развертывания модуля подготовки отчетов на сервере отчетов.  
  
 [Удаление модуля подготовки отчетов](removing-a-rendering-extension.md)  
 Описывает способ удаления модуля подготовки отчетов с сервера отчетов.  
  
## <a name="see-also"></a>См. также:  
 [Модули служб Reporting Services](../reporting-services-extensions.md)   
 [Библиотека модулей Reporting Services](../reporting-services-extension-library.md)  
  
  
