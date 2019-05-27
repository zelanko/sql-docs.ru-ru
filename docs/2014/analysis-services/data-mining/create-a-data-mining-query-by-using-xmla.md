---
title: Создание запроса интеллектуального анализа данных с помощью XML для Аналитики | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- content queries [DMX]
ms.assetid: 8f6b6008-006c-4792-9bd1-64c30dc3fd41
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ec69c7225d4c509d93787e667612269c4de91e23
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66085547"
---
# <a name="create-a-data-mining-query-by-using-xmla"></a>Создание запроса интеллектуального анализа данных с помощью XMLA
  С помощью объектов AMO, инструкций DMX и языка XML/A можно создавать разнообразные запросы к объектам интеллектуального анализа данных.  
  
 Язык XML необходим для связи между службами Analysis Services и всеми клиентами. Поэтому, хотя обычно гораздо проще создавать запросы к содержимому с помощью расширений интеллектуального анализа данных, запросы можно также создавать либо с помощью инструкций DISCOVER и COMMAND языка XML/A, либо с использованием клиента, поддерживающего протокол SOAP, либо создав запрос XML/A в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 В данном разделе объясняется, как использовать шаблоны XML/A, доступные в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , для создания запроса к содержимому модели интеллектуального анализа данных, хранящейся на текущем сервере.  
  
## <a name="querying-data-mining-schema-rowsets-by-using-xmla"></a>Создание запроса к набору строк схемы интеллектуального анализа данных с помощью XML/A  
  
#### <a name="to-open-an-xmla-template"></a>Открытие шаблона XML/A  
  
1.  В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]в меню **Вид** выберите пункт **Обозреватель шаблонов**.  
  
2.  Щелкните значок куба, чтобы открыть шаблоны служб Analysis Services.  
  
3.  В списке категорий шаблонов раскройте пункт **XMLA**, разверните узел **Наборы строк схемы**и дважды щелкните **Выявление наборов строк схемы** , чтобы открыть шаблон в соответствующем редакторе кода.  
  
4.  В диалоговом окне **Подключиться к службам Analysis Services** введите сведения о соединении и нажмите кнопку **Соединить**. Откроется новое окно редактора запросов, отображающее содержимое шаблона **Выявление наборов строк схемы**  
  
#### <a name="to-discover-column-names-from-the-mining-model-content-schema-rowset"></a>Получение имен столбцов для набора строк схемы MINING MODEL CONTENT  
  
1.  В открытом шаблоне **Выявление наборов строк схемы** щелкните **Выполнить**.  
  
     На панели **Результаты** будет выведен список наборов строк схемы, содержащий имена наборов строк и столбцы наборов строк для всех наборов строк, доступных в данном экземпляре.  
  
2.  В **запроса** области, поместите курсор после  **\<список ограничений >** и нажмите клавишу ВВОД, чтобы добавить новую строку.  
  
3.  Поместите курсор на пустую строку и введите  **\<SchemaName > DMSCHEMA_MINING_MODEL_CONTENT\</SchemaName >**  
  
     Весь раздел ограничений теперь должен выглядеть следующим образом.  
  
     `<Restrictions>`  
  
     `<RestrictionList>`  
  
     `<SchemaName>DMSCHEMA_MINING_MODEL_CONTENT</SchemaName>`  
  
     `</RestrictionList>`  
  
     `</Restrictions>`  
  
4.  Нажмите кнопку **Выполнить**.  
  
     На панели **Результаты** отображается список имен столбцов для указанного набора строк схемы.  
  
#### <a name="to-create-a-content-query-using-the-mining-model-content-schema-rowset"></a>Создание запроса к содержимому с использованием набора строк схемы MINING MODEL CONTENT  
  
1.  В шаблоне **Выявление наборов строк схемы** измените тип запроса, изменив текст внутри тегов типа запроса.  
  
     Вместо  
  
     `<RequestType>DISCOVER_SCHEMA_ROWSETS</RequestType>`  
  
     введите следующую строку:  
  
     **\<RequestType>DMSCHEMA_MINING_MODEL_CONTENT\</RequestType>**  
  
2.  Измените список ограничений, чтобы задать имя модели интеллектуального анализа данных, добавив новое условие к списку ограничений.  
  
3.  В шаблоне поместите курсор после элемента `<Restriction List>` и нажмите клавишу ВВОД, чтобы добавить новую строку.  
  
4.  Поместите курсор в пустую строку и введите **<MODEL_NAME>Имя моей модели</MODEL_NAME>**  
  
     Весь раздел ограничений теперь должен выглядеть следующим образом.  
  
     `<Restrictions>`  
  
     `<RestrictionList>`  
  
     `<MODEL_NAME>My model name</MODEL_NAME>`  
  
     `</RestrictionList>`  
  
     `</Restrictions>`  
  
5.  Нажмите кнопку **Выполнить**.  
  
     На панели результатов выводится определение схемы и значения для заданной модели.  
  
## <a name="see-also"></a>См. также  
 [Содержимое модели интеллектуального анализа данных (службы Analysis Services — интеллектуальный анализ данных)](mining-model-content-analysis-services-data-mining.md)   
 [Data Mining Schema Rowsets](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/data-mining-schema-rowsets) 
  
  
