---
title: Export Column Transformation Editor (страница "столбцы") | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.fileextractortransformation.columns.f1
helpviewer_keywords:
- Export Column Transformation Editor
ms.assetid: b659a5c2-5509-4b5b-9c82-136c971d5c7f
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 0d5e37211471285e971ba29bc3419e759b0c7af7
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66059011"
---
# <a name="export-column-transformation-editor-columns-page"></a>Редактор преобразования «Экспорт столбца» (страница «Столбцы»)
  Страница **Столбцы** диалогового окна **Редактор преобразования «Экспорт столбца»** используется для задания столбцов в потоке данных, извлекаемых в файлы. Можно указать, будет ли преобразование «Экспорт столбца» добавлять данные в конец файла или перезаписывать существующий файл.  
  
 Дополнительные сведения о редакторе преобразований «Экспорт столбца» см. в разделе [Export Column Transformation](data-flow/transformations/export-column-transformation.md).  
  
## <a name="options"></a>Параметры  
 **Извлечь столбец**  
 Производится выбор из списка входных столбцов, содержащих текстовые данные или изображения. Все строки должны иметь определения для параметров **Извлечь столбец** и **Столбец пути к файлу**.  
  
 **Столбец пути к файлу**  
 Производится выбор из списка входных столбцов, содержащих пути к файлам и имена файлов. Все строки должны иметь определения для параметров **Извлечь столбец** и **Столбец пути к файлу**.  
  
 **Разрешить добавление**  
 Определяет, будет ли преобразование добавлять данные к существующим файлам. Значение по умолчанию — `false`.  
  
 **Принудительное усечение**  
 Определяет, будет ли преобразование удалять содержимое существующих файлов перед записью данных. Значение по умолчанию — `false`.  
  
 **Запись BOM**  
 Определяет, будет ли в файл записываться метка порядка следования байтов (BOM). Метка BOM записывается только в случае, если данные имеют тип данных `DT_NTEXT` или DT_WSTR и не присоединяются к существующему файлу данных.  
  
## <a name="see-also"></a>См. также  
 [Справочник по сообщениям об ошибках служб Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Редактор преобразования "Экспорт столбца" (страница "Вывод ошибок")](../../2014/integration-services/export-column-transformation-editor-error-output-page.md)  
  
  
