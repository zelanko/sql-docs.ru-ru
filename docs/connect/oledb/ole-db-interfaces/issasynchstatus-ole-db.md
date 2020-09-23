---
title: ISSAsynchStatus (драйвер OLE DB) | Документация Майкрософт
description: Узнайте, как OLE DB Driver for SQL Server использует интерфейс ISSAsynchStatus для поддержки асинхронных операций SQL Server.
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
apiname:
- ISSAsynchStatus (OLE DB)
apitype: COM
helpviewer_keywords:
- ISSAsynchStatus interface
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1cc7d83cd9d014e863493365345b8f399f2ee713
ms.sourcegitcommit: c95f3ef5734dec753de09e07752a5d15884125e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/25/2020
ms.locfileid: "88862178"
---
# <a name="issasynchstatus-ole-db"></a>ISSAsynchStatus (OLE DB)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Интерфейс **ISSAsynchStatus** в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поддерживает асинхронные операции. Этот необязательный интерфейс наследует основной интерфейс OLE DB — **IDBAsynchStatus**. Помимо методов **Abort** и **GetStatus** , унаследованных от **IDBAsynchStatus**, **ISSAsynchStatus** предоставляет один новый метод, который используется для ожидания конца асинхронной операции или истечения назначенного времени.  
  
|Метод|Description|  
|------------|-----------------|  
|[ISSAsynchStatus::Abort (OLE DB)](../../oledb/ole-db-interfaces/issasynchstatus-abort-ole-db.md)|Отменяет операцию асинхронного выполнения.|  
|[ISSAsynchStatus::Abort (OLE DB)](../../oledb/ole-db-interfaces/issasynchstatus-getstatus-ole-db.md)|Возвращает состояние операции асинхронного выполнения.|  
|[ISSAsynchStatus::WaitForAsynchCompletion (OLE DB)](../../oledb/ole-db-interfaces/issasynchstatus-waitforasynchcompletion-ole-db.md)|Ждет завершения синхронной операции или истечения назначенного времени.|  
  
## <a name="remarks"></a>Remarks  
 Реализация метода **ISSAsynchStatus::GetStatus** в интерфейсе **ISSAsynchStatus** аналогична методу **IDBAsynchStatus::GetStatus** , за одним исключением: если инициализация объекта источника данных прервана преждевременно, возвращается не DB_E_CANCELED, а E_UNEXPECTED (хотя **ISSAsynchStatus::WaitForAsynchCompletion** возвращает DB_E_CANCELED). Это происходит потому, что объект источника данных не остается в обычном состоянии, следующем за аварийным прерыванием операции, чтобы можно было предпринимать новые попытки инициализации.  
  
 Следующие методы поддерживают асинхронное выполнение в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]:  
  
-   **ICommand::Execute**  
  
-   **IOpenRowset::OpenRowset**  
  
-   **IMultipleResults::GetResult**  
  
## <a name="see-also"></a>См. также:  
 [Интерфейсы (OLE DB)](../../oledb/ole-db-interfaces/oledb-driver-for-sql-server-ole-db-interfaces.md)    
 [Выполнение асинхронных операций](../../oledb/features/performing-asynchronous-operations.md)  
  
  
