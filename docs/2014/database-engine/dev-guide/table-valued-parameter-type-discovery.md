---
title: Обнаружение типа возвращающего табличное значение параметра | Документы Microsoft
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
- table-valued parameters, type discovery
ms.assetid: f55818c2-ebb5-4cf6-8c0c-0da41f592560
caps.latest.revision: 20
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: eea5d45c4c21b740a3ea91ee27023129b33719b3
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36096900"
---
# <a name="table-valued-parameter-type-discovery"></a>Обнаружение типа возвращающего табличное значение параметра
  Потребитель — то есть, клиентское приложение, использующее [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщиком Native Client OLE DB — может определить тип каждого параметра команды, если текст команды задано для поставщика OLE DB. Выяснив тип параметра, возвращающие табличные значения, потребитель может определить сведения метаданных для каждого отдельного столбца, возвращающих табличные значения параметра.  
  
 Сведения о типе параметров процедур поддерживается ICommandWithParameters::GetParameterInfo для большинства типов параметров. Начиная с версии [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], с появлением определяемых пользователем типов и `xml` тип данных GetParameterInfo-метод недостаточно для этой цели, так как невозможно для предоставления информации для определяемых пользователем типов (имя, схемы, и каталог) через ICommandWithParameters. Новый интерфейс ISSCommandWithParameters, был определен для предоставления расширенных сведений о типе.  
  
 Для параметров, возвращающих табличные значения также использовать интерфейс ISSCommandWithParameters для получения подробных сведений. Клиент вызывает ISSCommandWithParameters::GetParameterInfo после подготовки объекта команды. Для возвращающих табличное значение параметров *wType* член структуры DBPARAMINFO имеет значение DBTYPE_TABLE поставщиком. *UlParamSize* структуры DBPARAMINFO имеет значение ~ 0.  
  
 Затем потребитель запрашивает дополнительные свойства (имя каталога табличное значение параметра типа, имя схемы табличное значение параметра типа, имя типа возвращающего табличное значение параметра, порядок столбцов и столбцов по умолчанию) с помощью ISSCommandWithParamters:: GetParameterProperties.  
  
 Для получения сведений о отдельных столбцов, которые пользователь должен либо вызвать Выяснив имя типа, IOpenRowset::OpenRowsetor получить набор строк DBSCHEMA_TABLE_TYPE_COLUMNS, указав имя типа возвращающего табличное значение параметра как имя таблицы.  
  
## <a name="see-also"></a>См. также  
 [Возвращающие табличные значения параметров &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)   
 [Использование возвращающих табличные значения параметров &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  