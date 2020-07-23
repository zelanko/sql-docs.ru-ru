---
title: Преобразование "Импорт столбца" | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.importcolumntrans.f1
helpviewer_keywords:
- Import Column transformation [Integration Services]
- columns [Integration Services], importing
- importing data, SSIS packages
- inserting data
ms.assetid: ac3b74c1-ef54-4297-8062-1734324fffcc
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1db13057275f9a255ad247bd5f86ca35d7bd29d3
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/22/2020
ms.locfileid: "86919278"
---
# <a name="import-column-transformation"></a>Преобразование «Импорт столбца»

[!INCLUDE[sqlserver-ssis](../../../includes/applies-to-version/sqlserver-ssis.md)]


  Преобразование «Импорт столбца» считывает данные из файлов и добавляет данные в столбцы потока данных. С помощью этого преобразования пакет может добавлять в поток данных текст и изображения, хранимые в отдельных файлах. Например, поток данных, загружающий данные в таблицу сведений о продуктах, может содержать преобразование «Импорт столбца», чтобы выполнять импорт отзывов покупателей о каждом продукте из файлов и добавлять обзоры в поток данных.  
  
 Можно настроить преобразование «Импорт столбца» следующим образом:  
  
-   Укажите столбцы, в которые преобразование добавляет данные.  
  
-   Укажите, ожидает ли преобразование отметку порядка байтов (BOM).  
  
    > [!NOTE]  
    >  Отметка порядка байтов предполагается, только если данные принадлежат к типу данных DT_NTEXT.  
  
 Столбец входа преобразования содержит имена файлов, в которых хранятся данные. Каждая строка в наборе данных может указывать на отдельный файл. Когда преобразование «Импорт столбца» обрабатывает строку, оно считывает имя файла, открывает соответствующий файл в файловой системе и загружает содержимое файла в выходной столбец. Тип данных выходного столбца должен быть DT_TEXT, DT_NTEXT или DT_IMAGE. Дополнительные сведения см. в разделе [Integration Services Data Types](../../../integration-services/data-flow/integration-services-data-types.md).  
  
 Это преобразование имеет один вход, один выход и один выход ошибок.  
  
## <a name="configuration-of-the-import-column-transformation"></a>Настройка преобразования «Импорт столбца»  
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../../includes/ssis-md.md)] или программными средствами.  
  
 Диалоговое окно **Расширенный редактор** содержит свойства, которые можно установить с помощью программных средств. Дополнительные сведения о свойствах, которые вы можете задать в диалоговом окне **Расширенный редактор** или программными средствами, см. в следующих разделах.  
  
-   [Общие свойства](https://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
-   [Пользовательские свойства преобразований](../../../integration-services/data-flow/transformations/transformation-custom-properties.md)  
  
## <a name="related-tasks"></a>Связанные задачи  
 Дополнительные сведения о настройке свойств компонента см. в разделе [Установление свойств компонента потока данных](../../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md).  
  
## <a name="see-also"></a>См. также:  
 [Преобразование «Экспорт столбца»](../../../integration-services/data-flow/transformations/export-column-transformation.md)   
 [Поток данных](../../../integration-services/data-flow/data-flow.md)   
 [Преобразования служб Integration Services](../../../integration-services/data-flow/transformations/integration-services-transformations.md)  
  
  
