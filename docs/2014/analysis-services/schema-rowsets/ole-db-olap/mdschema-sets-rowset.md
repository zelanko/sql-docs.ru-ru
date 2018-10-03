---
title: Набор строк MDSCHEMA_SETS | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- MDSCHEMA_SETS
topic_type:
- apiref
helpviewer_keywords:
- MDSCHEMA_SETS rowset
ms.assetid: abb00dc0-2b83-48d6-b2ba-6615c1488d06
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1e3008fc6b56146c22a7508398dcc3896a697644
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48059544"
---
# <a name="mdschemasets-rowset"></a>MDSCHEMA_SETS
  Описывает любые наборы, определенные на текущий момент в базе данных, в том числе наборы с областью сеанса.  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 `MDSCHEMA_SETS` Набор строк содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Длина|Описание|  
|-----------------|--------------------|------------|-----------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`||Имя базы данных.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`||Не поддерживается.|  
|`CUBE_NAME`|`DBTYPE_WSTR`||Имя куба.|  
|`SET_NAME`|`DBTYPE_WSTR`||Имя набора, как указано в инструкции `CREATE SET`.|  
|`SCOPE`|`DBTYPE_I4`||Область набора:<br /><br /> -   `MDSET_SCOPE_GLOBAL` (`1`)<br />-   `MDSET_SCOPE_SESSION` (`2`)|  
|`DESCRIPTION`|`DBTYPE_WSTR`||Не поддерживается.|  
|`EXPRESSION`|`DBTYPE_WSTR`||Выражение для набора.|  
|`DIMENSIONS`|`DBTYPE_WSTR`||Разделенный запятыми список иерархий, включенных в набор.|  
|`SET_CAPTION`|`DBTYPE_WSTR`||Метка или заголовок, связанный с набором. Метка или заголовок используются главным образом в целях визуального отображения.|  
|`SET_DISPLAY_FOLDER`|`DBTYPE_WSTR`||Строка, определяющая путь к папке отображения, которую клиентское приложение использует для демонстрации набора. Разделитель уровней вложенности папок определяется клиентским приложением. Для средств и клиентов, входящих [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], обратная косая черта (\\) — это разделитель уровней вложенности. Чтобы указать несколько папок отображения, используйте точку с запятой (;) для разделения папок.|  
|`SET_EVALUATION_CONTEXT`|`DBTYPE_I4`||Контекст для набора. Набор может быть статическим или динамическим.<br /><br /> Этот столбец может иметь одно из следующих значений.<br /><br /> -MDSET_RESOLUTION_STATIC = 1<br />-MDSET_RESOLUTION_DYNAMIC = 2|  
  
 Набор строк отсортирован по `CATALOG_NAME`, `SCHEMA_NAME`, `CUBE_NAME`.  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 Набор строк `MDSCHEMA_SETS` может быть ограничен столбцами, перечисленными в следующей таблице.  
  
|Имя столбца|Индикатор типа|Состояние ограничения|  
|-----------------|--------------------|-----------------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`CUBE_NAME`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`SET_NAME`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`SCOPE`|`DBTYPE_I4`|Необязательный параметр.|  
|`HIERARCHY_UNIQUE_NAME`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`CUBE_SOURCE`|`DBTYPE_UI2`|Необязательный параметр. **Примечание:** только одна иерархия может быть включено, и возвращаются только тех именованных наборов иерархии которых точно соответствуют ограничению.|  
  
## <a name="see-also"></a>См. также  
 [Наборы строк схемы OLE DB для OLAP](ole-db-for-olap-schema-rowsets.md)  
  
  
