---
title: Поддержка типов табличное значение параметра OLE DB (свойства) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (OLE DB), API support (properties)
ms.assetid: b9c4e6ed-fe4f-4ef8-9bc8-784d80d44039
caps.latest.revision: 19
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: c487e6d3853eeb430b686896af279283ecdad2c6
ms.sourcegitcommit: a78fa85609a82e905de9db8b75d2e83257831ad9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2018
ms.locfileid: "35695475"
---
# <a name="ole-db-table-valued-parameter-type-support-properties"></a>Поддержка типов параметров OLE DB, возвращающих табличные значения (свойства)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  В данном разделе приводятся сведения о свойствах и наборах свойств OLE DB, связанных с объектами наборов строк для возвращающего табличное значение параметра.  
  
## <a name="properties"></a>Свойства  
 Ниже приведен список свойств, доступных через метод IRowsetInfo::GetPropeties для объектов набора строк возвращающего табличное значение параметра. Следует заметить, что все свойства объектов наборов строк для возвращающего табличное значение параметра неизменяемы. Таким образом попытка задать любой свойств через IOpenRowset::OpenRowset или ITableDefinitionWithConstraints::CreateTableWithConstraints способы их значения по умолчанию вызовет ошибку и не будет создать объект.  
  
 Свойства, не реализованные в объекте наборов строк для возвращающего табличное значение параметра, здесь не перечислены. Полный набор свойств можно найти в документации по OLE DB в разделе, посвященном компонентам доступа к данным Windows.  
  
|Идентификатор свойства|Значение|  
|-----------------|-----------|  
|DBPROP_ABORTPRESERVE|VARIANT_TRUE|  
|DBPROP_ACCESSORDER|DBPROPVAL_AO_RANDOM|  
|DBPROP_BLOCKINGSTORAGEOBJECTS|VARIANT_TRUE|  
|DBPROP_BOOKMARKS<br /><br /> DBPROP_LITERALBOOKMARKS|R Чтение и запись: только для чтения<br /><br /> По умолчанию: значение VARIANT_FALSE<br /><br /> Описание: Закладки не разрешены для объектов набора строк возвращающего табличное значение параметра.|  
|DBPROP_BOOKMARKSKIPPED|VARIANT_FALSE|  
|DBPROP_BOOKMARKTYPE|DBPROPVAL_BMK_NUMERIC|  
|DBPROP_CANHOLDROWS|VARIANT_FALSE|  
|DBPROP_CHANGEINSERTEDROWS|VARIANT_TRUE|  
|DBPROP_COLUMNRESTRICT|VARIANT_FALSE|  
|DBPROP_COMMANDTIMEOUT|0|  
|DBPROP_COMMITPRESERVE|VARIANT_TRUE|  
|DBPROP_DEFERRED|VARIANT_FALSE|  
|DBPROP_DELAYSTORAGEOBJECTS|VARIANT_FALSE|  
|DBPROP_IAccessor<br /><br /> DBPROP_IColumnsInfo<br /><br /> DBPROP_IConvertType<br /><br /> DBPROP_IRowset<br /><br /> DBPROP_IRowsetInfo,<br /><br /> DBPROP_IColumnsRowset|VARIANT_TRUE|  
|DBPROP_IConnectionPointContainer<br /><br /> DBPROP_IMultipleResults<br /><br /> DBPROP_IRowsetUpdate<br /><br /> DBPROP_IRowsetIdentity<br /><br /> DBPROP_IRowsetLocate<br /><br /> DBPROP_IRowsetScroll<br /><br /> DBPROP_IRowsetResynch|VARIANT_FALSE|  
|DBPROP_IRowsetChange|VARIANT_TRUE<br /><br /> Примечание: В объекте набора строк возвращающего табличное значение параметра поддерживает интерфейсы IRowsetChange.<br /><br /> Набор строк, созданный с DBPROP_IRowsetChange, равным VARIANT_TRUE, отражает режимы немедленного обновления.<br /><br /> Тем не менее если столбцы типа BLOB привязаны как объекты ISequentialStream, потребитель должно остаться в течение времени существования объекта набора строк возвращающего табличное значение параметра.|  
|DBPROP_ISupportErrorInfo|VARIANT_TRUE|  
|DBPROP_ISequentialStream|VARIANT_TRUE|  
|DBPROP_IMMOBILEROWS|VARIANT_TRUE|  
|DBPROP_LITERALIDENTITY|VARIANT_TRUE|  
|DBPROP_LOCKMODE|DBPROPVAL_LM_NONE|  
|DBPROP_MAXOPENROWS|0|  
|DBPROP_MAXPENDINGROWS|0|  
|DBPROP_MAXROWS|0|  
|DBPROP_NOTIFICATIONPHASES|0|  
|DBPROP_NOTIFYCOLUMNSET DBPROP_NOTIFYROWDELETE DBPROP_NOTIFYROWFIRSTCHANGE DBPROP_NOTIFYROWINSERT DBPROP_NOTIFYROWRESYNCH DBPROP_NOTIFYROWSETRELEASE DBPROP_NOTIFYROWSETFETCH-POSITIONCHANGE DBPROP_NOTIFYROWUNDOCHANGE DBPROP_NOTIFYROWUNDODELETE DBPROP_NOTIFYROWUNDOINSERT DBPROP_NOTIFYROWUPDATE|0|  
|DBPROP_OTHERINSERT DBPROP_OTHERUPDATEDELETE|VARIANT_FALSE|  
|DBPROP_OWNINSERT<br /><br /> DBPROP_OWNUPDATEDELETE|VARIANT_TRUE|  
|DBPROP_QUICKRESTART|VARIANT_TRUE|  
|DBPROP_REENTRANTEVENTS|VARIANT_FALSE|  
|DBPROP_REMOVEDELETED|VARIANT_TRUE|  
|DBPROP_RETURNPENDINGINSERTS|VARIANT_TRUE|  
|DBPROP_ROWRESTRICT|VARIANT_FALSE|  
|DBPROP_ROWTHREADMODEL|DBPROPVAL_RT_FREETHREAD|  
|DBPROP_SERVERCURSOR|VARIANT_FALSE|  
|DBPROP_SERVERDATAONINSERT|VARIANT_FALSE|  
|DBPROP_STRONGIDENTITY|VARIANT_TRUE|  
|DBPROP_TRANSACTEDOBJECT|VARIANT_FALSE|  
|DBPROP_UNIQUEROWS|VARIANT_FALSE|  
|DBPROP_UPDATABILITY|DBPROPVAL_UP_CHANGE &AMP;#124; DBPROPVAL_UP_DELETE &AMP;#124; DBPROPVAL_UP_INSERT|  
  
## <a name="property-sets"></a>Наборы свойств  
 Эти наборы свойств поддерживают параметры с табличным значением.  
  
### <a name="dbpropsetsqlservercolumn"></a>DBPROPSET_SQLSERVERCOLUMN  
 Это свойство используется потребителем в процессе создания объекта набора строк возвращающего табличное значение параметра с помощью ITableDefinitionWithConstraints::CreateTableWithConstraints для каждого столбца с помощью структуры DBCOLUMNDESC, если это необходимо.  
  
|Идентификатор свойства|Значение свойства|  
|-----------------|--------------------|  
|SSPROP_COL_COMPUTED|R Чтение и запись: чтение и запись<br /><br /> По умолчанию: значение VARIANT_FALSE<br /><br /> Тип: VT_BOOL<br /><br /> Описание: Если задано значение VARIANT_TRUE, указывает, что столбец является вычисляемым столбцом. VARIANT_FALSE означает, что столбец не является вычисляемым.|  
  
### <a name="dbpropsetsqlserverparameter"></a>DBPROPSET_SQLSERVERPARAMETER  
 Эти свойства считываются потребителем в процессе сведения о типе возвращающего табличное значение параметра в вызовах ISSCommandWithParamters::GetParameterProperties и устанавливаются потребителем в процессе задания отдельных свойств о табличное значение параметра через ISSCommandWithParameters::SetParameterProperties.  
  
 В следующей таблице приводятся подробные описания этих свойств.  
  
|Идентификатор свойства|Значение свойства|  
|-----------------|--------------------|  
|SSPROP_PARAM_TYPE_TYPENAME|R Чтение и запись: чтение и запись<br /><br /> По умолчанию: VT_EMPTY<br /><br /> Тип: VT_BSTR<br /><br /> Описание: Потребители используют это свойство для получения или задания имени типа возвращающего табличное значение параметра.<br /><br /> Это свойство также может использоваться с определяемыми пользователем типами данных CLR.<br /><br /> Это свойство можно указать по желанию, чтобы передать имя табличного типа для возвращающего табличное значение параметра (если при вызове команды применяется синтаксис ODBC). Для нерегламентированных параметризованных запросов SQL это свойство является обязательным.|  
|SSPROP_PARAM_TYPE_SCHEMANAME|R Чтение и запись: чтение и запись<br /><br /> По умолчанию: VT_EMPTY<br /><br /> Тип: VT_BSTR<br /><br /> Описание: Потребители используют это свойство для получения или задания имени схемы возвращающего табличное значение параметра.<br /><br /> Это свойство также может использоваться с определяемыми пользователем типами данных CLR.|  
|SSPROP_PARAM_TYPE_CATALOGNAME|Только для чтения R Чтение и запись:<br /><br /> По умолчанию: VT_EMPTY<br /><br /> Тип: VT_BSTR<br /><br /> Описание: Потребители используют это свойство для получения имени каталога возвращающего табличное значение параметра.<br /><br /> Это свойство также может использоваться с определяемыми пользователем типами данных CLR. Задание этого свойства является ошибкой; все табличные типы, определяемые пользователем, должны находиться в той же базе данных, что и использующие их возвращающие табличное значение параметры.|  
|SSPROP_PARAM_TABLE_DEFAULT_COLUMNS|R Чтение и запись: чтение и запись<br /><br /> По умолчанию: VT_EMPTY<br /><br /> Тип: VT_UI2 &#124; VT_ARRAY<br /><br /> Описание: Потребители используют это свойство для указания набор столбцов в наборе строк должны рассматриваться как значения по умолчанию. Значения для этих столбцов не передаются. При получении данных из потребительского объекта набора строк поставщик не требует привязки для этих столбцов.<br /><br /> Каждый элемент массива должен быть порядковым номером столбца в объекте набора строк. Если переданы недопустимые порядковые номера, это приведет к ошибке времени выполнения.|  
|SSPROP_PARAM_TABLE_COLUMN_ORDER|R Чтение и запись: чтение и запись<br /><br /> По умолчанию: VT_EMPTY<br /><br /> Тип: VT_UI2 &#124; VT_ARRAY<br /><br /> Описание: Это свойство используется потребителем, чтобы предоставить указание для сервера для указания сортировки упорядочиваются данные столбцов. Поставщик не проводит никакой проверки и предполагает, что потребитель выполняет существующую спецификацию. Сервер использует это свойство для проведения оптимизации.<br /><br /> Информация об упорядочивании каждого столбца представлена парой элементов массива. Первый элемент пары — номер столбца. Второй элемент пары равен 1, если сортировка проводится по возрастанию, и 2, если по убыванию.|  
  
## <a name="see-also"></a>См. также  
 [Поддержка типов табличное значение параметра OLE DB](../../relational-databases/native-client-ole-db-table-valued-parameters/ole-db-table-valued-parameter-type-support.md)   
 [Использование возвращающих табличные значения параметров &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
