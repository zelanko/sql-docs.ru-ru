---
title: "Реализация модуля обработки данных | Документы Microsoft"
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
- custom data processing extensions [Reporting Services]
- data sources [Reporting Services], data processing extensions
- data processing extensions [Reporting Services]
- extensions [Reporting Services], data processing
ms.assetid: 8dc2b44e-5ad9-411d-a29f-7213e29321a9
caps.latest.revision: 35
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: 1497690ebccc010601542308747240d0e91d89db
ms.contentlocale: ru-ru
ms.lasthandoff: 08/12/2017

---
# <a name="implementing-a-data-processing-extension"></a>Реализация модуля обработки данных
  Модули обработки данных в службах [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] позволяют соединяться с источником данных и получать данные. Они также служат мостом между источником данных и набором данных. [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]модули обработки данных моделируются подмножество [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] интерфейсов поставщиков данных.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Общие сведения о модулях обработки данных](../../../reporting-services/extensions/data-processing/data-processing-extensions-overview.md)  
 Введение в процесс написания пользовательского модуля обработки данных для служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].  
  
 [Подготовка к реализации модуля обработки данных](../../../reporting-services/extensions/data-processing/preparing-to-implement-a-data-processing-extension.md)  
 Описываются интерфейсы, доступные при внедрении модуля обработки данных служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], а также сроки, в которые необходимо произвести внедрение определенных интерфейсов.  
  
 [Создание библиотеки модулей обработки данных](../../../reporting-services/extensions/data-processing/creating-a-data-processing-extension-library.md)  
 Описывается процесс присвоения пространства имен модулю обработки данных служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] и процесс компиляции модуля обработки данных в DLL-библиотеку.  
  
 [Реализация класса Connection для модуля обработки данных](../../../reporting-services/extensions/data-processing/implementing-a-connection-class-for-a-data-processing-extension.md)  
 Описывает атрибуты соединения и методы реализации собственного **подключения** класс для модуля обработки данных.  
  
 [Реализация класса Command для модуля обработки данных](../../../reporting-services/extensions/data-processing/implementing-a-command-class-for-a-data-processing-extension.md)  
 Описываются атрибуты команды и способы реализации собственного **команда** класс для модуля обработки данных.  
  
 [Реализация класса DataReader для модуля обработки данных](../../../reporting-services/extensions/data-processing/implementing-a-datareader-class-for-a-data-processing-extension.md)  
 Описывает атрибуты модуля чтения данных и способ реализации собственного **DataReader** класс для модуля обработки данных.  
  
 [С помощью внешнего набора данных со службами Reporting Services](../../../reporting-services/extensions/data-processing/using-an-external-dataset-with-reporting-services.md)  
 Описывает способ предоставления созданных **DataSet** объекты на сервере отчетов для использования.  
  
 [Развертывание модуля обработки данных](../../../reporting-services/extensions/data-processing/deploying-a-data-processing-extension.md)  
 Описывается процесс развертывания модуля обработки данных.  
  
 [Отладка кода модуля обработки данных](../../../reporting-services/extensions/data-processing/debugging-data-processing-extension-code.md)  
 Описывается процесс отладки кода модулей обработки данных.  
  
 [Удаление модуля обработки данных](../../../reporting-services/extensions/data-processing/removing-a-data-processing-extension.md)  
 Описывается процесс удаления модуля обработки данных из сервера отчетов или из конструктора отчетов.  
  
 Образец полностью реализованного модуля обработки данных см. в разделе [SQL Server Reporting Services Product Samples](http://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="see-also"></a>См. также:  
 [Модули служб Reporting Services](../../../reporting-services/extensions/reporting-services-extensions.md)   
 [Библиотека служб Reporting Services расширения](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  

