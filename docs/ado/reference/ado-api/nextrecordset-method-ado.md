---
description: Метод NextRecordset (ADO)
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 018de245b6d809b094a88d3a1f455bce0166a466
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88774053"
---
# <a name="nextrecordset-method-ado"></a>Метод NextRecordset (ADO)
Очищает текущий объект [набора записей](./recordset-object-ado.md) и возвращает следующий **набор записей** путем перемещения по ряду команд.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Set recordset2 = recordset1.NextRecordset(RecordsAffected )  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает объект **Recordset** . В модели синтаксиса *recordset1* и *recordset2* могут быть одним и тем же объектом **Recordset** или можно использовать отдельные объекты. При использовании отдельных объектов **Recordset** сброс свойства **ActiveConnection** в исходном **наборе записей** (*recordset1*) после вызова **NextRecordset** выдаст ошибку.  
  
#### <a name="parameters"></a>Параметры  
 *RecordsAffected*  
 Необязательный элемент. **Длинная** переменная, к которой поставщик возвращает количество записей, затронутых текущей операцией.  
  
> [!NOTE]
>  Этот параметр возвращает только число записей, затронутых операцией. Он не возвращает число записей из инструкции SELECT, используемой для создания **набора записей**.  
  
## <a name="remarks"></a>Remarks  
 Используйте метод **NextRecordset** для возврата результатов следующей команды в составной инструкции Command или хранимой процедуры, возвращающей несколько результатов. При открытии объекта **набора записей** на основе составного оператора Command (например, SELECT \* from Table1; SELECT \* from Table2 ") с помощью метода [EXECUTE](./execute-method-ado-command.md) в [команде](./command-object-ado.md) или метода [Open](./open-method-ado-recordset.md) в **наборе записей**, ADO выполняет только первую команду и возвращает результаты в *набор записей*. Чтобы получить доступ к результатам последующих команд в инструкции, вызовите метод **NextRecordset** .  
  
 Пока имеются дополнительные результаты, а **набор записей** , содержащий составные инструкции, не отсоединен или не маршалируется через границы процесса, метод **NextRecordset** будет продолжать возвращать объекты **Recordset** . Если команда, возвращающая строку, выполняется успешно, но не возвращает никаких записей, возвращенный объект **набора записей** будет открыт, но пуст. Протестируйте этот случай, убедившись, что для свойств [BOF](./bof-eof-properties-ado.md) и [EOF](./bof-eof-properties-ado.md) задано **значение true**. Если команда, не возвращающая строки, выполняется успешно, возвращаемый объект **набора записей** будет закрыт, что можно проверить путем проверки свойства [State](./state-property-ado.md) в **наборе записей**. Если больше нет результатов, набору *записей* будет присвоено значение *Nothing*.  
  
 Метод **NextRecordset** недоступен на объекте неподключенного **набора записей** , где [ActiveConnection](./activeconnection-property-ado.md) имеет значение **Nothing** (в Microsoft Visual Basic) или null (в других языках).  
  
 Если изменение выполняется в режиме немедленного обновления, вызов метода **NextRecordset** приведет к ошибке; Сначала вызовите метод [Update](./update-method.md) или [CancelUpdate](./cancelupdate-method-ado.md) .  
  
 Чтобы передать параметры для нескольких команд в составной инструкции путем заполнения коллекции [Parameters](./parameters-collection-ado.md) или передачи массива с исходным вызовом **Open** или **EXECUTE** , параметры должны находиться в том же порядке в коллекции или массиве, что и соответствующие команды в ряде команд. Прежде чем считывать значения выходных параметров, необходимо завершить чтение всех результатов.  
  
 Поставщик OLE DB определяет, когда выполняется каждая команда в составном операторе. Например, [поставщик OLE DB Майкрософт для SQL Server](../../guide/appendixes/microsoft-ole-db-provider-for-sql-server.md)выполняет все команды в пакете после получения составного оператора. Итоговые **наборы записей** просто возвращаются при вызове **NextRecordset**.  
  
 Однако другие поставщики могут выполнить следующую команду в операторе только после вызова NextRecordset. Для этих поставщиков, если вы явно закрыли объект **Recordset** перед выполнением всех инструкций команды, ADO не выполняет оставшиеся команды.  
  
## <a name="applies-to"></a>Применение  
 [Объект Recordset (ADO)](./recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Пример метода NextRecordset (Visual Basic)](./nextrecordset-method-example-vb.md)   
 [Пример метода NextRecordset (Visual C++)](./nextrecordset-method-example-vc.md)