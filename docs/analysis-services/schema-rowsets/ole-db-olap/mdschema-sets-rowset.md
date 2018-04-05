---
title: MDSCHEMA_SETS, набор строк | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
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
ms.openlocfilehash: d861c23e40464535fbde4b666c2e1429f65c772c
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="mdschemasets-rowset"></a>MDSCHEMA_SETS
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Описывает любые наборы, определенные в данный момент в базе данных, включая наборы с областью сеанса.  
  
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
|**CATALOG_NAME**|**DBTYPE_WSTR**|Необязательный параметр.|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|Необязательный параметр.|  
|**CUBE_NAME**|**DBTYPE_WSTR**|Необязательный параметр.|  
|**SET_NAME**|**DBTYPE_WSTR**|Необязательный параметр.|  
|**ОБЛАСТЬ ДЕЙСТВИЯ**|**DBTYPE_I4**|Необязательный параметр.|  
|**HIERARCHY_UNIQUE_NAME**|**DBTYPE_WSTR**|Необязательный параметр.|  
|**CUBE_SOURCE**|**DBTYPE_UI2**|Необязательный параметр.<br /><br /> Примечание: Только одна иерархия может быть включено, и возвращаются только тех именованных наборов, иерархии которых точно соответствуют ограничению.|  
  
## <a name="see-also"></a>См. также:  
 [Наборы строк схемы OLE DB для OLAP](../../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)  
  
  
