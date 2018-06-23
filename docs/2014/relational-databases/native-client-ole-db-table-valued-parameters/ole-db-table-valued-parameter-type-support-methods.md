---
title: Поддержка типов табличное значение параметра OLE DB (методы) | Документы Microsoft
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
helpviewer_keywords:
- table-valued parameters (OLE DB), API support (methods)
ms.assetid: e3c2a450-8fd4-44cb-93d8-affe1b65c68e
caps.latest.revision: 10
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: e7a22684fabd74400a280396c696c7936081a8d5
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36192654"
---
# <a name="ole-db-table-valued-parameter-type-support-methods"></a>Поддержка типов параметров OLE DB, возвращающих табличное значение (методы)
  Следующие стандартные методы OLE DB поддерживают возвращающие табличные значения параметры.  
  
|Метод|Поддержка возвращающих табличные значения параметров|  
|------------|-------------------------------------|  
|ITableDefinitionWithConstraints::CreateTableWithConstraints|Используется при наличии сведений о типе возвращающего табличное значение параметра и необходимости создания экземпляра объекта набора строк возвращающего табличное значение параметра на основе сведений о типе.<br /><br /> Дополнительные сведения см. в разделе «Статический сценарий» в [создания набора строк возвращающего табличное значение параметра](table-valued-parameter-rowset-creation.md).|  
|IOpenRowset::OpenRowset|Используется при отсутствии сведений о типе возвращающего табличное значение параметра и необходимости создания экземпляра объекта набора строк возвращающего табличное значение параметра на основе метаданных, полученных от сервера.<br /><br /> Дополнительные сведения см. в разделе «Динамический сценарий» в [создания набора строк возвращающего табличное значение параметра](table-valued-parameter-rowset-creation.md).|  
|ISSCommandWithParameters::SetParameterInfo|Чтобы указать параметр команды табличное значение параметра, потребитель указывает тип параметра как «table» или «DBTYPE_TABLE» в *pwszName* структуры DBPARAMBINDINFO. *UlParamSize* имеет значение ~ 0. Дополнительные сведения см. в разделе «Спецификация возвращающего табличное значение параметра» в [Executing Commands Containing Table-Valued параметры](executing-commands-containing-table-valued-parameters.md).|  
|ISSCommandWithParameters::SetParameterProperties|Задает свойства, определенные для возвращающих табличные значения параметров, например имя схемы, имя типа, порядок столбца и столбцы по умолчанию.<br /><br /> Потребитель указывает порядковый номер параметра в *iOrdinal* структуры SSPARAMPROPS. Запрошенный набор свойств — DBPROPSET_SQLSERVERPARAMETER.|  
|ISSCommandWithParameters::GetParameterInfo|Возвращает типы всех параметров в указанную команду.<br /><br /> Для возвращающих табличное значение параметров *wType* поле в структуре DBPARAMINFO будет иметь тип DBTYPE_TABLE. *UlParamSize* будет содержать значение ~ 0 для определения неизвестной длины.|  
|ISSCommandWithParameters::GetParameterProperties|Возвращает дополнительные сведения о типе для параметров типа DBTYPE_TABLE.<br /><br /> Потребитель указывает порядковый номер параметра в *iOrdinal* структуры SSPARAMPROPS. Потребитель может запросить любое свойство в набор свойств dbpropset_sqlserverparameter, перечисленных в разделе ISSCommandWithParameters::SetParameterProperties.<br /><br /> Поскольку потребителю неизвестен тип возвращающего табличное значение параметра, поставщик должен установить правильные значения свойств SSPROP_PARAM_TYPE_TYPENAME, SSPROP_PARAM_TYPE_SCHEMANAME и SSPROP_PARAM_TYPE_CATALOGNAME. Оставшиеся свойства, SSPROP_PARAM_TABLE_DEFAULT_COLUMNS и SSPROP_PARAM_TABLE_COLUMN_SORT_ORDER, сохранят значения по умолчанию. После обнаружения потребителем имени типа табличное значение параметра IOpenRowset::OpenRowset используется для создания экземпляра этого табличное значение параметра, указав имя типа возвращающего табличное значение параметра. Дополнительные сведения см. в разделе [обнаружение типа возвращающего табличное значение параметра](../../database-engine/dev-guide/table-valued-parameter-type-discovery.md).|  
|IRowsetInfo::GetProperties|Возвращает свойства набора строк возвращающего табличное значение параметра. Потребитель может использовать эти параметры для оптимальной установки привязок.|  
|IColumnsRowset::GetColumnsRowset|Получает метаданные о таблице [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Для возвращающих табличные значения параметров этот же интерфейс предоставляет подробные метаданные о каждом столбце, например:<br /><br /> -DBCOLUMN_FLAGS обозначает допустимость значений NULL в бите DBCOLUMNFLAGS_ISNULLABLE.<br />-DBCOLUMN_ISUNIQUE указывает, является ли столбец столбцом идентификаторов.<br />-DBCOLUMN_COMPUTEMODE указывает, является ли столбец вычисляемым.|  
|IAccessor::CreateAccessor|Для привязки объекта набора строк возвращающего табличное значение параметра для параметра команды, можно создать метод доступа с его *wType* член значение DBTYPE_TABLE. Структура DBOBJECT будет содержать IID_IRowset или любой другой допустимый интерфейс объекта набора в *iid* член. Оставшиеся поля обрабатываются тем же способом, как и DBTYPE_IUNKNOWN.|  
  
## <a name="see-also"></a>См. также  
 [Поддержка типов табличное значение параметра OLE DB](ole-db-table-valued-parameter-type-support.md)   
 [Создание набора строк возвращающего табличное значение параметра](table-valued-parameter-rowset-creation.md)   
 [Использование возвращающих табличные значения параметров &#40;OLE DB&#41;](table-valued-parameters-ole-db.md)  
  
  