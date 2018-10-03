---
title: Обнаружение типа возвращающего табличное значение параметра | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters, type discovery
ms.assetid: f55818c2-ebb5-4cf6-8c0c-0da41f592560
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: bbdbfd58cc8e14722e62eee47223b1995c1d585e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47777332"
---
# <a name="table-valued-parameter-type-discovery"></a>Обнаружение типа возвращающего табличное значение параметра
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Потребитель — то есть клиентское приложение, использующее [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственный поставщик OLE DB клиента, может определить тип каждого параметра команды, если поставщик OLE DB внимание было уделено текст команды. После того как тип возвращающего табличное значение параметра становится известен, потребитель может определить метаданные для каждого отдельного столбца возвращающего табличное значение параметра.  
  
 Сведения о типе параметров процедур поддерживается ICommandWithParameters::GetParameterInfo для большинства типов параметров. Начиная с версии [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] с появлением пользовательских типов и типа данных **xml** одного метода GetParameterInfo стало недостаточно для этой цели, так как предоставить сведения о пользовательском типе (имя, схему и каталог) через интерфейс ICommandWithParameters невозможно. Новый интерфейс ISSCommandWithParameters, был определен для предоставления расширенных сведений о типе.  
  
 Для возвращающих табличные значения параметров также использовать интерфейс ISSCommandWithParameters для обнаружения подробных сведений. Клиент вызывает ISSCommandWithParameters::GetParameterInfo после подготовки объекта команды. Для возвращающих табличное значение параметров *wType* поставщиком член структуры DBPARAMINFO имеет значение DBTYPE_TABLE. Поле *ulParamSize* структуры DBPARAMINFO имеет значение ~0.  
  
 Затем потребитель запрашивает дополнительные свойства (имя каталога типа, имя схемы типа, имя типа возвращающего табличное значение параметра, порядок столбцов и столбцы по умолчанию) с помощью метода ISSCommandWithParamters::GetParameterProperties.  
  
 После того как имя типа стало известно, для получения сведений об отдельном столбце потребитель должен либо вызвать метод IOpenRowset::OpenRowset, либо получить набор строк DBSCHEMA_TABLE_TYPE_COLUMNS, указав имя типа возвращающего табличное значение параметра в качестве имени таблицы.  
  
## <a name="see-also"></a>См. также  
 [Возвращающие табличные значения параметры &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)   
 [Использование возвращающих табличные значения параметров &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
