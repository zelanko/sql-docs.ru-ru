---
title: Обнаружение типа возвращающего табличное значение параметра | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
helpviewer_keywords:
- table-valued parameters, type discovery
ms.assetid: f55818c2-ebb5-4cf6-8c0c-0da41f592560
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: cf3f7b4d6754902ac38172ffa0e8fc392599d307
ms.sourcegitcommit: b87c384e10d6621cf3a95ffc79d6f6fad34d420f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60154840"
---
# <a name="table-valued-parameter-type-discovery"></a>Обнаружение типа возвращающего табличное значение параметра
  Потребитель — то есть клиентское приложение, использующее [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента — могут определить тип каждого параметра команды, если поставщик OLE DB внимание было уделено текст команды. После того как тип возвращающего табличное значение параметра становится известен, потребитель может определить метаданные для каждого отдельного столбца возвращающего табличное значение параметра.  
  
 Сведения о типе параметров процедур поддерживается ICommandWithParameters::GetParameterInfo для большинства типов параметров. Начиная с версии [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], с появлением определяемых пользователем типов и `xml` тип данных, getparameterinfo-метод стало недостаточно для этой цели, так как не удалось указать сведения о пользовательских типах (имя, схемы, и каталог) через ICommandWithParameters. Новый интерфейс ISSCommandWithParameters, был определен для предоставления расширенных сведений о типе.  
  
 Для возвращающих табличные значения параметров также использовать интерфейс ISSCommandWithParameters для обнаружения подробных сведений. Клиент вызывает ISSCommandWithParameters::GetParameterInfo после подготовки объекта команды. Для возвращающих табличные значения параметров элемент *wType* структуры DBPARAMINFO устанавливается поставщиком в значение DBTYPE_TABLE. Поле *ulParamSize* структуры DBPARAMINFO имеет значение ~0.  
  
 Объект-получатель затем запрашивает дополнительные свойства (имя каталога для типа табличного параметра, имя схемы для типа табличного параметра, имя типа табличного параметра, порядок столбцов и столбцы по умолчанию) с помощью ISSCommandWithParameters::GetParameterProperties.  
  
 После того как имя типа стало известно, для получения сведений об отдельном столбце потребитель должен либо вызвать метод IOpenRowset::OpenRowset, либо получить набор строк DBSCHEMA_TABLE_TYPE_COLUMNS, указав имя типа возвращающего табличное значение параметра в качестве имени таблицы.  
  
## <a name="see-also"></a>См. также  
 [Возвращающие табличные значения параметры &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)   
 [Использование возвращающих табличные значения параметров &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
