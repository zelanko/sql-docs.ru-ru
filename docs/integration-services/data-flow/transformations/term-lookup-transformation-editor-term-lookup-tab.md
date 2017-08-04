---
title: "Редактор преобразования Уточняющий запрос термина (вкладка «Уточняющий запрос» терминов) | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.termlookup.termlookup.f1
helpviewer_keywords:
- Term Lookup Transformation Editor
ms.assetid: 245d3466-d51f-4073-978a-694a8d9dfaec
caps.latest.revision: 26
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 79e7f405e9418b47985efd7bcc8bb13b14f20ec6
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="term-lookup-transformation-editor-term-lookup-tab"></a>Редактор преобразований «Уточняющий запрос термина» (вкладка «Уточняющий запрос термина»)
  Вкладка **Уточняющий запрос термина** диалогового окна **Редактор преобразования «Уточняющий запрос термина»** позволяет сопоставить входной столбец с уточняющим столбцом в ссылочной таблице и предоставить псевдоним каждому выходному столбцу.  
  
 Дополнительные сведения о преобразовании «Уточняющий запрос термина» см. в разделе [Term Lookup Transformation](../../../integration-services/data-flow/transformations/term-lookup-transformation.md).  
  
## <a name="options"></a>Параметры  
 **Доступные входные столбцы**  
 Используя флажки, выберите входные столбцы, которые не должны измениться на выходе. Перетащите входной столбец в список **Доступные ссылочные столбцы** , чтобы сопоставить его с уточняющим столбцом в ссылочной таблице. Входной столбец и уточняющий столбец должны иметь одинаковый тип данных: DT_NTEXT или DT_WSTR. Выберите строку сопоставления и щелкните ее правой кнопкой мыши, чтобы изменить ее в диалоговом окне [Создание связей](../../../integration-services/data-flow/transformations/create-relationships.md) .  
  
 **Доступные ссылочные столбцы**  
 Просмотрите список доступных столбцов в ссылочной таблице. Выберите столбец, содержащий список нужных терминов.  
  
 **Передаваемый столбец**  
 Выберите входной столбец из списка имеющихся входных столбцов. Выбранные столбцы обозначаются флажками в таблице **Доступные входные столбцы** .  
  
 **Псевдоним выходного столбца**  
 Введите псевдоним для каждого выходного столбца. По умолчанию, это имя столбца, но можно выбрать любое уникальное описательное имя.  
  
 **Настройка вывода ошибок**  
 Используйте диалоговое окно [Настройка вывода ошибок](http://msdn.microsoft.com/library/5f8da390-fab5-44f8-b268-d8fa313ce4b9) для указания параметров обработки ошибок для строк, вызвавших ошибку.  
  
## <a name="see-also"></a>См. также  
 [Справочник по сообщениям об ошибках служб Integration Services](../../../integration-services/integration-services-error-and-message-reference.md)   
 [Редактор преобразования Уточняющий запрос термина &#40; Вкладка «Ссылочная таблица» &#41;](../../../integration-services/data-flow/transformations/term-lookup-transformation-editor-reference-table-tab.md)   
 [Редактор преобразования Уточняющий запрос термина &#40; Вкладка "Дополнительно" &#41;](../../../integration-services/data-flow/transformations/term-lookup-transformation-editor-advanced-tab.md)   
 [Преобразование «Извлечение терминов»](../../../integration-services/data-flow/transformations/term-extraction-transformation.md)  
  
  
