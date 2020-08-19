---
description: Метод Close (ADO)
title: Метод Close (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::Close
- _Stream::Close
- _Record::Close
helpviewer_keywords:
- Close method [ADO]
ms.assetid: 3cdf27d1-a180-4cff-8e42-95dec5fb1b55
author: rothja
ms.author: jroth
ms.openlocfilehash: 2cfdee50d0b5699e1f6eca4eb8e22375e4e5a672
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88450956"
---
# <a name="close-method-ado"></a>Метод Close (ADO)
Закрывает открытый объект и все зависимые объекты.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object.Close  
```  
  
## <a name="remarks"></a>Remarks  
 Используйте метод **Close** , чтобы закрыть [соединение](../../../ado/reference/ado-api/connection-object-ado.md), [запись](../../../ado/reference/ado-api/record-object-ado.md), [набор записей](../../../ado/reference/ado-api/recordset-object-ado.md)или объект [потока](../../../ado/reference/ado-api/stream-object-ado.md) , чтобы освободить все связанные системные ресурсы. Закрытие объекта не приводит к его удалению из памяти; можно изменить параметры свойств и открыть его позже. Чтобы полностью исключить объект из памяти, закройте объект и задайте для переменной объекта значение *Nothing* (в Visual Basic).  
  
## <a name="connection"></a>Соединение  
 Использование метода **Close** для закрытия объекта **соединения** также закрывает все активные объекты **набора записей** , связанные с соединением. Объект [команды](../../../ado/reference/ado-api/command-object-ado.md) , связанный с закрываемым объектом **соединения** , будет сохранен, но больше не будет связан с объектом **соединения** . то есть свойство [ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md) будет иметь значение **Nothing**. Кроме того, коллекция [Parameters](../../../ado/reference/ado-api/parameters-collection-ado.md) объекта **команды** будет очищать все параметры, определяемые поставщиком.  
  
 Позже можно вызвать метод [Open](../../../ado/reference/ado-api/open-method-ado-connection.md) для повторного установления соединения с тем же или другим источником данных. Пока объект **соединения** закрыт, вызов всех методов, требующих открытого соединения с источником данных, приведет к ошибке.  
  
 Закрытие объекта **соединения** при наличии открытых объектов **Recordset** в соединении откатывает все ожидающие изменения во всех объектах **набора записей** . Явное закрытие объекта **соединения** (вызов метода **Close** ) во время выполнения транзакции приводит к ошибке. Если объект **соединения** выходит за пределы области действия во время выполнения транзакции, ADO автоматически выполняет откат транзакции.  
  
## <a name="recordset-record-stream"></a>Набор записей, запись, поток  
 Использование метода **Close** для закрытия объекта **Recordset**, **записи**или **потока** освобождает связанные данные и любой монопольный доступ, который мог быть связан с данными через этот конкретный объект. Позже можно вызвать метод [Open](../../../ado/reference/ado-api/open-method-ado-recordset.md) , чтобы повторно открыть объект с теми же или измененными атрибутами.  
  
 При закрытии объекта **набора записей** вызов всех методов, требующих активного курсора, приводит к ошибке.  
  
 Если изменение выполняется в режиме немедленного обновления, вызов метода **Close** приведет к ошибке; Вместо этого сначала вызовите метод [Update](../../../ado/reference/ado-api/update-method.md) или [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md) . Если объект **Recordset** закрывается в режиме пакетного обновления, все изменения, произошедшие с момента последнего вызова [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) , теряются.  
  
 При использовании метода [clone](../../../ado/reference/ado-api/clone-method-ado.md) для создания копий объекта открытого **набора записей** закрытие исходного или клона не влияет на другие копии.  
  
## <a name="applies-to"></a>Применение  

:::row:::
    :::column:::
        [Объект Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
        [Объект Record (ADO)](../../../ado/reference/ado-api/record-object-ado.md)  
    :::column-end:::
    :::column:::
        [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
        [Объект Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>См. также:  
 [Примеры методов Open и Close (Visual Basic)](../../../ado/reference/ado-api/open-and-close-methods-example-vb.md)   
 [Пример методов Open и Close (VBScript)](../../../ado/reference/ado-api/open-and-close-methods-example-vbscript.md)   
 [Пример методов Open и Close (Visual c++)](../../../ado/reference/ado-api/open-and-close-methods-example-vc.md)   
 [Метод Open (подключение ADO)](../../../ado/reference/ado-api/open-method-ado-connection.md)   
 [Метод Open (набор записей ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md)   
 [Метод Save](../../../ado/reference/ado-api/save-method.md)
