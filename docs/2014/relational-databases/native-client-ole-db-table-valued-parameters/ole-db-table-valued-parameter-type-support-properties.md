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
author: rothja
ms.author: jroth
ms.openlocfilehash: bda93e970e933f1db604fa529133e6d023b3337e
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85043343"
---
# <a name="ole-db-table-valued-parameter-type-support-properties"></a>Поддержка типов параметров OLE DB, возвращающих табличные значения (свойства)
  В данном разделе приводятся сведения о свойствах и наборах свойств OLE DB, связанных с объектами наборов строк для возвращающего табличное значение параметра.  
  
## <a name="properties"></a>Свойства  
 Далее приводится список свойств, к которым можно получить доступ, применив метод IRowsetInfo::GetProperties к объектам наборов строк для табличного параметра. Следует заметить, что все свойства объектов наборов строк для возвращающего табличное значение параметра неизменяемы. Следовательно, попытка изменить значения любого из этих свойств с помощью метода IOpenRowset::OpenRowset или ITableDefinitionWithConstraints::CreateTableWithConstraints вызовет ошибку, и никакие объекты созданы не будут.  
  
 Свойства, не реализованные в объекте наборов строк для возвращающего табличное значение параметра, здесь не перечислены. Полный набор свойств можно найти в документации по OLE DB в разделе, посвященном компонентам доступа к данным Windows.  
  
|Идентификатор свойства|Значение|  
|-----------------|-----------|  
|DBPROP_ABORTPRESERVE|VARIANT_TRUE|  
|DBPROP_ACCESSORDER|DBPROPVAL_AO_RANDOM|  
|DBPROP_BLOCKINGSTORAGEOBJECTS|VARIANT_TRUE|  
|DBPROP_BOOKMARKS<br /><br /> DBPROP_LITERALBOOKMARKS|R/W: только для чтения<br /><br /> Значение по умолчанию: VARIANT_FALSE<br /><br /> Описание: использование закладок для объектов наборов строк возвращающего табличное значение параметра не допускается.|  
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
|DBPROP_IRowsetChange|VARIANT_TRUE<br /><br /> Примечание. объект набора строк возвращающего табличное значение параметра поддерживает интерфейсы IRowsetChange.<br /><br /> Набор строк, созданный с DBPROP_IRowsetChange, равным VARIANT_TRUE, отражает режимы немедленного обновления.<br /><br /> Однако, если столбцы типа BLOB привязаны как объекты ISequentialStream, потребитель должен сохранять их все время, пока существует объект набора строк возвращающего табличное значение параметра.|  
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
  
### <a name="dbpropset_sqlservercolumn"></a>DBPROPSET_SQLSERVERCOLUMN  
 Это свойство используется потребителем в процессе создания объекта наборов строк для параметра с табличным значением с помощью вызова метода ITableDefinitionWithConstraints::CreateTableWithConstraints для каждого столбца через структуру DBCOLUMNDESC, если потребуется.  
  
|Идентификатор свойства|Значение свойства|  
|-----------------|--------------------|  
|SSPROP_COL_COMPUTED|Чтение и запись в R/W<br /><br /> Значение по умолчанию: VARIANT_FALSE<br /><br /> Тип: VT_BOOL.<br /><br /> Описание: значение VARIANT_TRUE означает, что столбец является вычисляемым. VARIANT_FALSE означает, что столбец не является вычисляемым.|  
  
### <a name="dbpropset_sqlserverparameter"></a>DBPROPSET_SQLSERVERPARAMETER  
 Эти значения считываются потребителем в процессе получения информации о типе возвращающего табличное значение параметра при вызовах метода ISSCommandWithParameters::GetParameterProperties и устанавливаются потребителем в процессе задания отдельных свойств возвращающего табличное значение параметра с помощью метода ISSCommandWithParameters::SetParameterProperties.  
  
 В следующей таблице приводятся подробные описания этих свойств.  
  
|Идентификатор свойства|Значение свойства|  
|-----------------|--------------------|  
|SSPROP_PARAM_TYPE_TYPENAME|Чтение и запись в R/W<br /><br /> Значение по умолчанию: VT_EMPTY<br /><br /> Тип: VT_BSTR<br /><br /> Описание: потребители используют это свойство для получения или задания имени типа для возвращающего табличное значение параметра.<br /><br /> Это свойство также может использоваться с определяемыми пользователем типами данных CLR.<br /><br /> Это свойство можно указать по желанию, чтобы передать имя табличного типа для возвращающего табличное значение параметра (если при вызове команды применяется синтаксис ODBC). Для нерегламентированных параметризованных запросов SQL это свойство является обязательным.|  
|SSPROP_PARAM_TYPE_SCHEMANAME|Чтение и запись в R/W<br /><br /> Значение по умолчанию: VT_EMPTY<br /><br /> Тип: VT_BSTR<br /><br /> Описание: потребители используют это свойство для получения или задания имени схемы возвращающего табличное значение параметра.<br /><br /> Это свойство также может использоваться с определяемыми пользователем типами данных CLR.|  
|SSPROP_PARAM_TYPE_CATALOGNAME|R/W: только для чтения<br /><br /> Значение по умолчанию: VT_EMPTY<br /><br /> Тип: VT_BSTR<br /><br /> Описание: потребители используют это свойство для получения имени каталога возвращающего табличное значение параметра.<br /><br /> Это свойство также может использоваться с определяемыми пользователем типами данных CLR. Задание этого свойства является ошибкой; все табличные типы, определяемые пользователем, должны находиться в той же базе данных, что и использующие их возвращающие табличное значение параметры.|  
|SSPROP_PARAM_TABLE_DEFAULT_COLUMNS|Чтение и запись в R/W<br /><br /> Значение по умолчанию: VT_EMPTY<br /><br /> Type: VT_UI2 &#124; VT_ARRAY<br /><br /> Описание: потребители используют это свойство, чтобы указать, какие именно столбцы в наборе строк должны обрабатываться как значения по умолчанию. Значения для этих столбцов не передаются. При получении данных из потребительского объекта набора строк поставщик не требует привязки для этих столбцов.<br /><br /> Каждый элемент массива должен быть порядковым номером столбца в объекте набора строк. Если переданы недопустимые порядковые номера, это приведет к ошибке времени выполнения.|  
|SSPROP_PARAM_TABLE_COLUMN_ORDER|Чтение и запись в R/W<br /><br /> Значение по умолчанию: VT_EMPTY<br /><br /> Type: VT_UI2 &#124; VT_ARRAY<br /><br /> Описание: это свойство используется потребителем, чтобы указать серверу, каким образом упорядочиваются данные столбцов при сортировке. Поставщик не проводит никакой проверки и предполагает, что потребитель выполняет существующую спецификацию. Сервер использует это свойство для проведения оптимизации.<br /><br /> Информация об упорядочивании каждого столбца представлена парой элементов массива. Первый элемент пары — номер столбца. Второй элемент пары равен 1, если сортировка проводится по возрастанию, и 2, если по убыванию.|  
  
## <a name="see-also"></a>См. также:  
 [Поддержка типа возвращающего табличное значение параметра OLE DB](ole-db-table-valued-parameter-type-support.md)   
 [Использование возвращающих табличные значения параметров &#40;OLE DB&#41;](table-valued-parameters-ole-db.md)  
  
  
