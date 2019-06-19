---
title: Соединение компонентов с путями | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- data flow [Integration Services], connections
- components [Integration Services], connections
- connections [Integration Services], data flow components
ms.assetid: 05633e4c-1370-4b05-802b-f36b07dd71c8
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 1a75a9717345d1d0dc4c2fe30bf7fc441cb91ddc
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66060389"
---
# <a name="connect-components-with-paths"></a>Соединение компонентов с путями
  Поток данных пакета проектируется в области конструктора на вкладке **Поток данных** конструктора служб [!INCLUDE[ssIS](../includes/ssis-md.md)] . Если поток данных содержит два компонента потока данных, можно соединить их, подключив выход источника или преобразования ко входу преобразования или назначения. Соединитель компонентов потока данных называется путем.  
  
 На следующей диаграмме показан простой поток данных с компонентом источника, двумя преобразованиями, целевым компонентом и путями, которые их соединяют.  
  
 ![Поток данных](media/mw-dts-08.gif "Поток данных")  
  
 После соединения двух компонентов можно просматривать метаданные тех данных, которые перемещаются по пути, и свойства пути в **Редакторе пути потока данных**. Дополнительные сведения см. в статье [Integration Services Paths](data-flow/integration-services-paths.md).  
  
 Также можно добавлять к путям средства просмотра данных. Средство просмотра данных дает возможность просматривать данные, перемещающиеся между компонентами потока данных во время выполнения пакета.  
  
### <a name="to-connect-components-in-a-data-flow"></a>Соединение компонентов в потоке данных  
  
-   [Соединение компонентов в потоке данных](data-flow/connect-components-in-a-data-flow.md)  
  
### <a name="to-set-path-properties"></a>Задание свойств пути  
  
-   [Задание свойств пути с помощью редактора пути потока данных](../../2014/integration-services/set-the-properties-of-a-path-by-using-the-data-flow-path-editor.md)  
  
### <a name="to-view-path-metadata"></a>Просмотр метаданных пути  
  
-   [Просмотр метаданных пути в редакторе пути потока данных](../../2014/integration-services/view-path-metadata-in-the-data-flow-path-editor.md)  
  
### <a name="to-view-path-metadata"></a>Просмотр метаданных пути  
  
-   [Добавление средства просмотра данных к потоку данных](../../2014/integration-services/add-a-data-viewer-to-a-data-flow.md)  
  
## <a name="see-also"></a>См. также  
 [Задача потока данных](control-flow/data-flow-task.md)   
 [Поток данных](data-flow/data-flow.md)   
 [Преобразование данных с помощью преобразований](data-flow/transformations/transform-data-with-transformations.md)   
 [Обработка ошибок в данных](data-flow/error-handling-in-data.md)  
  
  
