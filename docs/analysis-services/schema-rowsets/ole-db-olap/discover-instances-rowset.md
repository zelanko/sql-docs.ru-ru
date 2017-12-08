---
title: "Набор строк DISCOVER_INSTANCES | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: schema-rowsets
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: DISCOVER_INSTANCES
apitype: NA
applies_to: SQL Server 2016 Preview
helpviewer_keywords: DISCOVER_INSTANCES rowset
ms.assetid: e0842e63-089d-468d-869f-634da343d9fb
caps.latest.revision: "30"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 4f5bcf5b090b1fb011ce4676b320291515044fd7
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="discoverinstances-rowset"></a>Набор строк DISCOVER_INSTANCES
  Описывает экземпляры на сервере.  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 Набор строк **DISCOVER_INSTANCES** содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Длина|Description|  
|-----------------|--------------------|------------|-----------------|  
|**ИМЯ_ЭКЗЕМПЛЯРА**|**DBTYPE_WSTR**||Имя экземпляра.|  
|**INSTANCE_PORT_NUMBER**|**DBTYPE_I4**||Номер порта, который прослушивается экземпляром.|  
|**INSTANCE_STATE**|**DBTYPE_I4**||Состояние экземпляра сервера:<br /><br /> **К работе**<br /><br /> **Остановлено**<br /><br /> **Запуск**<br /><br /> **Остановка**<br /><br /> **Пауза**|  
  
 Этот набор строк схемы не отсортирован.  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 Набор строк **DISCOVER_INSTANCES** может быть ограничен столбцами, перечисленными в следующей таблице.  
  
|Имя столбца|Индикатор типа|Состояние ограничения|  
|-----------------|--------------------|-----------------------|  
|**ИМЯ_ЭКЗЕМПЛЯРА**|**DBTYPE_WSTR**|Необязательно.|  
  
## <a name="see-also"></a>См. также:  
 [Наборы строк схемы OLE DB для OLAP](../../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)  
  
  
