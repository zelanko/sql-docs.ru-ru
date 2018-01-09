---
title: "Набор строк DISCOVER_KEYWORDS (OLE DB для OLAP) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: DISCOVER_KEYWORDS
apitype: NA
applies_to: SQL Server 2016 Preview
helpviewer_keywords: DISCOVER_KEYWORDS rowset
ms.assetid: 70cc680d-9530-469b-8a61-4e6779aec17a
caps.latest.revision: "12"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 896aad63ea49741e91b728b688812cf0c5f22e08
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="discoverkeywords-rowset-ole-db-for-olap"></a>Набор строк DISCOVER_KEYWORDS (OLE DB для OLAP)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Перечисляет список слов, зарезервированных поставщиком.  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 Набор строк DISCOVER_KEYWORDS содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Длина|Description|  
|-----------------|--------------------|------------|-----------------|  
|**Ключевое слово**|**DBTYPE_WSTR**||Зарезервированное ключевое слово.|  
  
 Этот набор строк схемы не отсортирован.  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 Набор строк DISCOVER_KEYWORDS может быть ограничен столбцами, перечисленными в следующей таблице.  
  
|Имя столбца|Индикатор типа|Состояние ограничения|  
|-----------------|--------------------|-----------------------|  
|**Ключевое слово**|**DBTYPE_WSTR**|Необязательный параметр.|  
  
## <a name="see-also"></a>См. также:  
 [Наборы строк схемы OLE DB для OLAP](../../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)  
  
  
