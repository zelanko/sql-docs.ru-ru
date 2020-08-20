---
description: Метод ISSAsynchStatus (поставщик собственного клиента OLE DB)
title: Метод ISSAsynchStatus (поставщик собственного клиента OLE DB) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apiname:
- ISSAsynchStatus (OLE DB)
apitype: COM
helpviewer_keywords:
- ISSAsynchStatus interface
ms.assetid: c643f09f-9ccc-4d8b-9243-3cde86c2bd46
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 340360c49d55d62e38c908e914cd81e7fab6d766
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88490843"
---
# <a name="issasynchstatus-native-client-ole-db-provider"></a>Метод ISSAsynchStatus (поставщик собственного клиента OLE DB)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Интерфейс**ISSAsynchStatus** в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает асинхронные операции. Этот необязательный интерфейс наследует основной интерфейс OLE DB — **IDBAsynchStatus**. Помимо методов **Abort** и **GetStatus** , унаследованных от **IDBAsynchStatus**, **ISSAsynchStatus** предоставляет один новый метод, который используется для ожидания конца асинхронной операции или истечения назначенного времени.  
  
|Метод|Description|  
|------------|-----------------|  
|[ISSAsynchStatus::Abort (OLE DB)](../../relational-databases/native-client-ole-db-interfaces/issasynchstatus-abort-ole-db.md)|Отменяет операцию асинхронного выполнения.|  
|[ISSAsynchStatus::Abort (OLE DB)](../../relational-databases/native-client-ole-db-interfaces/issasynchstatus-getstatus-ole-db.md)|Возвращает состояние операции асинхронного выполнения.|  
|[ISSAsynchStatus::WaitForAsynchCompletion (OLE DB)](../../relational-databases/native-client-ole-db-interfaces/issasynchstatus-waitforasynchcompletion-ole-db.md)|Ждет завершения синхронной операции или истечения назначенного времени.|  
  
## <a name="remarks"></a>Remarks  
 Реализация метода **ISSAsynchStatus::GetStatus** в интерфейсе **ISSAsynchStatus** аналогична методу **IDBAsynchStatus::GetStatus** , за одним исключением: если инициализация объекта источника данных прервана преждевременно, возвращается не DB_E_CANCELED, а E_UNEXPECTED (хотя **ISSAsynchStatus::WaitForAsynchCompletion** возвращает DB_E_CANCELED). Это происходит потому, что объект источника данных не остается в обычном состоянии, следующем за аварийным прерыванием операции, чтобы можно было предпринимать новые попытки инициализации.  
  
 Следующие методы поддерживают асинхронное выполнение в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
-   **ICommand::Execute**  
  
-   **IOpenRowset::OpenRowset**  
  
-   **IMultipleResults::GetResult**  
  
## <a name="see-also"></a>См. также:  
 [Интерфейсы (OLE DB)](https://msdn.microsoft.com/library/34c33364-8538-45db-ae41-5654481cda93)   
 [Выполнение асинхронных операций](../../relational-databases/native-client/features/performing-asynchronous-operations.md)  
  
  
