---
title: Обнаружение метаданных | Документы Microsoft
description: Обнаружение метаданных в драйвер OLE DB для SQL Server
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|features
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 3980b8064b565dc09ebb79e9d81be9c6f85fc21a
ms.sourcegitcommit: 354ed9c8fac7014adb0d752518a91d8c86cdce81
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/14/2018
ms.locfileid: "35611639"
---
# <a name="metadata-discovery"></a>Обнаружение метаданных
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Улучшенное обнаружение метаданных в [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] позволяет драйвер OLE DB для приложений SQL Server, чтобы убедиться, что столбец или идентична метаданные параметров, возвращенные в результате выполнения запроса или совместимые с форматом метаданных, указанным перед началом выполнить запрос. Если формат метаданных, возвращенных в результате выполнения запроса, будет несовместим с форматом, указанным до выполнения запроса, возвращается ошибка.  
  
 В программе bcp и интерфейсах IBCPSession и IBCPSession2, теперь можно задавать отложенное чтение (отложенное обнаружение метаданных), чтобы избежать обнаружения метаданных для операций. Это позволяет повысить производительность и устранить ошибки обнаружения метаданных.  
  
 При разработке приложения с помощью драйвера OLE DB для SQL Server, но подключиться к версии сервера более ранней, чем [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], обнаружение метаданных, функциональные возможности будут соответствовать версии сервера.  
  
## <a name="remarks"></a>Примечания   
 В [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] были изменены следующие методы OLE DB, которые теперь обеспечивают улучшенное обнаружение метаданных:  
  
-   IColumnsInfo::GetColumnInfo  
  
-   IColumnsRowset::GetColumnsRowset  
  
-   ICommandWithParameters::GetParameterInfo (см. [ICommandWithParameters](../../oledb/ole-db-interfaces/icommandwithparameters.md) Дополнительные сведения)  
  
 Вы также увидите более высокую производительность при указании формата метаданных с помощью IBCPSession::BCPSetBulkMode  
  
 Улучшенное обнаружение метаданных в драйвер OLE DB для SQL Server невозможна из-за добавления двух хранимых процедур в [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]:  
  
-   sp_describe_first_result_set  
  
-   sp_describe_undeclared_parameters  
  
## <a name="see-also"></a>См. также  
 [Возможности драйвера OLE DB для SQL Server](../../oledb/features/oledb-driver-for-sql-server-features.md)  
  
  
