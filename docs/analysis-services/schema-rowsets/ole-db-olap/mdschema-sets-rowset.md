---
title: "MDSCHEMA_SETS, набор строк | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- MDSCHEMA_SETS
apitype: NA
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- MDSCHEMA_SETS rowset
ms.assetid: abb00dc0-2b83-48d6-b2ba-6615c1488d06
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 4820c18992da2aab0ac8e0550a5cadd75ca193bc
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="mdschemasets-rowset"></a>MDSCHEMA_SETS
  Описывает любые наборы, определенные на текущий момент в базе данных, в том числе наборы с областью сеанса.  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 **MDSCHEMA_SETS** набор строк содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Description|  
|-----------------|--------------------|-----------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|Имя базы данных.|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|Не поддерживается.|  
|**CUBE_NAME**|**DBTYPE_WSTR**|Имя куба.|  
|**SET_NAME**|**DBTYPE_WSTR**|Имя набора, как указано в **CREATE SET** инструкции.|  
|**ОБЛАСТЬ ДЕЙСТВИЯ**|**DBTYPE_I4**|Область набора:<br /><br /> **MDSET_SCOPE_GLOBAL** (**1**)<br /><br /> **MDSET_SCOPE_SESSION** (**2**)|  
|**DESCRIPTION**|**DBTYPE_WSTR**|Не поддерживается.|  
|**ВЫРАЖЕНИЕ**|**DBTYPE_WSTR**|Выражение для набора.|  
|**ИЗМЕРЕНИЯ**|**DBTYPE_WSTR**|Разделенный запятыми список иерархий, включенных в набор.|  
|**SET_CAPTION**|**DBTYPE_WSTR**|Метка или заголовок, связанный с набором. Метка или заголовок используются главным образом в целях визуального отображения.|  
|**SET_DISPLAY_FOLDER**|**DBTYPE_WSTR**|Строка, определяющая путь к папке отображения, которую клиентское приложение использует для демонстрации набора. Разделитель уровней вложенности папок определяется клиентским приложением. Для средств и клиентов, входящих в [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], обратная косая черта (\\) является разделитель уровней вложенности. Чтобы указать несколько папок отображения, используйте точку с запятой (;) для разделения папок.|  
|**SET_EVALUATION_CONTEXT**|**DBTYPE_I4**|Контекст для набора. Набор может быть статическим или динамическим. Этот столбец может иметь одно из следующих значений.<br /><br /> MDSET_RESOLUTION_STATIC=1<br /><br /> MDSET_RESOLUTION_DYNAMIC=2|  
  
 Набор строк отсортирован по **CATALOG_NAME**, **SCHEMA_NAME**, **CUBE_NAME**.  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 **MDSCHEMA_SETS** строк может быть ограничен столбцами, перечисленными в следующей таблице.  
  
|Имя столбца|Индикатор типа|Состояние ограничения|  
|-----------------|--------------------|-----------------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|Необязательно.|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|Необязательно.|  
|**CUBE_NAME**|**DBTYPE_WSTR**|Необязательно.|  
|**SET_NAME**|**DBTYPE_WSTR**|Необязательно.|  
|**ОБЛАСТЬ ДЕЙСТВИЯ**|**DBTYPE_I4**|Необязательно.|  
|**HIERARCHY_UNIQUE_NAME**|**DBTYPE_WSTR**|Необязательно.|  
|**CUBE_SOURCE**|**DBTYPE_UI2**|Необязательно.<br /><br /> Примечание: Только одна иерархия может быть включено, и возвращаются только тех именованных наборов, иерархии которых точно соответствуют ограничению.|  
  
## <a name="see-also"></a>См. также:  
 [OLE DB для OLAP наборы строк схемы](../../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)  
  
  

