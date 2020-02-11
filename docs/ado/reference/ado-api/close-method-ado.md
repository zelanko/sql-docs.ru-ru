---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8a1d153d1433a377bb488366111b75a986365132
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67919934"
---
# <a name="close-method-ado"></a>Метод Close (ADO)
Закрывает открытый объект и все зависимые объекты.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object.Close  
```  
  
## <a name="remarks"></a>Remarks  
 Используйте метод **Close** , чтобы закрыть [соединение](../../../ado/reference/ado-api/connection-object-ado.md), [запись](../../../ado/reference/ado-api/record-object-ado.md), [набор записей](../../../ado/reference/ado-api/recordset-object-ado.md)или объект [потока](../../../ado/reference/ado-api/stream-object-ado.md) , чтобы освободить все связанные системные ресурсы. Закрытие объекта не приводит к его удалению из памяти; можно изменить параметры свойств и открыть его позже. Чтобы полностью исключить объект из памяти, закройте объект и задайте для переменной объекта значение *Nothing* (в Visual Basic).  
  
## <a name="connection"></a>Подключение  
 Использование метода **Close** для закрытия объекта **соединения** также закрывает все активные объекты **набора записей** , связанные с соединением. Объект [команды](../../../ado/reference/ado-api/command-object-ado.md) , связанный с закрываемым объектом **соединения** , будет сохранен, но больше не будет связан с объектом **соединения** . то есть свойство [ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md) будет иметь значение **Nothing**. Кроме того, коллекция [Parameters](../../../ado/reference/ado-api/parameters-collection-ado.md) объекта **команды** будет очищать все параметры, определяемые поставщиком.  
  
 Позже можно вызвать метод [Open](../../../ado/reference/ado-api/open-method-ado-connection.md) для повторного установления соединения с тем же или другим источником данных. Пока объект **соединения** закрыт, вызов всех методов, требующих открытого соединения с источником данных, приведет к ошибке.  
  
 Закрытие объекта **соединения** при наличии открытых объектов **Recordset** в соединении откатывает все ожидающие изменения во всех объектах **набора записей** . Явное закрытие объекта **соединения** (вызов метода **Close** ) во время выполнения транзакции приводит к ошибке. Если объект **соединения** выходит за пределы области действия во время выполнения транзакции, ADO автоматически выполняет откат транзакции.  
  
## <a name="recordset-record-stream"></a>Набор записей, запись, поток  
 Использование метода **Close** для закрытия объекта **Recordset**, **записи**или **потока** освобождает связанные данные и любой монопольный доступ, который мог быть связан с данными через этот конкретный объект. Позже можно вызвать метод [Open](../../../ado/reference/ado-api/open-method-ado-recordset.md) , чтобы повторно открыть объект с теми же или измененными атрибутами.  
  
 При закрытии объекта **набора записей** вызов всех методов, требующих активного курсора, приводит к ошибке.  
  
 Если изменение выполняется в режиме немедленного обновления, вызов метода **Close** приведет к ошибке; Вместо этого сначала вызовите метод [Update](../../../ado/reference/ado-api/update-method.md) или [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md) . Если объект **Recordset** закрывается в режиме пакетного обновления, все изменения, произошедшие с момента последнего вызова [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) , теряются.  
  
 При использовании метода [clone](../../../ado/reference/ado-api/clone-method-ado.md) для создания копий объекта открытого **набора записей** закрытие исходного или клона не влияет на другие копии.  
  
## <a name="applies-to"></a>Применяется к  
  
|||  
|-|-|  
|[Объект Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)|[Объект Record (ADO)](../../../ado/reference/ado-api/record-object-ado.md)|  
|[Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|[Объект Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)|  
  
## <a name="see-also"></a>См. также:  
 [Примеры методов Open и Close (Visual Basic)](../../../ado/reference/ado-api/open-and-close-methods-example-vb.md)   
 [Пример методов Open и Close (VBScript)](../../../ado/reference/ado-api/open-and-close-methods-example-vbscript.md)   
 [Пример методов Open и Close (Visual c++)](../../../ado/reference/ado-api/open-and-close-methods-example-vc.md)   
 [Метод Open (подключение ADO)](../../../ado/reference/ado-api/open-method-ado-connection.md)   
 [Метод Open (набор записей ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md)   
 [Метод Save](../../../ado/reference/ado-api/save-method.md)
