---
title: Обнаружение типа возвращающего табличное значение параметра | Документация Майкрософт
description: Обнаружение типа возвращающего табличное значение параметра с помощью драйвера OLE DB для SQL Server
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- table-valued parameters, type discovery
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 4e824e39a44985dc2f46a1a27c7b5b4e8d05a6dc
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68015301"
---
# <a name="table-valued-parameter-type-discovery"></a>Обнаружение типа возвращающего табличное значение параметра
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Потребитель (клиентское приложение, использующее драйвер OLE DB для SQL Server) может определить тип каждого параметра команды, если текст команды передается поставщику OLE DB. После того как тип возвращающего табличное значение параметра становится известен, потребитель может определить метаданные для каждого отдельного столбца возвращающего табличное значение параметра.  
  
 Сведения о типе параметров процедуры поддерживаются ICommandWithParameters:: GetParameterInfo для большинства типов параметров. Начиная с версии [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] с появлением пользовательских типов и типа данных **xml** одного метода GetParameterInfo стало недостаточно для этой цели, так как предоставить сведения о пользовательском типе (имя, схему и каталог) через интерфейс ICommandWithParameters невозможно. Для предоставления расширенных сведений о типе был определен новый интерфейс ISSCommandWithParameters.  
  
 Для возвращающих табличное значение параметров также используется интерфейс ISSCommandWithParameters для обнаружения подробных сведений. Клиент вызывает ISSCommandWithParameters:: GetParameterInfo после подготовки объекта команды. Для возвращающих табличные значения параметров элемент *wType* структуры DBPARAMINFO устанавливается поставщиком в значение DBTYPE_TABLE. Поле *ulParamSize* структуры DBPARAMINFO имеет значение ~0.  
  
 Объект-получатель затем запрашивает дополнительные свойства (имя каталога для типа табличного параметра, имя схемы для типа табличного параметра, имя типа табличного параметра, порядок столбцов и столбцы по умолчанию) с помощью ISSCommandWithParameters::GetParameterProperties.  
  
 После того как имя типа стало известно, для получения сведений об отдельном столбце потребитель должен либо вызвать метод IOpenRowset::OpenRowset, либо получить набор строк DBSCHEMA_TABLE_TYPE_COLUMNS, указав имя типа возвращающего табличное значение параметра в качестве имени таблицы.  
  
## <a name="see-also"></a>См. также:  
 [Возвращающие табличные значения параметры &#40;OLE DB&#41;](../../oledb/ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)   
 [Использование возвращающих табличные значения параметров &#40;OLE DB&#41;](../../oledb/ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
