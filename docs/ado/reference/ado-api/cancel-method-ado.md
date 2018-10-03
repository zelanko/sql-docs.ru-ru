---
title: Метод Cancel (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset20::Cancel
- _Record::Cancel
- _Connection::Cancel
- Command25::Cancel
- _Stream::Cancel
helpviewer_keywords:
- Cancel method [ADO]
ms.assetid: e0db4e15-6787-41e2-8f13-9e9b524d620a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9723b28ff56f4fe8eced52cecc43d58921d101e9
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47760788"
---
# <a name="cancel-method-ado"></a>Метод Cancel (ADO)
Отменяет выполнение вызова асинхронного метода, ожидающих утверждения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object.Cancel  
```  
  
## <a name="remarks"></a>Примечания  
 Используйте **отменить** метод для завершения выполнения асинхронный вызов метода: то есть метод вызван с **adAsyncConnect**, **adAsyncExecute**, или **adAsyncFetch** параметр.  
  
 В следующей таблице показано, какие задачи она прекращается при использовании **отменить** метод определенного типа объекта.  
  
|Если *объект* —|Последний асинхронного вызова этого метода завершается|  
|----------------------|-------------------------------------------------------------|  
|[Command](../../../ado/reference/ado-api/command-object-ado.md)|[Выполнение](../../../ado/reference/ado-api/execute-method-ado-command.md)|  
|[Соединение](../../../ado/reference/ado-api/connection-object-ado.md)|[Выполнение](../../../ado/reference/ado-api/execute-method-ado-connection.md) или [Open](../../../ado/reference/ado-api/open-method-ado-connection.md)|  
|[Запись](../../../ado/reference/ado-api/record-object-ado.md)|[Примеры CopyRecord](../../../ado/reference/ado-api/copyrecord-method-ado.md), [DeleteRecord](../../../ado/reference/ado-api/deleterecord-method-ado.md), [MoveRecord](../../../ado/reference/ado-api/moverecord-method-ado.md), или [Open](../../../ado/reference/ado-api/open-method-ado-record.md)|  
|[Набор записей](../../../ado/reference/ado-api/recordset-object-ado.md)|[Открытие](../../../ado/reference/ado-api/open-method-ado-recordset.md)|  
|[поток](../../../ado/reference/ado-api/stream-object-ado.md)|[Открытие](../../../ado/reference/ado-api/open-method-ado-stream.md)|  
  
## <a name="applies-to"></a>Объект применения  
  
||||  
|-|-|-|  
|[Объект Command (ADO)](../../../ado/reference/ado-api/command-object-ado.md)|[Объект Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)|[Объект Record (ADO)](../../../ado/reference/ado-api/record-object-ado.md)|  
|[Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|[Объект Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)||  
  
## <a name="see-also"></a>См. также  
 [Пример метода Cancel (Visual Basic)](../../../ado/reference/ado-api/cancel-method-example-vb.md)   
 [Пример метода Cancel (VBScript)](../../../ado/reference/rds-api/cancel-method-example-vbscript.md)   
 [Пример метода Cancel (Visual C++)](../../../ado/reference/ado-api/cancel-method-example-vc.md)   
 [Метод Cancel (служба удаленных рабочих СТОЛОВ)](../../../ado/reference/rds-api/cancel-method-rds.md)   
 [Метод CancelBatch (ADO)](../../../ado/reference/ado-api/cancelbatch-method-ado.md)   
 [Метод CancelUpdate (ADO)](../../../ado/reference/ado-api/cancelupdate-method-ado.md)   
 [Метод CancelUpdate (служба удаленных рабочих СТОЛОВ)](../../../ado/reference/rds-api/cancelupdate-method-rds.md)   
 [Выполнение метода (объект Command ADO)](../../../ado/reference/ado-api/execute-method-ado-command.md)   
 [Выполнение метода (объект Connection ADO)](../../../ado/reference/ado-api/execute-method-ado-connection.md)   
 [Метод Open (объект Connection ADO)](../../../ado/reference/ado-api/open-method-ado-connection.md)   
 [Метод Open (объект Recordset ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md)
