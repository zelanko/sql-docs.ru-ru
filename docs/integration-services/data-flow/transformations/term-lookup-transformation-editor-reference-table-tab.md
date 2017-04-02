---
title: "Редактор преобразования &#171;Уточняющий запрос терминов&#187; (вкладка &#171;Ссылочная таблица&#187;) | Microsoft Docs"
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
  - "sql13.dts.designer.termlookup.referencetable.f1"
helpviewer_keywords: 
  - "редактор преобразования «Уточняющий запрос термина»"
ms.assetid: 86ccec6d-615b-4f84-9226-ff80d8012f17
caps.latest.revision: 27
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 27
---
# Редактор преобразования &#171;Уточняющий запрос терминов&#187; (вкладка &#171;Ссылочная таблица&#187;)
  Вкладка **Ссылочная таблица** диалогового окна **Редактор преобразования "Уточняющий запрос термина"** используется для установки соединения со ссылочной таблицей (таблицей уточняющих запросов).  
  
 Дополнительные сведения о преобразовании «Уточняющий запрос термина» см. в разделе [Term Lookup Transformation](../../../integration-services/data-flow/transformations/term-lookup-transformation.md).  
  
## Параметры  
 **диспетчер соединений OLE DB**  
 Выберите из списка существующий диспетчер соединений или создайте новое соединение, нажав кнопку **Создать**.  
  
 **Создать**  
 Позволяет создать новое соединение с помощью диалогового окна **Настройка диспетчера соединений OLE DB**.  
  
 **Имя ссылочной таблицы**  
 Позволяет выбрать таблицу или представление уточняющих запросов из базы данных путем выбора элемента из списка. Таблица или представление должны содержать столбец с существующим списком терминов, с которыми можно сравнивать текст исходного столбца.  
  
 **Настройка вывода ошибок**  
 Используйте диалоговое окно [Настройка вывода ошибок](../Topic/Configure%20Error%20Output.md) для указания параметров обработки ошибок для строк, вызвавших ошибку.  
  
## См. также  
 [Справочник по сообщениям об ошибках служб Integration Services](../../../integration-services/integration-services-error-and-message-reference.md)   
 [Редактор преобразований "Уточняющий запрос термина" (вкладка "Уточняющий запрос термина")](../../../integration-services/data-flow/transformations/term-lookup-transformation-editor-term-lookup-tab.md)   
 [Редактор преобразования "Уточняющий запрос термина" (вкладка "Дополнительно")](../../../integration-services/data-flow/transformations/term-lookup-transformation-editor-advanced-tab.md)   
 [Преобразование «Извлечение терминов»](../../../integration-services/data-flow/transformations/term-extraction-transformation.md)  
  
  