---
title: "Редактор преобразования &#171;Уточняющий запрос&#187; (страница &#171;Дополнительно&#187;) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.lookuptransformation.advanced.f1"
helpviewer_keywords: 
  - "редактор преобразования «Уточняющий запрос»"
ms.assetid: f3395c65-0320-47f9-8d83-daaa082d8713
caps.latest.revision: 42
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 42
---
# Редактор преобразования &#171;Уточняющий запрос&#187; (страница &#171;Дополнительно&#187;)
  Используйте вкладку **Дополнительно** диалогового окна **Редактор преобразования «Уточняющий запрос»** для настройки частичного кэширования и для изменения инструкции SQL для преобразования «Уточняющий запрос».  
  
 Дополнительные сведения о преобразовании «Уточняющий запрос» см. в разделе [Lookup Transformation](../../../integration-services/data-flow/transformations/lookup-transformation.md).  
  
## Параметры  
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
>  Дополнительная инструкция SQL, которую можно указать на этой странице, заменяет имя таблицы, указанное на странице **Соединение** **Редактора преобразования «Уточняющий запрос»**. Дополнительные сведения см. в разделе [Редактор преобразования "Уточняющий запрос" (страница "Соединение")](../../../integration-services/data-flow/transformations/lookup-transformation-editor-connection-page.md).  
  
 **Задать параметры**  
 Сопоставить входные столбцы с параметрами, используя диалоговое окно **Установка параметров запроса**.  
  
## Внешние ресурсы  
 Запись в блоге [Режимы кэша уточняющих запросов](http://go.microsoft.com/fwlink/?LinkId=219518) на сайте blogs.msdn.com  
  
## См. также  
 [Редактор преобразования "Уточняющий запрос" (страница "Общие")](../../../integration-services/data-flow/transformations/lookup-transformation-editor-general-page.md)   
 [Редактор преобразования "Уточняющий запрос" (страница "Соединение")](../../../integration-services/data-flow/transformations/lookup-transformation-editor-connection-page.md)   
 [Редактор преобразования "Уточняющий запрос" (страница "Столбцы")](../../../integration-services/data-flow/transformations/lookup-transformation-editor-columns-page.md)   
 [Редактор преобразования "Уточняющий запрос" (страница "Вывод ошибок")](../../../integration-services/data-flow/transformations/lookup-transformation-editor-error-output-page.md)   
 [Справочник по сообщениям об ошибках служб Integration Services](../../../integration-services/integration-services-error-and-message-reference.md)   
 [Преобразование «Нечеткий уточняющий запрос»](../../../integration-services/data-flow/transformations/fuzzy-lookup-transformation.md)  
  
  