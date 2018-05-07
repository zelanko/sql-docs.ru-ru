---
title: Обнаружение типа возвращающего табличное значение параметра | Документы Microsoft
description: Table-Valued обнаружение типа параметра, с помощью драйвера OLE DB для SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: ole-db-table-valued-parameters
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- table-valued parameters, type discovery
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 502db140bbfb63bf4d0c3d7c6a82bb2459633384
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="table-valued-parameter-type-discovery"></a>Обнаружение типа возвращающего табличное значение параметра
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Потребитель — то есть, клиентское приложение использует драйвер OLE DB для SQL Server, можно определить тип каждого параметра команды, если текст команды задано для поставщика OLE DB. Выяснив тип параметра, возвращающие табличные значения, потребитель может определить сведения метаданных для каждого отдельного столбца, возвращающих табличные значения параметра.  
  
 Сведения о типе параметров процедур поддерживается ICommandWithParameters::GetParameterInfo для большинства типов параметров. Начиная с версии [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], с появлением определяемых пользователем типов и **xml** тип данных, метод GetParameterInfo недостаточно для этой цели, так как не удалось предоставить определяемого пользователем типа сведения (имя, схему и каталог) через ICommandWithParameters. Новый интерфейс ISSCommandWithParameters, был определен для предоставления расширенных сведений о типе.  
  
 Для параметров, возвращающих табличные значения также использовать интерфейс ISSCommandWithParameters для получения подробных сведений. Клиент вызывает ISSCommandWithParameters::GetParameterInfo после подготовки объекта команды. Для возвращающих табличное значение параметров *wType* член структуры DBPARAMINFO имеет значение DBTYPE_TABLE поставщиком. *UlParamSize* структуры DBPARAMINFO имеет значение ~ 0.  
  
 Затем потребитель запрашивает дополнительные свойства (имя каталога табличное значение параметра типа, имя схемы табличное значение параметра типа, имя типа возвращающего табличное значение параметра, порядок столбцов и столбцов по умолчанию) с помощью ISSCommandWithParamters:: GetParameterProperties.  
  
 Для получения сведений о отдельных столбцов, которые пользователь должен либо вызвать Выяснив имя типа, IOpenRowset::OpenRowsetor получить набор строк DBSCHEMA_TABLE_TYPE_COLUMNS, указав имя типа возвращающего табличное значение параметра как имя таблицы.  
  
## <a name="see-also"></a>См. также  
 [Возвращающие табличные значения параметров &#40;OLE DB&#41;](../../oledb/ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)   
 [Использование возвращающих табличные значения параметры & #40; OLE DB & #41;](../../oledb/ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
