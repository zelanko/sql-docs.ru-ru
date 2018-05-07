---
title: Обнаружение типа возвращающего табличное значение параметра | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client-ole-db-table-valued-parameters
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- table-valued parameters, type discovery
ms.assetid: f55818c2-ebb5-4cf6-8c0c-0da41f592560
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: af920c6ee746d064a1cb02d7ba60779dd6e8b22e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="table-valued-parameter-type-discovery"></a>Обнаружение типа возвращающего табличное значение параметра
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Потребитель — то есть, клиентское приложение, использующее [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщиком Native Client OLE DB — может определить тип каждого параметра команды, если текст команды задано для поставщика OLE DB. Выяснив тип параметра, возвращающие табличные значения, потребитель может определить сведения метаданных для каждого отдельного столбца, возвращающих табличные значения параметра.  
  
 Сведения о типе параметров процедур поддерживается ICommandWithParameters::GetParameterInfo для большинства типов параметров. Начиная с версии [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], с появлением определяемых пользователем типов и **xml** тип данных, метод GetParameterInfo недостаточно для этой цели, так как не удалось предоставить определяемого пользователем типа сведения (имя, схему и каталог) через ICommandWithParameters. Новый интерфейс ISSCommandWithParameters, был определен для предоставления расширенных сведений о типе.  
  
 Для параметров, возвращающих табличные значения также использовать интерфейс ISSCommandWithParameters для получения подробных сведений. Клиент вызывает ISSCommandWithParameters::GetParameterInfo после подготовки объекта команды. Для возвращающих табличное значение параметров *wType* член структуры DBPARAMINFO имеет значение DBTYPE_TABLE поставщиком. *UlParamSize* структуры DBPARAMINFO имеет значение ~ 0.  
  
 Затем потребитель запрашивает дополнительные свойства (имя каталога табличное значение параметра типа, имя схемы табличное значение параметра типа, имя типа возвращающего табличное значение параметра, порядок столбцов и столбцов по умолчанию) с помощью ISSCommandWithParamters:: GetParameterProperties.  
  
 Для получения сведений о отдельных столбцов, которые пользователь должен либо вызвать Выяснив имя типа, IOpenRowset::OpenRowsetor получить набор строк DBSCHEMA_TABLE_TYPE_COLUMNS, указав имя типа возвращающего табличное значение параметра как имя таблицы.  
  
## <a name="see-also"></a>См. также  
 [Возвращающие табличные значения параметров &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)   
 [Использование возвращающих табличные значения параметры & #40; OLE DB & #41;](../../relational-databases/native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
