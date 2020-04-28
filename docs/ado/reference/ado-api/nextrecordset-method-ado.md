---
title: Метод NextRecordset (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 03/20/2018
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- NextRecordset
- Recordset15::NextRecordset
- Recordset15::raw_NextRecordset
helpviewer_keywords:
- NextRecordset method [ADO]
ms.assetid: ab1fa449-a695-4987-b1ee-bc68f89418dd
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 3c7af4f5d217670ab23e71a3c53ccd5cf7944b0c
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67932037"
---
# <a name="nextrecordset-method-ado"></a>Метод NextRecordset (ADO)
Очищает текущий объект [набора записей](../../../ado/reference/ado-api/recordset-object-ado.md) и возвращает следующий **набор записей** путем перемещения по ряду команд.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Set recordset2 = recordset1.NextRecordset(RecordsAffected )  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает объект **Recordset** . В модели синтаксиса *recordset1* и *recordset2* могут быть одним и тем же объектом **Recordset** или можно использовать отдельные объекты. При использовании отдельных объектов **Recordset** сброс свойства **ActiveConnection** в исходном **наборе записей** (*recordset1*) после вызова **NextRecordset** выдаст ошибку.  
  
#### <a name="parameters"></a>Параметры  
 *RecordsAffected*  
 Необязательный параметр. **Длинная** переменная, к которой поставщик возвращает количество записей, затронутых текущей операцией.  
  
> [!NOTE]
>  Этот параметр возвращает только число записей, затронутых операцией. Он не возвращает число записей из инструкции SELECT, используемой для создания **набора записей**.  
  
## <a name="remarks"></a>Remarks  
 Используйте метод **NextRecordset** для возврата результатов следующей команды в составной инструкции Command или хранимой процедуры, возвращающей несколько результатов. При открытии объекта **набора записей** на основе составного оператора Command (например, SELECT \* from Table1; SELECT \* from Table2 ") с помощью метода [EXECUTE](../../../ado/reference/ado-api/execute-method-ado-command.md) в [команде](../../../ado/reference/ado-api/command-object-ado.md) или метода [Open](../../../ado/reference/ado-api/open-method-ado-recordset.md) в **наборе записей**, ADO выполняет только первую команду и возвращает результаты в *набор записей*. Чтобы получить доступ к результатам последующих команд в инструкции, вызовите метод **NextRecordset** .  
  
 Пока имеются дополнительные результаты, а **набор записей** , содержащий составные инструкции, не отсоединен или не маршалируется через границы процесса, метод **NextRecordset** будет продолжать возвращать объекты **Recordset** . Если команда, возвращающая строку, выполняется успешно, но не возвращает никаких записей, возвращенный объект **набора записей** будет открыт, но пуст. Протестируйте этот случай, убедившись, что для свойств [BOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) и [EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) задано **значение true**. Если команда, не возвращающая строки, выполняется успешно, возвращаемый объект **набора записей** будет закрыт, что можно проверить путем проверки свойства [State](../../../ado/reference/ado-api/state-property-ado.md) в **наборе записей**. Если больше нет результатов, набору *записей* будет присвоено значение *Nothing*.  
  
 Метод **NextRecordset** недоступен на объекте неподключенного **набора записей** , где [ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md) имеет значение **Nothing** (в Microsoft Visual Basic) или null (в других языках).  
  
 Если изменение выполняется в режиме немедленного обновления, вызов метода **NextRecordset** приведет к ошибке; Сначала вызовите метод [Update](../../../ado/reference/ado-api/update-method.md) или [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md) .  
  
 Чтобы передать параметры для нескольких команд в составной инструкции путем заполнения коллекции [Parameters](../../../ado/reference/ado-api/parameters-collection-ado.md) или передачи массива с исходным вызовом **Open** или **EXECUTE** , параметры должны находиться в том же порядке в коллекции или массиве, что и соответствующие команды в ряде команд. Прежде чем считывать значения выходных параметров, необходимо завершить чтение всех результатов.  
  
 Поставщик OLE DB определяет, когда выполняется каждая команда в составном операторе. Например, [поставщик OLE DB Майкрософт для SQL Server](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md)выполняет все команды в пакете после получения составного оператора. Итоговые **наборы записей** просто возвращаются при вызове **NextRecordset**.  
  
 Однако другие поставщики могут выполнить следующую команду в операторе только после вызова NextRecordset. Для этих поставщиков, если вы явно закрыли объект **Recordset** перед выполнением всех инструкций команды, ADO не выполняет оставшиеся команды.  
  
## <a name="applies-to"></a>Применяется к  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также:  
 [Пример метода NextRecordset (Visual Basic)](../../../ado/reference/ado-api/nextrecordset-method-example-vb.md)   
 [Пример метода NextRecordset (Visual C++)](../../../ado/reference/ado-api/nextrecordset-method-example-vc.md)   
