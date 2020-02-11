---
title: 'Метод ISSAsynchStatus:: Abort (OLE DB) | Документация Майкрософт'
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apiname:
- ISSAsynchStatus::Abort (OLE DB)
apitype: COM
helpviewer_keywords:
- Abort method
ms.assetid: 2a4bd312-839a-45a8-a299-fc8609be9a2a
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 7250c27e2ce35abbd15fc334f4f0ac07e94e985b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "73789527"
---
# <a name="issasynchstatusabort-ole-db"></a>ISSAsynchStatus::Abort (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Отменяет операцию асинхронного выполнения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
HRESULT Abort(  
        HCHAPTER hChapter,  
        DBASYNCHOP eOperation);  
```  
  
## <a name="arguments"></a>Аргументы  
 *параметру hChapter*[in]  
 Дескриптор раздела, для которого прерывается операция. Если вызываемый объект не является объектом набора строк или операция не применяется к разделу, вызывающий должен установить параметру *hChapter* значение DB_NULL_HCHAPTER.  
  
 *eoperation отличного*[in]  
 Операция, которая должна быть прервана. Это должно быть следующее значение.  
  
 DBASYNCHOP_OPEN — запрос на отмену применяется к асинхронному открытию или заполнению набора строк или асинхронной инициализации объекта источника данных.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 S_OK  
 Запрос на отмену асинхронной операции обработан. Это не гарантирует, что сама операция была отменена. Чтобы определить, отменена ли операция, потребитель должен вызвать метод [ISSAsynchStatus::GetStatus](../../relational-databases/native-client-ole-db-interfaces/issasynchstatus-getstatus-ole-db.md) и проверить наличие DB_E_CANCELED; однако это значение может быть не возвращено уже в следующем вызове.  
  
 DB_E_CANTCANCEL  
 Асинхронную операцию невозможно отменить.  
  
 DB_E_CANCELED  
 Запрос на прерывание асинхронной операции был отменен во время отправки уведомлений. Операция все еще выполняется асинхронно.  
  
 E_FAIL  
 Произошла ошибка, зависящая от поставщика.  
  
 E_INVALIDARG  
 Значение параметра *hChapter* не равно DB_NULL_HCHAPTER или значение параметра *eOperation* не равно DBASYNCH_OPEN.  
  
 E_UNEXPECTED  
 **Метод ISSAsynchStatus:: Abort** был вызван для объекта источника данных, для которого **IDBInitialize:: Initialize** не был вызван или не завершен.  
  
 **Метод ISSAsynchStatus:: Abort** был вызван для объекта источника данных, для которого была вызвана **IDBInitialize:: Initialize** , но впоследствии была отменена до инициализации или истекло время ожидания. Объект источника данных все еще не инициализирован.  
  
 **Метод ISSAsynchStatus:: Abort** был вызван для набора строк, в котором ранее вызывался метод **ITransaction:: Commit** или **ITransaction:: Abort** , а набор строк не сохранил фиксацию или прерывание и находится в состоянии зомби.  
  
 **Метод ISSAsynchStatus:: Abort** был вызван для набора строк, который асинхронно отменен на этапе инициализации. Набор строк находится в состоянии зомби.  
  
## <a name="remarks"></a>Remarks  
 При прерывании инициализации набора строк или объекта источника данных набор строк или объект источника данных может перейти в состояние зомби, когда все методы, кроме методов **IUnknown** , возвращают E_UNEXPECTED. В этом случае единственным возможным для потребителя действием является освобождение набора строк или объекта источника данных.  
  
 При вызове интерфейса **ISSAsynchStatus::Abort** и передаче параметру *eOperation* значения, отличного от DBASYNCHOP_OPEN, возвращается S_OK. Это не подразумевает, что сама операция была завершена или отменена.  
  
## <a name="see-also"></a>См. также:  
 [Выполнение асинхронных операций](../../relational-databases/native-client/features/performing-asynchronous-operations.md)  
  
  
