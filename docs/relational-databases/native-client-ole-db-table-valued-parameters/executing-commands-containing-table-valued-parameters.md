---
title: "Выполнение команд, содержащих возвращающие табличные значения параметров | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-ole-db-table-valued-parameters
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: table-valued parameters, executing commands containing
ms.assetid: 7ecba6f6-fe7a-462a-9aa3-d5115b6d4529
caps.latest.revision: "26"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: bc8b3028650775501f466987f23da78e9d71d5f3
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="executing-commands-containing-table-valued-parameters"></a>Выполняет команды, содержащие возвращающие табличное значение параметры
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Выполнение команд, содержащих возвращающие табличное значение параметры, проводится в две стадии.  
  
1.  Задать тип параметра.  
  
2.  Выполнить привязку данных параметра.  
  
## <a name="table-valued-parameter-specification"></a>Спецификация возвращающих табличные значения параметров  
 Потребитель может указать тип возвращающего табличные значения параметра. В эту информацию входит имя возвращающего табличное значение параметра. Кроме того, в нее входит имя схемы, если тип определенной пользователем таблицы для возвращающего табличное значение параметра не входит в текущую используемую по умолчанию схему соединения. В зависимости от поддержки на сервере потребитель может также указать необязательную информацию о метаданных (например, упорядочение столбцов), и указать, что все строки конкретных столбцов имеют значения по умолчанию.  
  
 Чтобы задать параметр, возвращающие табличные значения, потребитель вызывает ISSCommandWithParamter::SetParameterInfo, а при необходимости ISSCommandWithParameters::SetParameterProperties. Для возвращающего табличное значение параметра *pwszDataSourceType* поле в структуре DBPARAMBINDINFO имеет значение DBTYPE_TABLE. *UlParamSize* имеет значение ~ 0 указывает, что длина неизвестна. Конкретные свойства параметров, возвращающих табличные значения, таких как имя схемы, имя типа, порядок столбцов и столбцов по умолчанию можно задать с помощью ISSCommandWithParameters::SetParameterProperties.  
  
## <a name="table-valued-parameter-binding"></a>Привязка возвращающих табличные значения параметров  
 Возвращающий табличное значение параметр может представлять собой любой объект — набор рядов. Поставщик читает этот объект при отправке возвращающих табличное значение параметров на сервер во время выполнения.  
  
 Чтобы привязать табличное значение параметра, потребитель вызывает IAccessor::CreateAccessor. *WType* структуры DBBINDING табличное значение параметра задано значение DBTYPE_TABLE. *PObject* структуры DBBINDING отлично от NULL и *pObject* *iid* член имеет значение IID_IRowset или любого другого объекта набора строк возвращающего табличное значение параметра интерфейсы. Остальным полям структуры DBBINDING значения присваиваются так же, как для объектов BLOB с потоковым обновлением.  
  
 При привязке возвращающего табличное значение параметра и связанного с ним объекта набора строк действуют следующие ограничения.  
  
-   Для данных столбцов набора строк возвращающего табличное значение параметра допускаются только состояния DBSTATUS_S_ISNULL и DBSTATUS_S_OK. Передача значения DBSTATUS_S_DEFAULT приведет к ошибке, и состоянию привязки будет присвоено значение DBSTATUS_E_BADSTATUS.  
  
-   Возвращающий табличное значение параметр может иметь значение состояния DBSTATUS_S_DEFAULT. Допускаются только значения DBSTATUS_S_DEFAULT и DBSTATUS_S_OK. Если состояние равно DBSTATUS_S_DEFAULT, возвращающий табличное значение параметр соответствует пустой таблице.  
  
-   Столбцы «только для чтения» возвращающего табличное значение параметра (столбцы-идентификаторы и вычисляемые столбцы) должны быть помечены как значения по умолчанию с помощью свойства SSPROP_PARAM_TABLE_DEFAULT_COLUMNS. Столбцы, имеющие значения по умолчанию, следует также пометить как значения по умолчанию с помощью свойства SSPROP_PARAM_TABLE_DEFAULT_COLUMNS, чтобы их можно было использовать как значения данных столбца для конкретного возвращающего табличное значение параметра. Поставщик не учитывает значения данных, привязанные к столбцам, помеченным как столбцы по умолчанию.  
  
-   Данные для столбцов с атрибутом DPPROP_COL_AUTOINCREMENT или SSPROP_COL_COMPUTED будут переданы на сервер, за исключением столбцов, для которых также задан атрибут SSPROP_PARAM_TABLE_DEFAULT.  
  
## <a name="see-also"></a>См. также:  
 [Возвращающие табличные значения параметры &#40; OLE DB &#41;](../../relational-databases/native-client-ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)   
 [Использование возвращающих табличные значения параметры &#40; OLE DB &#41;](../../relational-databases/native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
