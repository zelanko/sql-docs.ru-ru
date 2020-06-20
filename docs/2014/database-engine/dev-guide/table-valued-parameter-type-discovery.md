---
title: Обнаружение типа для возвращающего табличное значение параметра | Документация Майкрософт
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
ms.openlocfilehash: ab8d837e4ddf74256e4bae70f772557ec8ff67f7
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84933255"
---
# <a name="table-valued-parameter-type-discovery"></a>Обнаружение типа возвращающего табличное значение параметра
  Потребитель, то есть клиентское приложение, использующее [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB собственного клиента, может определить тип каждого параметра команды, если текст команды был передан поставщику OLE DB. После того как тип возвращающего табличное значение параметра становится известен, потребитель может определить метаданные для каждого отдельного столбца возвращающего табличное значение параметра.  
  
 Сведения о типе параметров процедур предоставляются методом ICommandWithParameters::GetParameterInfo для большинства типов параметров. Начиная с [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] , с появлением определяемых пользователем типов и `xml` типа данных метод GetParameterInfo недостаточно для этой цели, поскольку было невозможно предоставить сведения о определяемом пользователем типе (имя, схема и каталог) через ICommandWithParameters. Для предоставления расширенных сведений о типе был определен новый интерфейс ISSCommandWithParameters.  
  
 Среди прочего, интерфейс ISSCommandWithParameters позволяет получать подробные сведения для возвращающих табличное значение параметров. Клиент вызывает ISSCommandWithParameters::GetParameterInfo после подготовки объекта команды. Для возвращающих табличные значения параметров элемент *wType* структуры DBPARAMINFO устанавливается поставщиком в значение DBTYPE_TABLE. Поле *ulParamSize* структуры DBPARAMINFO имеет значение ~0.  
  
 Объект-получатель затем запрашивает дополнительные свойства (имя каталога для типа табличного параметра, имя схемы для типа табличного параметра, имя типа табличного параметра, порядок столбцов и столбцы по умолчанию) с помощью ISSCommandWithParameters::GetParameterProperties.  
  
 После того как имя типа стало известно, для получения сведений об отдельном столбце потребитель должен либо вызвать метод IOpenRowset::OpenRowset, либо получить набор строк DBSCHEMA_TABLE_TYPE_COLUMNS, указав имя типа возвращающего табличное значение параметра в качестве имени таблицы.  
  
## <a name="see-also"></a>См. также:  
 [Возвращающие табличное значение параметры &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)   
 [Использование возвращающих табличные значения параметров &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
