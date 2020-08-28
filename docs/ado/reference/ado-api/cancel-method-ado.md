---
description: Метод Cancel (ADO)
title: Метод Cancel (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
ms.openlocfilehash: 75829400fbb1beb838b9254acf7db129980046c3
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88975655"
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
|[Команда](./command-object-ado.md)|[Execute](./execute-method-ado-command.md)|  
|[Соединение](./connection-object-ado.md)|[Выполнить](./execute-method-ado-connection.md) или [Открыть](./open-method-ado-connection.md)|  
|[Запись](./record-object-ado.md)|[Копирекорд](./copyrecord-method-ado.md), [делетерекорд](./deleterecord-method-ado.md), [MoveRecord](./moverecord-method-ado.md)или [Open](./open-method-ado-record.md)|  
|[набор записей](./recordset-object-ado.md)|[Открыть](./open-method-ado-recordset.md)|  
|[Поток](./stream-object-ado.md)|[Открыть](./open-method-ado-stream.md)|  
  
## <a name="applies-to"></a>Применение  

:::row:::
    :::column:::
        [Объект Command (ADO)](./command-object-ado.md)  
        [Объект Connection (ADO)](./connection-object-ado.md)  
    :::column-end:::
    :::column:::
        [Объект Record (ADO)](./record-object-ado.md)  
        [Объект Recordset (ADO)](./recordset-object-ado.md)  
    :::column-end:::
    :::column:::
        [Объект Stream (ADO)](./stream-object-ado.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>См. также  
 [Пример метода Cancel (Visual Basic)](./cancel-method-example-vb.md)   
 [Пример метода Cancel (VBScript)](../rds-api/cancel-method-example-vbscript.md)   
 [Пример метода Cancel (Visual c++)](./cancel-method-example-vc.md)   
 [Метод Cancel (RDS)](../rds-api/cancel-method-rds.md)   
 [Метод CancelBatch (ADO)](./cancelbatch-method-ado.md)   
 [Метод CancelUpdate (ADO)](./cancelupdate-method-ado.md)   
 [Метод CancelUpdate (RDS)](../rds-api/cancelupdate-method-rds.md)   
 [Метод Execute (команда ADO)](./execute-method-ado-command.md)   
 [Метод Execute (соединение ADO)](./execute-method-ado-connection.md)   
 [Метод Open (подключение ADO)](./open-method-ado-connection.md)   
 [Метод Open (объект Recordset ADO)](./open-method-ado-recordset.md)