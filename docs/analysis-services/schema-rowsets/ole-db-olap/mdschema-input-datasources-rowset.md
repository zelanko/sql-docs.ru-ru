---
title: Набор строк MDSCHEMA_INPUT_DATASOURCES | Документы Microsoft
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
- MDSCHEMA_INPUT_DATASOURCES
apitype: NA
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- MDSCHEMA_INPUT_DATASOURCES rowset
ms.assetid: 12482fd5-16e3-4171-9cb0-76d0d4f5308e
caps.latest.revision: 30
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: e256ec44816db43f61c332a76942d27f63cb676b
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="mdschemainputdatasources-rowset"></a>Набор строк MDSCHEMA_INPUT_DATASOURCES
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Описывает источники данных, определенные в базе данных.  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 Набор строк **MDSCHEMA_INPUT_DATASOURCES** содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Длина|Описание|  
|-----------------|--------------------|------------|-----------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**||Имя каталога, которому принадлежат этот источник данных.|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**||Не поддерживается.|  
|**DATASOURCE_NAME**|**DBTYPE_WSTR**||Имя объекта источника данных.|  
|**DATASOURCE_TYPE**|**DBTYPE_WSTR**||Тип источника данных. Допустимы следующие значения.<br /><br /> **Реляционные**<br /><br /> **OLAP**|  
|**CREATED_ON**|**DBTYPE_DBTIMESTAMP**||Дата создания источника данных.|  
|**LAST_SCHEMA_UPDATE**|**DBTYPE_DBTIMESTAMP**||Дата и время последнего изменения источника данных.|  
|**DESCRIPTION**|**DBTYPE_WSTR**||Понятное описание действия.|  
|**ВРЕМЯ ОЖИДАНИЯ**|**DBTYPE_UI4**||Время ожидания источника данных.|  
  
 Этот набор строк схемы не отсортирован.  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 Набор строк **MDSCHEMA_INPUT_DATASOURCES** может быть ограничен столбцами, перечисленными в следующей таблице.  
  
|Имя столбца|Индикатор типа|Состояние ограничения|  
|-----------------|--------------------|-----------------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|Необязательно.|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|Необязательно.|  
|**DATASOURCE_NAME**|**DBTYPE_WSTR**|Необязательно.|  
|**DATASOURCE_TYPE**|**DBTYPE_WSTR**|Необязательно.|  
  
## <a name="see-also"></a>См. также  
 [OLE DB для OLAP наборы строк схемы](../../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)  
  
  
