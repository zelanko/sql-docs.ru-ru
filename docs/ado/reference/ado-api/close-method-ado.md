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
ms.openlocfilehash: 5f2fe4aff39b29e937de88f3166698fb8f9ad730
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88776223"
---
# <a name="close-method-ado"></a>Метод Close (ADO)
Закрывает открытый объект и все зависимые объекты.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object.Close  
```  
  
## <a name="remarks"></a>Remarks  
 Используйте метод **Close** , чтобы закрыть [соединение](./connection-object-ado.md), [запись](./record-object-ado.md), [набор записей](./recordset-object-ado.md)или объект [потока](./stream-object-ado.md) , чтобы освободить все связанные системные ресурсы. Закрытие объекта не приводит к его удалению из памяти; можно изменить параметры свойств и открыть его позже. Чтобы полностью исключить объект из памяти, закройте объект и задайте для переменной объекта значение *Nothing* (в Visual Basic).  
  
## <a name="connection"></a>Подключение  
 Использование метода **Close** для закрытия объекта **соединения** также закрывает все активные объекты **набора записей** , связанные с соединением. Объект [команды](./command-object-ado.md) , связанный с закрываемым объектом **соединения** , будет сохранен, но больше не будет связан с объектом **соединения** . то есть свойство [ActiveConnection](./activeconnection-property-ado.md) будет иметь значение **Nothing**. Кроме того, коллекция [Parameters](./parameters-collection-ado.md) объекта **команды** будет очищать все параметры, определяемые поставщиком.  
  
 Позже можно вызвать метод [Open](./open-method-ado-connection.md) для повторного установления соединения с тем же или другим источником данных. Пока объект **соединения** закрыт, вызов всех методов, требующих открытого соединения с источником данных, приведет к ошибке.  
  
 Закрытие объекта **соединения** при наличии открытых объектов **Recordset** в соединении откатывает все ожидающие изменения во всех объектах **набора записей** . Явное закрытие объекта **соединения** (вызов метода **Close** ) во время выполнения транзакции приводит к ошибке. Если объект **соединения** выходит за пределы области действия во время выполнения транзакции, ADO автоматически выполняет откат транзакции.  
  
## <a name="recordset-record-stream"></a>Набор записей, запись, поток  
 Использование метода **Close** для закрытия объекта **Recordset**, **записи**или **потока** освобождает связанные данные и любой монопольный доступ, который мог быть связан с данными через этот конкретный объект. Позже можно вызвать метод [Open](./open-method-ado-recordset.md) , чтобы повторно открыть объект с теми же или измененными атрибутами.  
  
 При закрытии объекта **набора записей** вызов всех методов, требующих активного курсора, приводит к ошибке.  
  
 Если изменение выполняется в режиме немедленного обновления, вызов метода **Close** приведет к ошибке; Вместо этого сначала вызовите метод [Update](./update-method.md) или [CancelUpdate](./cancelupdate-method-ado.md) . Если объект **Recordset** закрывается в режиме пакетного обновления, все изменения, произошедшие с момента последнего вызова [UpdateBatch](./updatebatch-method.md) , теряются.  
  
 При использовании метода [clone](./clone-method-ado.md) для создания копий объекта открытого **набора записей** закрытие исходного или клона не влияет на другие копии.  
  
## <a name="applies-to"></a>Применение  

:::row:::
    :::column:::
        [Объект Connection (ADO)](./connection-object-ado.md)  
        [Объект Record (ADO)](./record-object-ado.md)  
    :::column-end:::
    :::column:::
        [Объект Recordset (ADO)](./recordset-object-ado.md)  
        [Объект Stream (ADO)](./stream-object-ado.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>См. также  
 [Примеры методов Open и Close (Visual Basic)](./open-and-close-methods-example-vb.md)   
 [Пример методов Open и Close (VBScript)](./open-and-close-methods-example-vbscript.md)   
 [Пример методов Open и Close (Visual c++)](./open-and-close-methods-example-vc.md)   
 [Метод Open (подключение ADO)](./open-method-ado-connection.md)   
 [Метод Open (набор записей ADO)](./open-method-ado-recordset.md)   
 [Метод Save](./save-method.md)