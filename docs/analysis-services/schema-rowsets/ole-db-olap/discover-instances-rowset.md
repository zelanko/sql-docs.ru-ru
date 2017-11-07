---
title: "Набор строк DISCOVER_INSTANCES | Документы Microsoft"
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
- DISCOVER_INSTANCES
apitype: NA
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- DISCOVER_INSTANCES rowset
ms.assetid: e0842e63-089d-468d-869f-634da343d9fb
caps.latest.revision: 30
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: fbed6de71f83da959591003039fe5910a1a4c53d
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

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
 [OLE DB для OLAP наборы строк схемы](../../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)  
  
  

