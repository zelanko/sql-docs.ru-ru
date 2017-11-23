---
title: "Метод NextRecordset (ADO) | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- NextRecordset
- Recordset15::NextRecordset
- Recordset15::raw_NextRecordset
helpviewer_keywords: NextRecordset method [ADO]
ms.assetid: ab1fa449-a695-4987-b1ee-bc68f89418dd
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 524957fe66debad97fc9c1512cc9e3c70153d216
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="nextrecordset-method-ado"></a>Метод NextRecordset (ADO)
Очищает текущий [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекта и возвращает следующий **записей** с помощью перемещения через ряд команд.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Set recordset2 = recordset1.NextRecordset(RecordsAffected )  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает **записей** объекта. В модели синтаксис *recordset1* и *recordset2* могут быть одинаковыми **записей** объекта, или можно использовать отдельные объекты. При использовании отдельных **записей** объектов, сброс **ActiveConnection** свойство на исходном **записей** (*recordset1*) После **NextRecordset** вызова будет формировать ошибку.  
  
#### <a name="parameters"></a>Параметры  
 *RecordsAffected*  
 Необязательно. Объект **длинные** переменной, в которой поставщик возвращает количество записей, затронутых текущей операции.  
  
> [!NOTE]
>  Этот параметр только возвращает число записей, затронутых операцией; Возвращает количество записей в инструкции select, используемый для создания **записей**.  
  
## <a name="remarks"></a>Замечания  
 Используйте **NextRecordset** метод для возврата результатов инструкция комплексной команды в следующую команду или хранимую процедуру, которая возвращает несколько результатов. При открытии **записей** объекта, основанного на инструкция комплексной команды (например, «ВЫБЕРИТЕ \* из таблицы table1; ВЫБЕРИТЕ \* из table2») с помощью [Execute](../../../ado/reference/ado-api/execute-method-ado-command.md) метод [команда](../../../ado/reference/ado-api/command-object-ado.md) или [откройте](../../../ado/reference/ado-api/open-method-ado-recordset.md) метод **набора записей**, ADO выполняет только первая команда и возвращает результаты в *записей*. Чтобы открыть результаты последующих команд в инструкции, вызовите **NextRecordset** метод.  
  
 При условии, что имеются дополнительные результаты и **записей** содержит составные операторы не отключается или переданы через границы процессов **NextRecordset** метод будет продолжать вернуть **записей** объектов. Если команды, возвращающей строки выполняется успешно, но данные не возвращаются, возвращенный **записей** объекта будут открыты, но не пустой. Тест для этого случая путем проверки, что [BOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) и [EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) свойства являются оба **True**. Если не тип команда выполняется успешно, возвращенный возвращающие строки **записей** объект будет закрыт, это можно проверить путем проверки [состояние](../../../ado/reference/ado-api/state-property-ado.md) свойство **записей**. Если нет дополнительных результатов *записей* будет присвоено *ничего не*.  
  
 **NextRecordset** метод не доступен на несвязанный **записей** объекта, где [ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md) ему было присвоено **ничего**(в Microsoft Visual Basic) или значение NULL (на других языках).  
  
 Если выполняется в режиме немедленного обновления изменения, вызвав **NextRecordset** метод создает ошибку, вызовите [обновление](../../../ado/reference/ado-api/update-method.md) или [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md) метод первой.  
  
 Для передачи параметров для нескольких команд в составном операторе путем заполнения [параметры](../../../ado/reference/ado-api/parameters-collection-ado.md) коллекции, или при передаче массива с первоначальным **откройте** или **Execute** вызов, параметры должны быть в том же порядке, в коллекции или массиве и как их соответствующих команд в серии команд. Необходимо завершить, считывая все результаты до считывания значения выходных параметров.  
  
 Поставщик OLE DB определяет, когда выполняется каждая команда команда в составной оператор. [Поставщик Microsoft OLE DB для SQL Server](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md), например, выполняет все команды в пакете при получении составной оператор. Итоговый **наборы записей** возвращаются при вызове **NextRecordset**.  
  
 Тем не менее других поставщиков может выполните следующую команду в инструкции только после вызова NextRecordset. Для этих поставщиков, если явно закрыть **записей** объекта перед проходить через инструкцию всей команды ADO никогда не выполняет остальные команды.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также:  
 [Пример метода NextRecordset (Visual Basic)](../../../ado/reference/ado-api/nextrecordset-method-example-vb.md)   
 [Пример метода NextRecordset (Visual C++)](../../../ado/reference/ado-api/nextrecordset-method-example-vc.md)   
