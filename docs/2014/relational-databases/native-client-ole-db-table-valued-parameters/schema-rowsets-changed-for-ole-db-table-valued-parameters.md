---
title: Наборы строк схемы, измененные для возвращающих табличное значение параметров OLE DB | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- schema rowsets [OLE DB]
- table-valued parameters (OLE DB), schema rowsets changed for (OLE DB)
ms.assetid: 581e3ead-53db-44da-8718-f3fc4b5108f1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ff0086d6b8c724ef83575cde387217ad69549d56
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63213858"
---
# <a name="schema-rowsets-changed-for-ole-db-table-valued-parameters"></a>Наборы строк схемы, измененные для возвращающих табличное значение параметров OLE DB
  Далее приведены наборы строк схемы, измененные или добавленные для поддержки возвращающих табличные значения параметров.  
  
|Набор строк схемы|Описание|  
|-------------------|-----------------|  
|DBSCHEMA_PROCEDURE_PARAMETERS|В конец набора строк были добавлены два новых столбца с именами SS_TYPE_CATALOG_NAME и SS_TYPE_SCHEMANAME. Эти столбцы можно повторно использовать для будущих типов. Столбцы TYPE_NAME и LOCAL_TYPE_NAME содержат имя возвращающего табличное значение параметра типа TABLE. Столбец DATA_TYPE для возвращающих табличные значения параметров принимает значение DBTYPE_TABLE = 143.|  
|DBSCHEMA_TABLE_TYPES|Этот набор строк был добавлен для поддержки возвращающих табличное значение параметров. Он аналогичен набору строк DBSCHEMA_TABLES, за исключением того, что возвращает метаданные только для табличных типов, а не для таблиц, представлений или синонимов. Столбец TABLE_TYPE принимает значение TABLE TYPE.|  
|DBSCHEMA_TABLE_TYPE_PRIMARY_KEYS|Этот набор строк был добавлен для поддержки возвращающих табличное значение параметров. Он аналогичен набору строк DBSCHEMA_PRIMARY_KEYS, за исключением того, что возвращает метаданные первичных ключей только для табличных типов, а не для таблиц.|  
|DBSCHEMA_TABLE_TYPE_COLUMNS|Этот набор строк был добавлен для поддержки возвращающих табличное значение параметров. Он аналогичен набору строк DBSCHEMA_COLUMNS, за исключением того, что возвращает метаданные столбцов только для табличных типов, а не для таблиц, представлений или синонимов.|  
  
## <a name="see-also"></a>См. также  
 [Возвращающие табличные значения параметры &#40;OLE DB&#41;](table-valued-parameters-ole-db.md)   
 [Использование возвращающих табличные значения параметров &#40;OLE DB&#41;](../native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
