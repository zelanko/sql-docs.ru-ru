---
title: Обнаружение типа возвращающего табличное значение параметра | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- table-valued parameters, type discovery
ms.assetid: f55818c2-ebb5-4cf6-8c0c-0da41f592560
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 66f2be8633c7070e2458d5c1e1258fe3bcb9f949
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48146724"
---
# <a name="table-valued-parameter-type-discovery"></a>Обнаружение типа возвращающего табличное значение параметра
  Потребитель — то есть клиентское приложение, использующее [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственный поставщик OLE DB клиента, может определить тип каждого параметра команды, если поставщик OLE DB внимание было уделено текст команды. После того как тип возвращающего табличное значение параметра становится известен, потребитель может определить метаданные для каждого отдельного столбца возвращающего табличное значение параметра.  
  
 Сведения о типе параметров процедур поддерживается ICommandWithParameters::GetParameterInfo для большинства типов параметров. Начиная с версии [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], с появлением определяемых пользователем типов и `xml` тип данных, getparameterinfo-метод стало недостаточно для этой цели, так как не удалось указать сведения о пользовательских типах (имя, схемы, и каталог) через ICommandWithParameters. Новый интерфейс ISSCommandWithParameters, был определен для предоставления расширенных сведений о типе.  
  
 Для возвращающих табличные значения параметров также использовать интерфейс ISSCommandWithParameters для обнаружения подробных сведений. Клиент вызывает ISSCommandWithParameters::GetParameterInfo после подготовки объекта команды. Для возвращающих табличное значение параметров *wType* поставщиком член структуры DBPARAMINFO имеет значение DBTYPE_TABLE. Поле *ulParamSize* структуры DBPARAMINFO имеет значение ~0.  
  
 Затем потребитель запрашивает дополнительные свойства (имя каталога типа, имя схемы типа, имя типа возвращающего табличное значение параметра, порядок столбцов и столбцы по умолчанию) с помощью метода ISSCommandWithParamters::GetParameterProperties.  
  
 После того как имя типа стало известно, для получения сведений об отдельном столбце потребитель должен либо вызвать метод IOpenRowset::OpenRowset, либо получить набор строк DBSCHEMA_TABLE_TYPE_COLUMNS, указав имя типа возвращающего табличное значение параметра в качестве имени таблицы.  
  
## <a name="see-also"></a>См. также  
 [Возвращающие табличные значения параметры &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)   
 [Использование возвращающих табличные значения параметров &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
