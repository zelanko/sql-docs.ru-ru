---
title: ISSAsynchStatus (OLE DB) | Документация Майкрософт
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- ISSAsynchStatus (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- ISSAsynchStatus interface
ms.assetid: c643f09f-9ccc-4d8b-9243-3cde86c2bd46
author: rothja
ms.author: jroth
ms.openlocfilehash: 4489f9d1ad576d49d885842f6969f9b61065791c
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85056131"
---
# <a name="issasynchstatus-ole-db"></a>ISSAsynchStatus (OLE DB)
  Интерфейс**ISSAsynchStatus** в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает асинхронные операции. Этот необязательный интерфейс наследует основной интерфейс OLE DB — **IDBAsynchStatus**. Помимо методов **Abort** и **GetStatus** , унаследованных от **IDBAsynchStatus**, **ISSAsynchStatus** предоставляет один новый метод, который используется для ожидания конца асинхронной операции или истечения назначенного времени.  
  
|Метод|Описание|  
|------------|-----------------|  
|[ISSAsynchStatus::Abort (OLE DB)](issasynchstatus-abort-ole-db.md)|Отменяет операцию асинхронного выполнения.|  
|[ISSAsynchStatus::Abort (OLE DB)](issasynchstatus-getstatus-ole-db.md)|Возвращает состояние операции асинхронного выполнения.|  
|[ISSAsynchStatus::WaitForAsynchCompletion (OLE DB)](issasynchstatus-waitforasynchcompletion-ole-db.md)|Ждет завершения синхронной операции или истечения назначенного времени.|  
  
## <a name="remarks"></a>Remarks  
 Реализация метода **ISSAsynchStatus::GetStatus** в интерфейсе **ISSAsynchStatus** аналогична методу **IDBAsynchStatus::GetStatus** , за одним исключением: если инициализация объекта источника данных прервана преждевременно, возвращается не DB_E_CANCELED, а E_UNEXPECTED (хотя **ISSAsynchStatus::WaitForAsynchCompletion** возвращает DB_E_CANCELED). Это происходит потому, что объект источника данных не остается в обычном состоянии, следующем за аварийным прерыванием операции, чтобы можно было предпринимать новые попытки инициализации.  
  
 Следующие методы поддерживают асинхронное выполнение в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
-   **ICommand::Execute**  
  
-   **IOpenRowset::OpenRowset**  
  
-   **IMultipleResults::GetResult**  
  
## <a name="see-also"></a>См. также:  
 [Интерфейсы &#40;OLE DB&#41;](../../database-engine/dev-guide/interfaces-ole-db.md)   
 [Выполнение асинхронных операций](../native-client/features/performing-asynchronous-operations.md)  
  
  
