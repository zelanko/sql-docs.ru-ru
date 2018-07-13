---
title: ISSAsynchStatus (OLE DB) | Документация Майкрософт
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- ISSAsynchStatus (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- ISSAsynchStatus interface
ms.assetid: c643f09f-9ccc-4d8b-9243-3cde86c2bd46
caps.latest.revision: 32
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a112c19d78c4d59b68ea5896109f88a101aaad13
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37413413"
---
# <a name="issasynchstatus-ole-db"></a>ISSAsynchStatus (OLE DB)
  **ISSAsynchStatus** обеспечивает поддержку [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] асинхронных операций. Этот необязательный интерфейс наследует основной интерфейс OLE DB — **IDBAsynchStatus**. Помимо методов **Abort** и **GetStatus** , унаследованных от **IDBAsynchStatus**, **ISSAsynchStatus** предоставляет один новый метод, который используется для ожидания конца асинхронной операции или истечения назначенного времени.  
  
|Метод|Описание|  
|------------|-----------------|  
|[ISSAsynchStatus::Abort &#40;OLE DB&#41;](issasynchstatus-abort-ole-db.md)|Отменяет операцию асинхронного выполнения.|  
|[ISSAsynchStatus::GetStatus &#40;OLE DB&#41;](issasynchstatus-getstatus-ole-db.md)|Возвращает состояние операции асинхронного выполнения.|  
|[ISSAsynchStatus::WaitForAsynchCompletion &#40;OLE DB&#41;](issasynchstatus-waitforasynchcompletion-ole-db.md)|Ждет завершения синхронной операции или истечения назначенного времени.|  
  
## <a name="remarks"></a>Примечания  
 Реализация метода **ISSAsynchStatus::GetStatus** в интерфейсе **ISSAsynchStatus** аналогична методу **IDBAsynchStatus::GetStatus** , за одним исключением: если инициализация объекта источника данных прервана преждевременно, возвращается не DB_E_CANCELED, а E_UNEXPECTED (хотя **ISSAsynchStatus::WaitForAsynchCompletion** возвращает DB_E_CANCELED). Это происходит потому, что объект источника данных не остается в обычном состоянии, следующем за аварийным прерыванием операции, чтобы можно было предпринимать новые попытки инициализации.  
  
 Следующие методы поддерживают асинхронное выполнение в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
-   **ICommand::Execute**  
  
-   **IOpenRowset::OpenRowset**  
  
-   **IMultipleResults::GetResult**  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы &#40;OLE DB&#41;](../../database-engine/dev-guide/interfaces-ole-db.md)   
 [Выполнение асинхронных операций](../native-client/features/performing-asynchronous-operations.md)  
  
  
