---
title: Поддержка типов параметров OLE DB, возвращающих табличные значения (методы) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (OLE DB), API support (methods)
ms.assetid: e3c2a450-8fd4-44cb-93d8-affe1b65c68e
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 082eb2c9e04a3aa77ff7098036e39460dff6a379
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67967406"
---
# <a name="ole-db-table-valued-parameter-type-support-methods"></a>Поддержка типов параметров OLE DB, возвращающих табличное значение (методы)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Следующие стандартные методы OLE DB поддерживают возвращающие табличные значения параметры.  
  
|Метод|Поддержка возвращающих табличные значения параметров|  
|------------|-------------------------------------|  
|ITableDefinitionWithConstraints::CreateTableWithConstraints|Используется при наличии сведений о типе возвращающего табличное значение параметра и необходимости создания экземпляра объекта набора строк возвращающего табличное значение параметра на основе сведений о типе.<br /><br /> Дополнительные сведения см. в разделе «Статический сценарий» в [Создание набора строк возвращающего табличное значение параметра](../../relational-databases/native-client-ole-db-table-valued-parameters/table-valued-parameter-rowset-creation.md).|  
|IOpenRowset::OpenRowset|Используется при отсутствии сведений о типе возвращающего табличное значение параметра и необходимости создания экземпляра объекта набора строк возвращающего табличное значение параметра на основе метаданных, полученных от сервера.<br /><br /> Дополнительные сведения см. в разделе «Динамический сценарий» в [Создание набора строк возвращающего табличное значение параметра](../../relational-databases/native-client-ole-db-table-valued-parameters/table-valued-parameter-rowset-creation.md).|  
|ISSCommandWithParameters::SetParameterInfo|Для указания возвращающего табличное значение параметра команды потребитель указывает тип параметра "table" или "DBTYPE_TABLE" в элементе *pwszName* структуры DBPARAMBINDINFO. *UlParamSize* имеет значение ~ 0. Дополнительные сведения см. в разделе «Спецификация возвращающего табличное значение параметр» в [Executing Commands Containing Table-Valued параметры](../../relational-databases/native-client-ole-db-table-valued-parameters/executing-commands-containing-table-valued-parameters.md).|  
|ISSCommandWithParameters::SetParameterProperties|Задает свойства, определенные для возвращающих табличные значения параметров, например имя схемы, имя типа, порядок столбца и столбцы по умолчанию.<br /><br /> Потребитель указывает порядковый номер параметра в элементе *iOrdinal* структуры SSPARAMPROPS. Запрошенный набор свойств — DBPROPSET_SQLSERVERPARAMETER.|  
|ISSCommandWithParameters::GetParameterInfo|Возвращает типы всех параметров в указанную команду.<br /><br /> Для возвращающих табличные значения параметров поле *wType* в структуре DBPARAMINFO будет иметь тип DBTYPE_TABLE. Для определения неизвестной длины поле *ulParamSize* будет установлено в значение ~0.|  
|ISSCommandWithParameters::GetParameterProperties|Возвращает дополнительные сведения о типе для параметров типа DBTYPE_TABLE.<br /><br /> Потребитель указывает порядковый номер параметра в элементе *iOrdinal* структуры SSPARAMPROPS. Потребитель может запросить любое свойство в набор свойств dbpropset_sqlserverparameter, перечисленных в разделе ISSCommandWithParameters::SetParameterProperties.<br /><br /> Поскольку потребителю неизвестен тип возвращающего табличное значение параметра, поставщик должен установить правильные значения свойств SSPROP_PARAM_TYPE_TYPENAME, SSPROP_PARAM_TYPE_SCHEMANAME и SSPROP_PARAM_TYPE_CATALOGNAME. Оставшиеся свойства, SSPROP_PARAM_TABLE_DEFAULT_COLUMNS и SSPROP_PARAM_TABLE_COLUMN_SORT_ORDER, сохранят значения по умолчанию. После обнаружения потребителем имени типа возвращающего табличное значение параметра он использует метод IOpenRowset::OpenRowset для создания экземпляра этого параметра, указав имя его типа. Дополнительные сведения см. в разделе [обнаружение типа возвращающего табличное значение параметра](../../relational-databases/native-client-ole-db-table-valued-parameters/table-valued-parameter-type-discovery.md).|  
|IRowsetInfo::GetProperties|Возвращает свойства набора строк возвращающего табличное значение параметра. Потребитель может использовать эти параметры для оптимальной установки привязок.|  
|IColumnsRowset::GetColumnsRowset|Получает метаданные о таблице [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Для возвращающих табличные значения параметров этот же интерфейс предоставляет подробные метаданные о каждом столбце, например:<br /><br /> DBCOLUMN_FLAGS обозначает допустимость значений типа NULL в бите DBCOLUMNFLAGS_ISNULLABLE;<br /><br /> DBCOLUMN_ISUNIQUE обозначает, является ли столбец столбцом идентификаторов;<br /><br /> DBCOLUMN_COMPUTEMODE обозначает, является ли столбец вычисляемым.|  
|IAccessor::CreateAccessor|Для привязки объекта набора строк возвращающего табличное значение параметра создается метод доступа с элементом *wType*, установленным в значение DBTYPE_TABLE. Структура DBOBJECT будет содержать IID_IRowset или любой другой допустимый интерфейс объекта набора строк в элементе *iid*. Оставшиеся поля обрабатываются тем же способом, как и DBTYPE_IUNKNOWN.|  
  
## <a name="see-also"></a>См. также  
 [Поддержка типов параметров OLE DB, возвращающих табличные значения](../../relational-databases/native-client-ole-db-table-valued-parameters/ole-db-table-valued-parameter-type-support.md)   
 [Создание набора строк возвращающего табличное значение параметра](../../relational-databases/native-client-ole-db-table-valued-parameters/table-valued-parameter-rowset-creation.md)   
 [Использование возвращающих табличные значения параметров &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
