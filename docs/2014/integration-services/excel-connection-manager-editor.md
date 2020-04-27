---
title: Редактор диспетчера соединений с Excel | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.excelconnection.f1
helpviewer_keywords:
- Excel Connection Manager Editor
ms.assetid: 7ff097e4-cafb-4885-a898-05b2a46628c1
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 0881624f421cba5bda5d2b0ba8f9d3732efd2497
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66059269"
---
# <a name="excel-connection-manager-editor"></a>редактор диспетчера соединений с Excel
  Диалоговое окно **Редактор диспетчера соединений с Excel** используется для добавления подключения к существующему или новому файлу книги [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] .  
  
 Дополнительные сведения о диспетчере соединений с Excel см. в разделе [Диспетчер соединений с Excel](connection-manager/excel-connection-manager.md).  
  
> [!NOTE]  
>  Подключить защищенный паролем файл Excel нельзя.  
  
## <a name="options"></a>Параметры  
 **Путь к файлу Excel**  
 Введите путь и имя существующего или нового файла книги Excel с расширением XLS.  
  
> [!WARNING]  
>  **Редактор назначения «Excel** » автоматически создает файл Excel при выборе **подключения Excel** , указывающего на новый или несуществующий файл, а затем нажмите кнопку **создать** для **имени листа Excel**.  
  
 **Обзор**  
 Используйте диалоговое окно **Открыть** , чтобы перейти в папку, в которой находится файл Excel, или в место, где нужно создать новый файл.  
  
 **Версия Excel**  
 Позволяет указать версию Microsoft Excel, в которой был создан файл.  
  
|Параметр|Описание|  
|------------|-----------------|  
|Excel 97-2003|Файл был создан с помощью Excel 97 или более поздней версии.|  
|Excel 3,0|Файл был создан с помощью Excel 3,0.|  
|Excel 4,0|Файл был создан с помощью Excel 4.0.|  
|Excel 5,0|Файл был создан с помощью Excel 95 (7.0).|  
  
 **Первая строка содержит имена столбцов**  
 Позволяет указать, содержит ли первая строка данных выбранного листа имена столбцов. По умолчанию значение этого параметра равно **True**.  
  
## <a name="see-also"></a>См. также  
 [Справочник по ошибкам и сообщениям Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Просмотр файлов и таблиц Excel с помощью контейнера "Цикл по каждому элементу"](control-flow/foreach-loop-container.md)  
  
  
