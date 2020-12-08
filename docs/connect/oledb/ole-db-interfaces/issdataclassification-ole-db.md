---
title: ISSDataClassification | Документация Майкрософт
description: Интерфейс ISSDataClassification
ms.custom: ''
ms.date: 09/30/2020
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
apiname:
- ISSDataClassification
apitype: COM
helpviewer_keywords:
- ISSDataClassification interface
author: bazizi
ms.author: v-beaziz
ms.openlocfilehash: 328110f81f993c66a9455324ff8ec830b329b41b
ms.sourcegitcommit: 0e0cd9347c029e0c7c9f3fe6d39985a6d3af967d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/02/2020
ms.locfileid: "96506663"
---
# <a name="issdataclassification"></a>ISSDataClassification
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW](../../../includes/applies-to-version/sql-asdb-asa.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Интерфейс **ISSDataClassification** предоставляет функции, позволяющие получить сведения о классификации конфиденциальных данных для активного набора строк, полученного от SQL Server.
  

## <a name="methods"></a>Методы

|Метод|Описание|  
|------------|-----------------|  
|[ISSDataClassification::GetSensitivityClassification](../../oledb/ole-db-interfaces/issdataclassification-getsensitivityclassification-ole-db.md)|Возвращает указатель на структуру SENSITIVITYCLASSIFICATION, содержащую сведения о классификации конфиденциальных данных.|  

## <a name="see-also"></a>См. также:  
 [Интерфейсы (OLE DB)](../../oledb/ole-db-interfaces/oledb-driver-for-sql-server-ole-db-interfaces.md)   
 [Наборы строк](../ole-db-rowsets/rowsets.md)   
 [Использование классификации данных](../features/using-data-classification.md)
