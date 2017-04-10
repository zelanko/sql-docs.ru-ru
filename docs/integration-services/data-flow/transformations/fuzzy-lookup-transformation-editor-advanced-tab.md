---
title: "Редактор преобразования &#171;Нечеткий уточняющий запрос&#187; (вкладка &#171;Дополнительно&#187;) | Microsoft Docs"
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
  - "sql13.dts.designer.fuzzylookuptransformation.advanced.f1"
helpviewer_keywords: 
  - "редактор преобразования «Нечеткий уточняющий запрос»"
ms.assetid: 0a2919be-2ea7-4c06-82b8-0ffad5f0dd83
caps.latest.revision: 27
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 27
---
# Редактор преобразования &#171;Нечеткий уточняющий запрос&#187; (вкладка &#171;Дополнительно&#187;)
  Вкладка **Дополнительно** диалогового окна **Редактор преобразования «Нечеткий уточняющий запрос»** позволяет задать параметры нечеткого поиска.  
  
 Дополнительные сведения о преобразовании «Нечеткий уточняющий запрос» см. в разделе [Fuzzy Lookup Transformation](../../../integration-services/data-flow/transformations/fuzzy-lookup-transformation.md).  
  
## Параметры  
 **Максимальное количество совпадений, которое следует выводить на каждый уточняющий запрос**  
 Указывает максимальное число совпадений, возвращаемое преобразованием для каждой входной строки. Значение по умолчанию — **1**.  
  
 **Порог подобия**  
 Задает порог подобия на уровне компонента при помощи данного ползунка. Чем ближе значение к 1, тем ближе к искомому должно быть значение строки уточняющего запроса. Увеличение порогового значения может увеличить скорость соответствия, так как при этом будет рассматриваться меньшее количество предполагаемых совпадений.  
  
 **Разделители токенов**  
 Определяет разделители, используемые преобразованием для разделения значений столбца.  
  
## См. также  
 [Справочник по сообщениям об ошибках служб Integration Services](../../../integration-services/integration-services-error-and-message-reference.md)   
 [Редактор преобразования "Нечеткий уточняющий запрос" (вкладка "Ссылочная таблица")](../../../integration-services/data-flow/transformations/fuzzy-lookup-transformation-editor-reference-table-tab.md)   
 [Редактор преобразования "Нечеткий уточняющий запрос" (вкладка "Столбцы")](../../../integration-services/data-flow/transformations/fuzzy-lookup-transformation-editor-columns-tab.md)  
  
  