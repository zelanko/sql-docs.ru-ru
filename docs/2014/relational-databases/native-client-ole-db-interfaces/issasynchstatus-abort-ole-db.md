---
title: ISSAsynchStatus::Abort (OLE DB) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- ISSAsynchStatus::Abort (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- Abort method
ms.assetid: 2a4bd312-839a-45a8-a299-fc8609be9a2a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b61f5e3e44f9584fc3f93efb521585e3173b6c1d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62638720"
---
# <a name="issasynchstatusabort-ole-db"></a>ISSAsynchStatus::Abort (OLE DB)
  Отменяет операцию асинхронного выполнения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
HRESULT Abort(  
  HCHAPTER hChapter,  
  DBASYNCHOP eOperation);  
```  
  
## <a name="arguments"></a>Аргументы  
 *hChapter*[in]  
 Дескриптор раздела, для которого прерывается операция. Если вызываемый объект не является объектом набора строк или операция не применяется к разделу, вызывающий должен установить параметру *hChapter* значение DB_NULL_HCHAPTER.  
  
 *eOperation*[in]  
 Операция, которая должна быть прервана. Это должно быть следующее значение.  
  
 DBASYNCHOP_OPEN — запрос на отмену применяется к асинхронному открытию или заполнению набора строк или асинхронной инициализации объекта источника данных.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 S_OK  
 Запрос на отмену асинхронной операции обработан. Это не гарантирует, что сама операция была отменена. Чтобы определить, отменена ли операция, потребитель должен вызвать метод [ISSAsynchStatus::GetStatus](issasynchstatus-getstatus-ole-db.md) и проверить наличие DB_E_CANCELED; однако это значение может быть не возвращено уже в следующем вызове.  
  
 DB_E_CANTCANCEL  
 Асинхронную операцию невозможно отменить.  
  
 DB_E_CANCELED  
 Запрос на прерывание асинхронной операции был отменен во время отправки уведомлений. Операция все еще выполняется асинхронно.  
  
 E_FAIL  
 Произошла ошибка, зависящая от поставщика.  
  
 E_INVALIDARG  
 Значение параметра *hChapter* не равно DB_NULL_HCHAPTER или значение параметра *eOperation* не равно DBASYNCH_OPEN.  
  
 E_UNEXPECTED  
 Метод**ISSAsynchStatus::Abort** был вызван для объекта источника данных, для которого не был вызван метод **IDBInitialize::Initialize** .  
  
 Метод**ISSAsynchStatus::Abort** был вызван для объекта источника данных, для которого был вызван метод **IDBInitialize::Initialize** , но впоследствии отменен до инициализации, либо истекло время ожидания. Объект источника данных еще не инициализирован.  
  
 Интерфейс**ISSAsynchStatus::Abилиt** был вызван для набора строк, для которого ранее был вызван интерфейс **ITransaction::Commit** или **ITransaction::Abилиt** was previously called, and the rowset did not survive the commit или abилиt and is in a zombie state.  
  
 Интерфейс**ISSAsynchStatus::Abort** был вызван для набора строк, который был асинхронно отменен на стадии его инициализации. Набор строк находится в состоянии зомби.  
  
## <a name="remarks"></a>Примечания  
 При прерывании инициализации набора строк или объекта источника данных набор строк или объект источника данных может перейти в состояние зомби, когда все методы, кроме методов **IUnknown** , возвращают E_UNEXPECTED. В этом случае единственным возможным для потребителя действием является освобождение набора строк или объекта источника данных.  
  
 При вызове интерфейса **ISSAsynchStatus::Abort** и передаче параметру *eOperation* значения, отличного от DBASYNCHOP_OPEN, возвращается S_OK. Это не подразумевает, что сама операция была завершена или отменена.  
  
## <a name="see-also"></a>См. также  
 [Выполнение асинхронных операций](../native-client/features/performing-asynchronous-operations.md)  
  
  
