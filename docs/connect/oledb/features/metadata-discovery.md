---
title: Обнаружение метаданных | Документация Майкрософт
description: Обнаружение метаданных в драйвере OLE DB для SQL Server
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 9891e5708110be83a4ef33cb2a142accaf93ffe2
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67989061"
---
# <a name="metadata-discovery"></a>Обнаружение метаданных
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Улучшенное обнаружение метаданных в [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] позволяет гарантировать, что в приложениях драйвера OLE DB для SQL Server метаданные столбца или параметра, возвращенные в результате выполнения запроса, будут полностью соответствовать формату метаданных, указанному до выполнения запроса, или будут совместимы с ним. Если формат метаданных, возвращенных в результате выполнения запроса, будет несовместим с форматом, указанным до выполнения запроса, возвращается ошибка.  
  
 В функциях bcp, а также интерфейсах IBCPSession и IBCPSession2 теперь можно задавать отложенное чтение (отложенное обнаружение метаданных), чтобы избежать обнаружения метаданных для операций с параметром queryout. Это позволяет повысить производительность и устранить ошибки обнаружения метаданных.  
  
 Если при разработке приложения с помощью драйвера OLE DB для SQL Server выполняется подключение к серверу с версией, более ранней, чем [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], функция обнаружения метаданных будет соответствовать версии сервера.  
  
## <a name="remarks"></a>Remarks   
 В [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] были изменены следующие методы OLE DB, которые теперь обеспечивают улучшенное обнаружение метаданных:  
  
-   IColumnsInfo::GetColumnInfo  
  
-   IColumnsRowset::GetColumnsRowset  
  
-   ICommandWithParameters:: GetParameterInfo (Дополнительные сведения см. в [ICommandWithParameters](../../oledb/ole-db-interfaces/icommandwithparameters.md) )  
  
 Повышение производительности также заметно при указании формата метаданных с помощью метода IBCPSession::BCPSetBulkMode.  
  
 Улучшенное обнаружение метаданных в драйвере OLE DB для SQL Server возможно благодаря добавлению двух хранимых процедур в [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]:  
  
-   sp_describe_first_result_set  
  
-   sp_describe_undeclared_parameters  
  
## <a name="see-also"></a>См. также:  
 [Возможности драйвера OLE DB для SQL Server](../../oledb/features/oledb-driver-for-sql-server-features.md)  
  
  
