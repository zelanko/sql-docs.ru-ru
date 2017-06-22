---
title: "Удаление модуля обработки данных | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
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
- deleting data processing extensions
- data processing extensions [Reporting Services], removing
- removing data processing extensions
ms.assetid: 1d89e32b-0631-44f6-8178-a57fb791d26d
caps.latest.revision: 34
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: e59120a2297617d9234dac070cb5c99b4d564d65
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="removing-a-data-processing-extension"></a>Удаление модуля обработки данных
  Чтобы удалить модуль обработки данных, просто удалите **расширения** элемент для модуля обработки данных из файла конфигурации. Если выполнены записи для сервера отчетов, а также конструктор отчетов, удалите **расширения** элемент из файла RSReportServer.config и RSReportDesigner.config файлов. После удаления сведений о конфигурации модуль обработки данных становится недоступным компоненту.  
  
## <a name="see-also"></a>См. также:  
 [модули служб Reporting Services](../../../reporting-services/extensions/reporting-services-extensions.md)   
 [Реализация модуля обработки данных](../../../reporting-services/extensions/data-processing/implementing-a-data-processing-extension.md)   
 [Библиотека служб Reporting Services расширения](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
