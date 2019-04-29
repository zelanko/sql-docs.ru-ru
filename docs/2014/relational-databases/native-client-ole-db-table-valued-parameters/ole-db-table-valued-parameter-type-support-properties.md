---
title: Поддержка типов параметров OLE DB, возвращающих табличные значения (свойства) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (OLE DB), API support (properties)
ms.assetid: b9c4e6ed-fe4f-4ef8-9bc8-784d80d44039
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5cdd19895a1cf91e1c5c8608013cb52482f946c5
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63046539"
---
# <a name="ole-db-table-valued-parameter-type-support-properties"></a>Поддержка типов параметров OLE DB, возвращающих табличные значения (свойства)
  В данном разделе приводятся сведения о свойствах и наборах свойств OLE DB, связанных с объектами наборов строк для возвращающего табличное значение параметра.  
  
## <a name="properties"></a>Свойства  
 Далее приводится список свойств, к которым можно получить доступ, применив метод IRowsetInfo::GetProperties к объектам наборов строк для табличного параметра. Следует заметить, что все свойства объектов наборов строк для возвращающего табличное значение параметра неизменяемы. Таким образом попытка задать любой из этих свойств с помощью IOpenRowset::OpenRowset или ITableDefinitionWithConstraints::CreateTableWithConstraints способы их значения по умолчанию вызовет ошибку, и объект не будет создан.  
  
 Свойства, не реализованные в объекте наборов строк для возвращающего табличное значение параметра, здесь не перечислены. Полный набор свойств можно найти в документации по OLE DB в разделе, посвященном компонентам доступа к данным Windows.  
  
|Идентификатор свойства|Значение|  
|-----------------|-----------|  
|DBPROP_ABORTPRESERVE|VARIANT_TRUE|  
|DBPROP_ACCESSORDER|DBPROPVAL_AO_RANDOM|  
|DBPROP_BLOCKINGSTORAGEOBJECTS|VARIANT_TRUE|  
|DBPROP_BOOKMARKS<br /><br /> DBPROP_LITERALBOOKMARKS|И ЗАПИСЬ: Только для чтения<br /><br /> По умолчанию: VARIANT_FALSE<br /><br /> Описание. Закладки не разрешены в объекты набора строк возвращающего табличное значение параметра.|  
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
|DBPROP_IRowsetChange|VARIANT_TRUE<br /><br /> Примечание. Объекта набора строк возвращающего табличное значение параметра поддерживает интерфейсы IRowsetChange.<br /><br /> Набор строк, созданный с DBPROP_IRowsetChange, равным VARIANT_TRUE, отражает режимы немедленного обновления.<br /><br /> Однако, если столбцы типа BLOB привязаны как объекты ISequentialStream, потребитель должен сохранять их все время, пока существует объект набора строк возвращающего табличное значение параметра.|  
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
|DBPROP_UPDATABILITY|DBPROPVAL_UP_CHANGE &#124; DBPROPVAL_UP_DELETE &#124; DBPROPVAL_UP_INSERT|  
  
## <a name="property-sets"></a>Наборы свойств  
 Эти наборы свойств поддерживают параметры с табличным значением.  
  
### <a name="dbpropsetsqlservercolumn"></a>DBPROPSET_SQLSERVERCOLUMN  
 Это свойство используется потребителем в процессе создания объекта набора строк возвращающего табличное значение параметра с помощью ITableDefinitionWithConstraints::CreateTableWithConstraints для каждого столбца через структуру DBCOLUMNDESC, при необходимости.  
  
|Идентификатор свойства|Значение свойства|  
|-----------------|--------------------|  
|SSPROP_COL_COMPUTED|И ЗАПИСЬ: Чтение и запись<br /><br /> По умолчанию: VARIANT_FALSE<br /><br /> Тип: VT_BOOL<br /><br /> Описание. При значении VARIANT_TRUE, указывает, что столбец является вычисляемым. VARIANT_FALSE означает, что столбец не является вычисляемым.|  
  
### <a name="dbpropsetsqlserverparameter"></a>DBPROPSET_SQLSERVERPARAMETER  
 Эти свойства считываются потребителем при обнаружении сведения о типе возвращающего табличное значение параметра в вызовах ISSCommandWithParameters::GetParameterProperties и устанавливаются потребителем в процессе задания отдельных свойств о возвращающих табличные значения параметра через ISSCommandWithParameters::SetParameterProperties.  
  
 В следующей таблице приводятся подробные описания этих свойств.  
  
|Идентификатор свойства|Значение свойства|  
|-----------------|--------------------|  
|SSPROP_PARAM_TYPE_TYPENAME|И ЗАПИСЬ: Чтение и запись<br /><br /> По умолчанию: VT_EMPTY<br /><br /> Тип: VT_BSTR<br /><br /> Описание. Потребители используют это свойство для получения или задания имени типа возвращающего табличное значение параметра.<br /><br /> Это свойство также может использоваться с определяемыми пользователем типами данных CLR.<br /><br /> Это свойство можно указать по желанию, чтобы передать имя табличного типа для возвращающего табличное значение параметра (если при вызове команды применяется синтаксис ODBC). Для нерегламентированных параметризованных запросов SQL это свойство является обязательным.|  
|SSPROP_PARAM_TYPE_SCHEMANAME|И ЗАПИСЬ: Чтение и запись<br /><br /> По умолчанию: VT_EMPTY<br /><br /> Тип: VT_BSTR<br /><br /> Описание. Потребители используют это свойство для получения или задания имени схемы возвращающего табличное значение параметра.<br /><br /> Это свойство также может использоваться с определяемыми пользователем типами данных CLR.|  
|SSPROP_PARAM_TYPE_CATALOGNAME|И ЗАПИСЬ: Только для чтения<br /><br /> По умолчанию: VT_EMPTY<br /><br /> Тип: VT_BSTR<br /><br /> Описание. Потребители используют это свойство для получения имени каталога возвращающего табличное значение параметра.<br /><br /> Это свойство также может использоваться с определяемыми пользователем типами данных CLR. Задание этого свойства является ошибкой; все табличные типы, определяемые пользователем, должны находиться в той же базе данных, что и использующие их возвращающие табличное значение параметры.|  
|SSPROP_PARAM_TABLE_DEFAULT_COLUMNS|И ЗАПИСЬ: Чтение и запись<br /><br /> По умолчанию: VT_EMPTY<br /><br /> Тип: VT_UI2 &#124; VT_ARRAY<br /><br /> Описание. Потребители используют это свойство для указания, какой набор столбцов в наборе строк должны рассматриваться как значения по умолчанию. Значения для этих столбцов не передаются. При получении данных из потребительского объекта набора строк поставщик не требует привязки для этих столбцов.<br /><br /> Каждый элемент массива должен быть порядковым номером столбца в объекте набора строк. Если переданы недопустимые порядковые номера, это приведет к ошибке времени выполнения.|  
|SSPROP_PARAM_TABLE_COLUMN_ORDER|И ЗАПИСЬ: Чтение и запись<br /><br /> По умолчанию: VT_EMPTY<br /><br /> Тип: VT_UI2 &#124; VT_ARRAY<br /><br /> Описание. Это свойство используется потребителем для предоставления подсказки на сервер, каким образом упорядочение данных столбца. Поставщик не проводит никакой проверки и предполагает, что потребитель выполняет существующую спецификацию. Сервер использует это свойство для проведения оптимизации.<br /><br /> Информация об упорядочивании каждого столбца представлена парой элементов массива. Первый элемент пары — номер столбца. Второй элемент пары равен 1, если сортировка проводится по возрастанию, и 2, если по убыванию.|  
  
## <a name="see-also"></a>См. также  
 [Поддержка типов параметров OLE DB, возвращающих табличные значения](ole-db-table-valued-parameter-type-support.md)   
 [Использование возвращающих табличные значения параметров &#40;OLE DB&#41;](table-valued-parameters-ole-db.md)  
  
  
