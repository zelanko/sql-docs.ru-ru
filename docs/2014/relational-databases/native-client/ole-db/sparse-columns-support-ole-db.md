---
title: Поддержка разреженных столбцов (OLE DB) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 918574b3-c62e-4937-9e5f-37310dedc8f9
caps.latest.revision: 16
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: bce02bc96e47ac824d1e95c86abaa6fcf47fef21
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36190750"
---
# <a name="sparse-columns-support-ole-db"></a>Поддержка разреженных столбцов (OLE DB)
  В этом разделе приводятся сведения о поддержке разреженных столбцов поставщиком OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Дополнительные сведения о разреженных столбцах см. в разделе [Поддержка разреженных столбцов в собственном клиенте SQL Server](../features/sparse-columns-support-in-sql-server-native-client.md). Пример см. в разделе [отображение метаданных столбца и каталога для разреженных столбцов &#40;OLE DB&#41;](../../native-client-ole-db-how-to/display-column-and-catalog-metadata-for-sparse-columns-ole-db.md).  
  
## <a name="ole-db-statement-metadata"></a>Метаданные инструкции OLE DB  
 В версии [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] появилось новое значение DBCOLUMNFLAGS_SS_ISCOLUMNSET флага DBCOLUMNFLAGS. Это значение должно задаваться для столбцов со значениями `column_set`. Флаг DBCOLUMNFLAGS можно извлечь с помощью *dwFlags* параметр IColumnsInfo::GetColumnsInfo и DBCOLUMN_FLAGS столбца набора строк, возвращенных IColumnsRowset::GetColumnsRowset.  
  
## <a name="ole-db-catalog-metadata"></a>Метаданные каталога OLE DB  
 В DBSCHEMA_COLUMNS были добавлены два дополнительных столбца, специфичных для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
|Имя столбца|Тип данных|Значения/комментарии|  
|-----------------|---------------|---------------------|  
|SS_IS_SPARSE|DBTYPE_BOOL|Если столбец является разреженным, то значение VARIANT_TRUE. В противном случае — значение VARIANT_FALSE.|  
|SS_IS_COLUMN_SET|DBTYPE_BOOL|Если столбец является разреженным столбцом `column_set`, то значение VARIANT_TRUE. В противном случае — значение VARIANT_FALSE.|  
  
 Кроме этого, были добавлены два дополнительных набора строк схемы. Эти наборы строк имеют ту же структуру, что и DBSCHEMA_COLUMNS, но возвращают другое содержимое. DBSCHEMA_COLUMNS_EXTENDED возвращает все столбцы, независимо от членства в `column_set`. DBSCHEMA_SPARSE_COLUMN_SET возвращает только те столбцы, которые являются членами разреженного `column_set`.  
  
## <a name="ole-db-datatypecompatibility-behavior"></a>Поведение OLE DB DataTypeCompatibility  
 Поведение с `DataTypeCompatibility=80` (в строке соединения) согласовано с [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] следующим образом.  
  
-   Новые наборы строк схемы невидимы; для них нет строк в наборе строк схемы.  
  
-   Новые столбцы в наборе строк COLUMNS невидимы.  
  
-   DBCOLUMNFLAGS_SS_ISCOLUMNSET не устанавливается для столбцов `column_set`.  
  
-   DBCOMPUTEMODE_NOTCOMPUTED устанавливается для столбцов `column_set`.  
  
## <a name="ole-db-support-for-sparse-columns"></a>Поддержка разреженных столбцов в OLE DB  
 Для поддержки разреженных столбцов были изменены следующие интерфейсы OLE DB в собственном клиенте [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
|Тип или функция-элемент|Описание|  
|-----------------------------|-----------------|  
|IColumnsInfo::GetColumnsInfo|Новый DBCOLUMNFLAGS флаг значение DBCOLUMNFLAGS_SS_ISCOLUMNSET для `column_set` столбцы в *dwFlags*.<br /><br /> Значение DBCOLUMNFLAGS_WRITE устанавливается для столбцов `column_set`.|  
|IColumsRowset::GetColumnsRowset|Новое значение DBCOLUMNFLAGS_SS_ISCOLUMNSET флага DBCOLUMNFLAGS задается для столбцов `column_set` в DBCOLUMN_FLAGS.<br /><br /> DBCOLUMN_COMPUTEMODE устанавливается в значение DBCOMPUTEMODE_DYNAMIC для столбцов `column_set`.|  
|IDBSchemaRowset::GetSchemaRowset|DBSCHEMA_COLUMNS возвращает два новых столбца: SS_IS_COLUMN_SET и SS_IS_SPARSE.<br /><br /> DBSCHEMA_COLUMNS возвращает только те столбцы, которые не являются членами `column_set`.<br /><br /> Были добавлены два новых набора строк схемы: DBSCHEMA_COLUMNS_EXTENDED возвращает все столбцы, независимо от разреженности `column_set` членства. DBSCHEMA_SPARSE_COLUMN_SET возвращает только те столбцы, которые являются членами столбца `column_set`. Новые наборы строк содержат те же столбцы и ограничения, что и DBSCHEMA_COLUMNS.|  
|IDBSchemaRowset::GetSchemas|IDBSchemaRowset::GetSchemas содержит идентификаторы GUID для новых наборов строк DBSCHEMA_COLUMNS_EXTENDED и DBSCHEMA_SPARSE_COLUMN_SET в списке доступных наборов строк схемы.|  
|ICommand::Execute|Если **выберите \* из** *таблицы* — используется, он возвращает все столбцы, которые не являются членами разреженного `column_set`, плюс XML-столбец, содержащий значения всех непустых столбцов членами разреженного `column_set`, если он существует.|  
|IOpenRowset::OpenRowset|IOpenRowset::OpenRowset возвращает набор строк с теми же столбцами, как ICommand::Execute, с **выберите \***  запросов в одной таблице.|  
|ITableDefinition|Этот интерфейс не изменился для разреженных столбцов или столбцов `column_set`. Приложения, которым необходимо изменить схему, должны выполнить соответствующий код [!INCLUDE[tsql](../../../includes/tsql-md.md)] напрямую.|  
  
## <a name="see-also"></a>См. также  
 [SQL Server Native Client &#40;OLE DB&#41;](sql-server-native-client-ole-db.md)  
  
  