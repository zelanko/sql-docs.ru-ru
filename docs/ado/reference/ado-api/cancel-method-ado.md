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
author: rothja
ms.author: jroth
ms.openlocfilehash: 25b6de609d286847fe7458353203dd7f4b9c7b4b
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/28/2020
ms.locfileid: "87242430"
---
# <a name="cancel-method-ado"></a>Метод Cancel (ADO)
Отменяет выполнение ожидающего асинхронного вызова метода.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object.Cancel  
```  
  
## <a name="remarks"></a>Remarks  
 Используйте метод **Cancel** для завершения выполнения асинхронного вызова метода, то есть метода, вызываемого с параметром **адасинкконнект**, **адасинцексекуте**или **адасинкфетч** .  
  
 В следующей таблице показано, какая задача завершается при использовании метода **Cancel** для определенного типа объекта.  
  
|Если *объект* является|Последний асинхронный вызов этого метода завершен|  
|----------------------|-------------------------------------------------------------|  
|[Command](../../../ado/reference/ado-api/command-object-ado.md)|[Execute](../../../ado/reference/ado-api/execute-method-ado-command.md)|  
|[Соединение](../../../ado/reference/ado-api/connection-object-ado.md)|[Выполнить](../../../ado/reference/ado-api/execute-method-ado-connection.md) или [Открыть](../../../ado/reference/ado-api/open-method-ado-connection.md)|  
|[Запись](../../../ado/reference/ado-api/record-object-ado.md)|[Копирекорд](../../../ado/reference/ado-api/copyrecord-method-ado.md), [делетерекорд](../../../ado/reference/ado-api/deleterecord-method-ado.md), [MoveRecord](../../../ado/reference/ado-api/moverecord-method-ado.md)или [Open](../../../ado/reference/ado-api/open-method-ado-record.md)|  
|[набор записей](../../../ado/reference/ado-api/recordset-object-ado.md)|[Открыть](../../../ado/reference/ado-api/open-method-ado-recordset.md)|  
|[Поток](../../../ado/reference/ado-api/stream-object-ado.md)|[Открыть](../../../ado/reference/ado-api/open-method-ado-stream.md)|  
  
## <a name="applies-to"></a>Применение  

:::row:::
    :::column:::
        [Объект Command (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
        [Объект Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
    :::column-end:::
    :::column:::
        [Объект Record (ADO)](../../../ado/reference/ado-api/record-object-ado.md)  
        [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
    :::column-end:::
    :::column:::
        [Объект Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>См. также  
 [Пример метода Cancel (Visual Basic)](../../../ado/reference/ado-api/cancel-method-example-vb.md)   
 [Пример метода Cancel (VBScript)](../../../ado/reference/rds-api/cancel-method-example-vbscript.md)   
 [Пример метода Cancel (Visual c++)](../../../ado/reference/ado-api/cancel-method-example-vc.md)   
 [Метод Cancel (RDS)](../../../ado/reference/rds-api/cancel-method-rds.md)   
 [Метод CancelBatch (ADO)](../../../ado/reference/ado-api/cancelbatch-method-ado.md)   
 [Метод CancelUpdate (ADO)](../../../ado/reference/ado-api/cancelupdate-method-ado.md)   
 [Метод CancelUpdate (RDS)](../../../ado/reference/rds-api/cancelupdate-method-rds.md)   
 [Метод Execute (команда ADO)](../../../ado/reference/ado-api/execute-method-ado-command.md)   
 [Метод Execute (соединение ADO)](../../../ado/reference/ado-api/execute-method-ado-connection.md)   
 [Метод Open (подключение ADO)](../../../ado/reference/ado-api/open-method-ado-connection.md)   
 [Метод Open (объект Recordset ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md)
