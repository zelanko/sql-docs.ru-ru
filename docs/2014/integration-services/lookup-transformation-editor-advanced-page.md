---
title: Редактор преобразования "Уточняющий запрос" (страница "Дополнительно") | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.lookuptransformation.advanced.f1
helpviewer_keywords:
- Lookup Transformation Editor
ms.assetid: f3395c65-0320-47f9-8d83-daaa082d8713
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 2f73f8e1e4dbbadc4b73a487d433fc8ab1913b5f
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84951234"
---
# <a name="lookup-transformation-editor-advanced-page"></a>Редактор преобразования «Уточняющий запрос» (страница «Дополнительно»)
  Используйте вкладку **Дополнительно** диалогового окна **Редактор преобразования «Уточняющий запрос»** для настройки частичного кэширования и для изменения инструкции SQL для преобразования «Уточняющий запрос».  
  
 Дополнительные сведения о преобразовании «Уточняющий запрос» см. в разделе [Lookup Transformation](data-flow/transformations/lookup-transformation.md).  
  
## <a name="options"></a>Варианты  
 **Размер кэша (32-разрядная версия)**  
 Настройте размер кэша (в мегабайтах) для 32-разрядных компьютеров. Значение по умолчанию 5.  
  
 **Размер кэша (64-разрядная версия)**  
 Настройте размер кэша (в мегабайтах) для 64-разрядных компьютеров. Значение по умолчанию 5.  
  
 **Включить кэширование для строк с несовпадающими записями**  
 Кэшировать строки без совпадающих элементов в эталонном наборе данных.  
  
 **Размещение из кэша**  
 Задать долю кэша (в процентах), которую следует выделять для строк без совпадающих элементов в эталонном наборе данных.  
  
 **Изменить инструкцию SQL**  
 Изменить инструкцию SQL, которая используется для формирования эталонного набора данных.  
  
> [!NOTE]  
>  Дополнительная инструкция SQL, которую можно указать на этой странице, заменяет имя таблицы, указанное на странице **Соединение****Редактора преобразования «Уточняющий запрос»**. Дополнительные сведения см. в разделе [Редактор преобразования "Уточняющий запрос" (страница "Соединение")](../../2014/integration-services/lookup-transformation-editor-connection-page.md).  
  
 **Задать параметры**  
 Сопоставить входные столбцы с параметрами, используя диалоговое окно **Установка параметров запроса** .  
  
## <a name="external-resources"></a>Внешние ресурсы  
 Запись в блоге [Режимы кэша уточняющих запросов](https://go.microsoft.com/fwlink/?LinkId=219518) на сайте blogs.msdn.com  
  
## <a name="see-also"></a>См. также:  
 [Редактор преобразования "Уточняющий запрос" &#40;общие&#41;страницы](general-page-of-integration-services-designers-options.md)   
 [Редактор преобразования "Уточняющий запрос" &#40;страница подключения&#41;](../../2014/integration-services/lookup-transformation-editor-connection-page.md)   
 [Редактор преобразования «Уточняющий запрос» &#40;столбцов&#41;](../../2014/integration-services/lookup-transformation-editor-columns-page.md)   
 [Редактор преобразования "Уточняющий запрос" &#40;страница "вывод ошибок"&#41;](../../2014/integration-services/lookup-transformation-editor-error-output-page.md)   
 [Справочник по ошибкам и сообщениям Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [преобразование «Нечеткий уточняющий запрос»](data-flow/transformations/fuzzy-lookup-transformation.md)  
  
  
