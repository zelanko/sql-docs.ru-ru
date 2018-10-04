---
title: Реализация модуля обработки данных | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.topic: reference
helpviewer_keywords:
- custom data processing extensions [Reporting Services]
- data sources [Reporting Services], data processing extensions
- data processing extensions [Reporting Services]
- extensions [Reporting Services], data processing
ms.assetid: 8dc2b44e-5ad9-411d-a29f-7213e29321a9
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 919f77d0f2295091133203de2474cf81a070d956
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48162194"
---
# <a name="implementing-a-data-processing-extension"></a>Реализация модуля обработки данных
  Модули обработки данных в службах [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] позволяют соединяться с источником данных и получать данные. Они также служат мостом между источником данных и набором данных. Модули обработки данных служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] построены на наборе интерфейсов поставщиков данных платформы [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].  
  
## <a name="in-this-section"></a>в этом разделе  
 [Общие сведения о модулях обработки данных](data-processing-extensions-overview.md)  
 Введение в процесс написания пользовательского модуля обработки данных для служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].  
  
 [Подготовка к реализации модуля обработки данных](preparing-to-implement-a-data-processing-extension.md)  
 Описываются интерфейсы, доступные при внедрении модуля обработки данных служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], а также сроки, в которые необходимо произвести внедрение определенных интерфейсов.  
  
 [Создание библиотеки модулей обработки данных](creating-a-data-processing-extension-library.md)  
 Описывается процесс присвоения пространства имен модулю обработки данных служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] и процесс компиляции модуля обработки данных в DLL-библиотеку.  
  
 [Реализация класса Connection для модуля обработки данных](implementing-a-connection-class-for-a-data-processing-extension.md)  
 Описываются атрибуты соединения и методы реализации собственного класса **Connection** для модуля обработки данных.  
  
 [Реализация класса Command для модуля обработки данных](implementing-a-command-class-for-a-data-processing-extension.md)  
 Описываются атрибуты команды и методы реализации собственного класса **Command** для модуля обработки данных.  
  
 [Реализация класса DataReader для модуля обработки данных](implementing-a-datareader-class-for-a-data-processing-extension.md)  
 Описываются атрибуты модуля чтения данных и методы реализации собственного класса **DataReader** для модуля обработки данных.  
  
 [Использование внешнего набора данных со службами Reporting Services](using-an-external-dataset-with-reporting-services.md)  
 Описывается способ предоставления пользовательских объектов **DataSet** для использования сервером отчетов.  
  
 [Развертывание модуля обработки данных](deploying-a-data-processing-extension.md)  
 Описывается процесс развертывания модуля обработки данных.  
  
 [Отладка кода модуля обработки данных](debugging-data-processing-extension-code.md)  
 Описывается процесс отладки кода модулей обработки данных.  
  
 [Удаление модуля обработки данных](removing-a-data-processing-extension.md)  
 Описывается процесс удаления модуля обработки данных из сервера отчетов или из конструктора отчетов.  
  
 Образец полностью реализованного модуля обработки данных см. на странице [Образцы продуктов служб SQL Server Reporting Services](http://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="see-also"></a>См. также  
 [Модули служб Reporting Services](../reporting-services-extensions.md)   
 [Библиотека модулей Reporting Services](../reporting-services-extension-library.md)  
  
  
