---
title: Close-метод (ADO) | Документы Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::Close
- _Stream::Close
- _Record::Close
helpviewer_keywords:
- Close method [ADO]
ms.assetid: 3cdf27d1-a180-4cff-8e42-95dec5fb1b55
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a88b6eefe8e251d97bbc77fbcdd3a7b2dc911983
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="close-method-ado"></a>Close-метод (ADO)
Закрывает открытый объект и все зависимые объекты.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object.Close  
```  
  
## <a name="remarks"></a>Замечания  
 Используйте **закрыть** метод закрытия [подключения](../../../ado/reference/ado-api/connection-object-ado.md), [записи](../../../ado/reference/ado-api/record-object-ado.md), [записей](../../../ado/reference/ado-api/recordset-object-ado.md), или [поток](../../../ado/reference/ado-api/stream-object-ado.md) объекта Чтобы освободить все связанные системные ресурсы. Закрывает объект не удаляется из памяти; можно изменить настройки его свойств и открыть его позже. Для полного устранения объекта из памяти, закройте объект и затем присвойте переменной объекта *ничего* (в Visual Basic).  
  
## <a name="connection"></a>Соединение  
 С помощью **закрыть** метод закрытия **подключения** объекта также закрывает все активные **записей** объектов, связанных с подключением. Объект [команда](../../../ado/reference/ado-api/command-object-ado.md) объекта, связанного с **подключения** закрытие объекта сохранятся, но больше не будут связаны с **подключения** объекта, то есть его [ ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md) свойству будет присвоено **ничего не**. Кроме того **команда** объекта [параметры](../../../ado/reference/ado-api/parameters-collection-ado.md) коллекции будет удалено из параметров, определенных поставщиком.  
  
 Позже можно вызвать [откройте](../../../ado/reference/ado-api/open-method-ado-connection.md) метод, чтобы повторно установить подключение к тому же или другой источник данных. Хотя **подключения** объект закрыт, вызов любых методов, которые требуется открытое соединение с источником данных приведет к ошибке.  
  
 Закрытие **подключения** объекта, пока имеются открытые **записей** объекты для соединения выполняет откат всех изменений, ожидающих во всех **записей** объектов. Явное закрытие **подключения** объекта (вызов **закрыть** метод) во время транзакции выполняется приводит к ошибке. Если **подключения** объект выходит за пределы области во время транзакции, ADO автоматически выполняет откат транзакции.  
  
## <a name="recordset-record-stream"></a>Набор записей, запишите, потоковую передачу  
 С помощью **закрыть** метод закрытия **набора записей**, **запись**, или **поток** объект освобождает связанные данные и любые монопольного доступа Вы могли к данным с помощью этого конкретного объекта. Позже можно вызвать [откройте](../../../ado/reference/ado-api/open-method-ado-recordset.md) метод, чтобы снова открыть объект с таким, или изменения, атрибуты.  
  
 Хотя **записей** объект закрыт, вызов любых методов, в которых требуется динамическая курсора приводит к ошибке.  
  
 Если выполняется в режиме немедленного обновления изменения, вызвав **закрыть** метод создает ошибку, вместо этого необходимо вызвать [обновление](../../../ado/reference/ado-api/update-method.md) или [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md) метод первой. Если вы закроете **набора записей** объекта в пакетный режим обновления, все изменения с момента последнего [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) вызова будут потеряны.  
  
 При использовании [клон](../../../ado/reference/ado-api/clone-method-ado.md) метод для создания копий открытого **записей** объекта, закрытие исходные или клон не влияет на все остальные копии.  
  
## <a name="applies-to"></a>Объект применения  
  
|||  
|-|-|  
|[Объект Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)|[Объект Record (ADO)](../../../ado/reference/ado-api/record-object-ado.md)|  
|[Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|[Объект Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)|  
  
## <a name="see-also"></a>См. также  
 [Открытие и закрытие примере методы (Visual Basic)](../../../ado/reference/ado-api/open-and-close-methods-example-vb.md)   
 [Пример методов открытия и закрытия (VBScript)](../../../ado/reference/ado-api/open-and-close-methods-example-vbscript.md)   
 [Пример методов открытия и закрытия (VC ++)](../../../ado/reference/ado-api/open-and-close-methods-example-vc.md)   
 [Метод Open (соединение ADO)](../../../ado/reference/ado-api/open-method-ado-connection.md)   
 [Метод Open (набора записей ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md)   
 [Метод Save](../../../ado/reference/ado-api/save-method.md)
