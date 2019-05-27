---
title: Редактор преобразования Уточняющий запрос термина (вкладка Уточняющий запрос термина) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.termlookup.termlookup.f1
helpviewer_keywords:
- Term Lookup Transformation Editor
ms.assetid: 245d3466-d51f-4073-978a-694a8d9dfaec
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 2939d160773d60944a2e8a786e5495cea366edb1
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66055130"
---
# <a name="term-lookup-transformation-editor-term-lookup-tab"></a>Редактор преобразований «Уточняющий запрос термина» (вкладка «Уточняющий запрос термина»)
  Вкладка **Уточняющий запрос термина** диалогового окна **Редактор преобразования «Уточняющий запрос термина»** позволяет сопоставить входной столбец с уточняющим столбцом в ссылочной таблице и предоставить псевдоним каждому выходному столбцу.  
  
 Дополнительные сведения о преобразовании «Уточняющий запрос термина» см. в разделе [Term Lookup Transformation](data-flow/transformations/lookup-transformation.md).  
  
## <a name="options"></a>Параметры  
 **Доступные входные столбцы**  
 Используя флажки, выберите входные столбцы, которые не должны измениться на выходе. Перетащите входной столбец в список **Доступные ссылочные столбцы** , чтобы сопоставить его с уточняющим столбцом в ссылочной таблице. Входной столбец и уточняющий столбец должны иметь одинаковый тип данных: DT_NTEXT или DT_WSTR. Выберите строку сопоставления и щелкните ее правой кнопкой мыши, чтобы изменить ее в диалоговом окне [Создание связей](data-flow/transformations/create-relationships.md) .  
  
 **Доступные ссылочные столбцы**  
 Просмотрите список доступных столбцов в ссылочной таблице. Выберите столбец, содержащий список нужных терминов.  
  
 **Передаваемый столбец**  
 Выберите входной столбец из списка имеющихся входных столбцов. Выбранные столбцы обозначаются флажками в таблице **Доступные входные столбцы** .  
  
 **Псевдоним выходного столбца**  
 Введите псевдоним для каждого выходного столбца. По умолчанию, это имя столбца, но можно выбрать любое уникальное описательное имя.  
  
 **Настройка вывода ошибок**  
 Используйте диалоговое окно [Настройка вывода ошибок](../../2014/integration-services/configure-error-output.md) для указания параметров обработки ошибок для строк, вызвавших ошибку.  
  
## <a name="see-also"></a>См. также:  
 [Справочник по сообщениям об ошибках служб Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Редактор преобразования "Уточняющий запрос термина" (вкладка "Ссылочная таблица")](../../2014/integration-services/term-lookup-transformation-editor-reference-table-tab.md)   
 [Редактор преобразования "Уточняющий запрос термина" (вкладка "Дополнительно")](../../2014/integration-services/term-lookup-transformation-editor-advanced-tab.md)   
 [Преобразование "Извлечение терминов"](data-flow/transformations/term-extraction-transformation.md)  
  
  
