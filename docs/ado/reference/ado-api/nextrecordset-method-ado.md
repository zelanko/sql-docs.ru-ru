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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67932037"
---
# <a name="nextrecordset-method-ado"></a>Метод NextRecordset (ADO)
Очищает текущий [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекта и возвращает следующий **записей** путем выполнения инструкций до ряд команд.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Set recordset2 = recordset1.NextRecordset(RecordsAffected )  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает **записей** объекта. В модели синтаксис *recordset1* и *recordset2* могут совпадать **записей** объекта, или же можно использовать отдельные объекты. При использовании отдельных **записей** объектов, сброс **ActiveConnection** свойство на исходном **записей** (*recordset1*) После **NextRecordset** вызова будет формировать ошибку.  
  
#### <a name="parameters"></a>Параметры  
 *RecordsAffected*  
 Необязательный параметр. Объект **Long** переменной, в которой поставщик возвращает число записей, которые затронуты текущей операции.  
  
> [!NOTE]
>  Этот параметр только возвращает число записей, затронутых операцией; он не возвращает число записей в инструкции select, используемый для создания **записей**.  
  
## <a name="remarks"></a>Примечания  
 Используйте **NextRecordset** метод для возврата результатов следующей команды в операторе комплексной команду или хранимую процедуру, которая возвращает несколько результатов. При открытии **записей** объекта на основе составных команда инструкции (например, «ВЫБЕРИТЕ \* из table1; ВЫБЕРИТЕ \* из table2») с помощью [Execute](../../../ado/reference/ado-api/execute-method-ado-command.md) метод [команда](../../../ado/reference/ado-api/command-object-ado.md) или [откройте](../../../ado/reference/ado-api/open-method-ado-recordset.md) метод **записей**, ADO выполняет только первая команда и возвращает результаты, чтобы *записей*. Чтобы получить доступ к результаты последующих команд в инструкции, вызовите **NextRecordset** метод.  
  
 До тех пор, пока имеются дополнительные результаты и **записей** содержит составные операторы не отключается или переданы через границы процессов **NextRecordset** метод будет продолжать вернуть **записей** объектов. Если команды, возвращающей строки выполняется успешно, но не возвращает записи, возвращенный **записей** объект будет открытым, но пуст. Тест для этого случая путем проверки, что [BOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) и [EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) оба являются свойства **True**. Если команда не возвращает строк выполняется успешно, возвращенный **записей** объект будет закрыт, это можно проверить путем проверки [состояние](../../../ado/reference/ado-api/state-property-ado.md) свойство **записей**. Если нет дополнительных результатов, *записей* будет присвоено *ничего не*.  
  
 **NextRecordset** метод недоступен на отключенном **записей** объекта, где [ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md) было присвоено **Nothing**(в Microsoft Visual Basic) или значение NULL (в других языках).  
  
 Если выполняется в режиме немедленного обновления изменения, вызвав **NextRecordset** метод создает ошибку, вызовите [обновление](../../../ado/reference/ado-api/update-method.md) или [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md) метод первой.  
  
 Для передачи параметров для нескольких команд в составной оператор, заполнив [параметры](../../../ado/reference/ado-api/parameters-collection-ado.md) коллекции, или при передаче массива с исходным **откройте** или **Execute** вызов, параметры должны быть в том же порядке, в коллекции или массиве и как их соответствующих команд в серии команды. Необходимо завершить, считывая все результаты до считывания значения выходных параметров.  
  
 Поставщик OLE DB определяет, при выполнении каждой команды в составном операторе. [Поставщик Microsoft OLE DB для SQL Server](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md), например, выполняет все команды в одном пакете при получении составной оператор. Полученный в результате **наборы записей** просто возвращаются при вызове **NextRecordset**.  
  
 Тем не менее другие поставщики могут выполнить команду далее в инструкции, только в том случае, после вызова NextRecordset. Для этих поставщиков, если вы явно закрыть **записей** объекта перед пошагового выполнения инструкцию вся команда ADO никогда не выполняет остальные команды.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Пример метода NextRecordset (Visual Basic)](../../../ado/reference/ado-api/nextrecordset-method-example-vb.md)   
 [Пример метода NextRecordset (Visual C++)](../../../ado/reference/ado-api/nextrecordset-method-example-vc.md)   
