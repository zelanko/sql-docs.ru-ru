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
manager: craigg
ms.openlocfilehash: f43e59ed38dfde8091cb851f75a133c60874a6af
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63302498"
---
# <a name="close-method-ado"></a>Метод Close (ADO)
Закрывает открытый объект и все зависимые объекты.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object.Close  
```  
  
## <a name="remarks"></a>Примечания  
 Используйте **закрыть** метод для закрытия [подключения](../../../ado/reference/ado-api/connection-object-ado.md), [записи](../../../ado/reference/ado-api/record-object-ado.md), [записей](../../../ado/reference/ado-api/recordset-object-ado.md), или [Stream](../../../ado/reference/ado-api/stream-object-ado.md) объекта для освобождения любых ресурсов операционной системы. Закрыть объект не удаляется из памяти; можно изменить его параметры свойств и открыть его позже. Для полного устранения объект из памяти, закройте объект и затем присвойте переменной объекта *Nothing* (в Visual Basic).  
  
## <a name="connection"></a>Соединение  
 С помощью **закрыть** метод для закрытия **подключения** объекта также закрывает все активные **записей** объекты, связанные с подключением. Объект [команда](../../../ado/reference/ado-api/command-object-ado.md) объект, связанный с **подключения** закрытие объекта сохраняются, но больше не будут связаны с **подключения** объекта, то есть его [ ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md) свойству будет присвоено **ничего не**. Кроме того **команда** объекта [параметры](../../../ado/reference/ado-api/parameters-collection-ado.md) коллекции будет очищен всех параметров, определяемых поставщиком.  
  
 Позже можно вызвать [откройте](../../../ado/reference/ado-api/open-method-ado-connection.md) метод, чтобы повторно установить подключение к тому же или другой источник данных. Хотя **подключения** объект закрыт, вызова методов, которые требуется открытое соединение с источником данных приводит к ошибке.  
  
 Закрытие **подключения** пока открыты объект **записей** объекты для соединения откат всех изменений, ожидающих во всех **записей** объектов. Явное закрытие **подключения** объекта (вызов **закрыть** метод) во время транзакции ход выполнения приводит к ошибке. Если **подключения** объект выходит за пределы области действия транзакции во время выполнения, ADO автоматически выполняет откат транзакции.  
  
## <a name="recordset-record-stream"></a>Набор записей, записи Stream  
 С помощью **закрыть** метод для закрытия **записей**, **записи**, или **Stream** объект освобождает связанные данные и любые монопольный доступ Вы могли к данным с помощью этого конкретного объекта. Позже можно вызвать [откройте](../../../ado/reference/ado-api/open-method-ado-recordset.md) метод, чтобы снова открыть объект с тем же, то есть измененные, атрибуты.  
  
 Хотя **записей** объект закрыт, вызова методов, которые требуют динамический курсор формирует ошибку.  
  
 Если выполняется в режиме немедленного обновления изменения, вызвав **закрыть** метод создает ошибку, вместо этого необходимо вызвать [обновление](../../../ado/reference/ado-api/update-method.md) или [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md) метод первой. Если вы закроете **записей** объекта в пакетный режим обновления, все изменения с момента последнего [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) вызова будут потеряны.  
  
 При использовании [клона](../../../ado/reference/ado-api/clone-method-ado.md) метод для создания копий открытого **записей** объекта, закрытие исходные или клон не влияет на любой из этих копий.  
  
## <a name="applies-to"></a>Объект применения  
  
|||  
|-|-|  
|[Объект Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)|[Объект Record (ADO)](../../../ado/reference/ado-api/record-object-ado.md)|  
|[Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|[Объект Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)|  
  
## <a name="see-also"></a>См. также  
 [Примеры методов Open и Close (Visual Basic)](../../../ado/reference/ado-api/open-and-close-methods-example-vb.md)   
 [Примеры методов Open и Close (VBScript)](../../../ado/reference/ado-api/open-and-close-methods-example-vbscript.md)   
 [Примеры методов Open и Close (Visual C++)](../../../ado/reference/ado-api/open-and-close-methods-example-vc.md)   
 [Метод Open (объект Connection ADO)](../../../ado/reference/ado-api/open-method-ado-connection.md)   
 [Метод Open (объект Recordset ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md)   
 [Метод Save](../../../ado/reference/ado-api/save-method.md)
