---
title: MDSCHEMA_SETS, набор строк | Документы Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 666f8aa8889f2d15e9e62499e41ad9c0bc69fcff
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="mdschemasets-rowset"></a>MDSCHEMA_SETS
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Описывает любые наборы, определенные на текущий момент в базе данных, в том числе наборы с областью сеанса.  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 **MDSCHEMA_SETS** набор строк содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Описание|  
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
  
## <a name="see-also"></a>См. также  
 [OLE DB для OLAP наборы строк схемы](../../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)  
  
  
