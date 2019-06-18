---
title: Реализация модуля обработки данных | Документы Майкрософт
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: extensions
ms.topic: reference
helpviewer_keywords:
- custom data processing extensions [Reporting Services]
- data sources [Reporting Services], data processing extensions
- data processing extensions [Reporting Services]
- extensions [Reporting Services], data processing
ms.assetid: 8dc2b44e-5ad9-411d-a29f-7213e29321a9
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 96458c62500794d06633299da57b4eccea9810da
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63193923"
---
# <a name="implementing-a-data-processing-extension"></a>Реализация модуля обработки данных
  Модули обработки данных в службах [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] позволяют соединяться с источником данных и получать данные. Они также служат мостом между источником данных и набором данных. Модули обработки данных служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] построены на наборе интерфейсов поставщиков данных платформы [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].  
  
## <a name="in-this-section"></a>в этом разделе  
 [Общие сведения о модулях обработки данных](../../../reporting-services/extensions/data-processing/data-processing-extensions-overview.md)  
 Введение в процесс написания пользовательского модуля обработки данных для служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].  
  
 [Подготовка к реализации модуля обработки данных](../../../reporting-services/extensions/data-processing/preparing-to-implement-a-data-processing-extension.md)  
 Описываются интерфейсы, доступные при внедрении модуля обработки данных служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], а также сроки, в которые необходимо произвести внедрение определенных интерфейсов.  
  
 [Создание библиотеки модулей обработки данных](../../../reporting-services/extensions/data-processing/creating-a-data-processing-extension-library.md)  
 Описывается процесс присвоения пространства имен модулю обработки данных служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] и процесс компиляции модуля обработки данных в DLL-библиотеку.  
  
 [Реализация класса Connection для модуля обработки данных](../../../reporting-services/extensions/data-processing/implementing-a-connection-class-for-a-data-processing-extension.md)  
 Описываются атрибуты соединения и методы реализации собственного класса **Connection** для модуля обработки данных.  
  
 [Реализация класса Command для модуля обработки данных](../../../reporting-services/extensions/data-processing/implementing-a-command-class-for-a-data-processing-extension.md)  
 Описываются атрибуты команды и методы реализации собственного класса **Command** для модуля обработки данных.  
  
 [Реализация класса DataReader для модуля обработки данных](../../../reporting-services/extensions/data-processing/implementing-a-datareader-class-for-a-data-processing-extension.md)  
 Описываются атрибуты модуля чтения данных и методы реализации собственного класса **DataReader** для модуля обработки данных.  
  
 [Использование внешнего набора данных со службами Reporting Services](../../../reporting-services/extensions/data-processing/using-an-external-dataset-with-reporting-services.md)  
 Описывается способ предоставления пользовательских объектов **DataSet** для использования сервером отчетов.  
  
 [Развертывание модуля обработки данных](../../../reporting-services/extensions/data-processing/deploying-a-data-processing-extension.md)  
 Описывается процесс развертывания модуля обработки данных.  
  
 [Отладка кода модуля обработки данных](../../../reporting-services/extensions/data-processing/debugging-data-processing-extension-code.md)  
 Описывается процесс отладки кода модулей обработки данных.  
  
 Образец полностью реализованного модуля обработки данных см. на странице [Образцы продуктов служб SQL Server Reporting Services](https://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="see-also"></a>См. также:  
 [Модули служб Reporting Services](../../../reporting-services/extensions/reporting-services-extensions.md)   
 [Библиотека модулей Reporting Services](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
