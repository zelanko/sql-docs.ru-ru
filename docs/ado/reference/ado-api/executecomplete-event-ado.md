---
description: Событие ExecuteComplete (ADO)
title: Событие Ексекутекомплете (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection::ExecuteComplete
- ExecuteComplete
helpviewer_keywords:
- ExecuteComplete event [ADO]
ms.assetid: 62470d42-e511-494c-bec4-ad4591734b7b
author: rothja
ms.author: jroth
ms.openlocfilehash: 4e7b800f7dba925230ade048f3792020ad8a44ec
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88443846"
---
# <a name="executecomplete-event-ado"></a>Событие ExecuteComplete (ADO)
Событие **ексекутекомплете** вызывается после завершения выполнения команды.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
ExecuteComplete RecordsAffected, pError, adStatus, pCommand, pRecordset, pConnection  
```  
  
#### <a name="parameters"></a>Параметры  
 *RecordsAffected*  
 Значение **типа Long** , указывающее количество записей, затронутых командой.  
  
 *pError*  
 Объект [ошибки](../../../ado/reference/ado-api/error-object.md) . Она описывает ошибку, которая возникла, если значение **адстатус** равно **адстатусеррорсоккурред**; в противном случае он не задан.  
  
 *адстатус*  
 Значение состояния [евентстатусенум](../../../ado/reference/ado-api/eventstatusenum.md) . При вызове этого события этот параметр устанавливается в значение **адстатусок** , если операция, вызвавшая событие, прошла успешно, или значение **адстатусеррорсоккурред** , если операция завершилась ошибкой.  
  
 Перед возвратом этого события задайте для этого параметра значение **адстатусунвантедевент** , чтобы предотвратить появление последующих уведомлений.  
  
 *пкомманд*  
 Выполняемый объект [команды](../../../ado/reference/ado-api/command-object-ado.md) . Содержит объект **Command** , даже если вызывает **Connection.Exeмилые** или **Recordset. Open** без явного создания **команды**. в этом случае объект **команды** создается внутренне ADO.  
  
 *предшнур*  
 Объект [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) , являющийся результатом выполненной команды. Этот **набор записей** может быть пустым. Ни в коем случае не следует уничтожать этот объект Recordset из этого обработчика событий. Это приведет к нарушению прав доступа при попытке ADO получить доступ к объекту, который больше не существует.  
  
 *пконнектион*  
 Объект [соединения](../../../ado/reference/ado-api/connection-object-ado.md) . Соединение, для которого была выполнена операция.  
  
## <a name="remarks"></a>Комментарии  
 Событие **ексекутекомплете** может возникать из-за **соединения.** [Выполните](../../../ado/reference/ado-api/execute-method-ado-connection.md) **команду.** [EXECUTE](../../../ado/reference/ado-api/execute-method-ado-command.md), **набор записей.** [Открыть](../../../ado/reference/ado-api/open-method-ado-recordset.md), **набор записей.** [Requery](../../../ado/reference/ado-api/requery-method.md)или **Recordset.** Методы [NextRecordset](../../../ado/reference/ado-api/nextrecordset-method-ado.md) .  
  
## <a name="see-also"></a>См. также  
 [Пример модели событий ADO (Visual c++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [Общие сведения об обработчике событий ADO](../../../ado/guide/data/ado-event-handler-summary.md)
