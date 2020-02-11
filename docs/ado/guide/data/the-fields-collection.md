---
title: Коллекция Fields | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Field object [ADO], fields collection
- Fields collection [ADO]
ms.assetid: 574cf36e-e5f5-403b-983c-749ef93c108f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 197a57b8a9b9ea2927a057733992a02c731a335a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67923936"
---
# <a name="the-fields-collection"></a>Коллекция Fields
Коллекция **Fields** является одной из встроенных коллекций ADO. Коллекция — это упорядоченный набор элементов, которые можно называть единицей. Дополнительные сведения о коллекциях ADO см. [в разделе Объектная модель ADO](../../../ado/guide/data/ado-objects-and-collections.md).  
  
 Коллекция **Fields** содержит объект **field** для каждого поля (столбца) в **наборе записей**. Как и все коллекции ADO, у него есть свойства **Count** и **Item** , а также методы **добавления** и **обновления** . У него также есть методы **CancelUpdate**, **Delete**, **Resync**и **Update** , которые недоступны для других коллекций ADO.  
  
## <a name="examining-the-fields-collection"></a>Проверка коллекции Fields  
 Рассмотрим коллекцию **Fields** образца **набора записей** , представленного в этом разделе. Образец **набора записей** был получен из инструкции SQL  
  
```  
SELECT ProductID, ProductName, UnitPrice FROM Products WHERE CategoryID = 7  
```  
  
 Поэтому следует убедиться, что коллекция **полей набора записей** содержит три поля.  
  
```  
'BeginWalkFields  
    Dim objFields As ADODB.Fields  
    Dim intLoop As Integer  
  
    objRs.Open strSQL, strConnStr, adOpenForwardOnly, adLockReadOnly, adCmdText  
  
    Set objFields = objRs.Fields  
  
    For intLoop = 0 To (objFields.Count - 1)  
        Debug.Print objFields.Item(intLoop).Name  
    Next  
'EndWalkFields  
```  
  
 Этот код просто определяет количество объектов **field** в коллекции **Fields** с помощью свойства **Count** и выполняет цикл по коллекции, возвращая значение свойства **Name** для каждого объекта **field** . Для получения сведений о поле можно использовать много дополнительных свойств **поля** . Дополнительные сведения о запросах к **полю**см. [в разделе объект Field](../../../ado/guide/data/the-field-object.md).  
  
## <a name="counting-columns"></a>Подсчет столбцов  
 Как и следовало ожидать, свойство **Count** возвращает фактическое число объектов **field** в коллекции **Fields** . Поскольку нумерация элементов коллекции начинается с нуля, всегда следует создавать циклы кода, начиная с нуля и заканчивая значением свойства **Count** минус 1. Если вы используете Microsoft Visual Basic и хотите перебрать элементы коллекции, не проверяя свойство **Count** , используйте оператор **For Each... Следующая** команда.  
  
 Если свойство **Count** равно нулю, в коллекции отсутствуют объекты.  
  
## <a name="getting-to-the-field"></a>Приступая к работе с полем  
 Как и в случае с любой коллекцией ADO, свойство **Item** является свойством коллекции по умолчанию. Он возвращает отдельный объект **поля** , заданный по имени или индексу, переданному в него. Поэтому следующие инструкции эквивалентны образцу **набора записей**.  
  
```  
objField = objRecordset.Fields.Item("ProductID")  
objField = objRecordset.Fields("ProductID")  
objField = objRecordset.Fields.Item(0)  
objField = objRecordset.Fields(0)  
```  
  
 Если эти методы эквивалентны, что лучше? Здесь возможны варианты в зависимости от обстоятельств. Использование индекса для получения **поля** из коллекции выполняется быстрее, так как оно обращается к **полю** напрямую без необходимости выполнять поиск строки. С другой стороны, порядок **полей** в коллекции должен быть известен, и если порядок меняется, ссылка на индекс **поля** будет изменяться везде, где оно происходит. Хотя несколько медленнее, использование имени **поля** является более гибким, поскольку оно не зависит от порядка **полей** в коллекции.  
  
## <a name="using-the-refresh-method"></a>Использование метода Refresh  
 В отличие от других коллекций ADO, использование метода **Refresh** в коллекции **Fields** не имеет видимого результата. Чтобы получить изменения из базовой структуры базы данных, необходимо использовать метод **Requery** или, если объект **набора записей** не поддерживает закладки, метод **MoveFirst** , который приведет к повторному выполнению команды для поставщика.  
  
## <a name="adding-fields-to-a-recordset"></a>Добавление полей в набор записей  
 Метод **append** используется для добавления полей в **набор записей**.  
  
 Можно использовать метод **append** для формирования **набора записей** программным способом без открытия соединения с источником данных. Ошибка времени выполнения возникает, если метод **append** вызывается для коллекции **полей** открытого **набора записей** или для **набора записей** , в котором было задано свойство **ActiveConnection** . Поля можно добавлять только к **набору записей** , который не открыт и еще не подключен к источнику данных. Однако, чтобы указать значения для вновь добавляемых **полей**, сначала необходимо открыть **набор записей** .  
  
 Разработчикам часто требуется место для временного хранения некоторых данных или требуется, чтобы некоторые данные действовали так, как если бы они поступали с сервера, чтобы они могли участвовать в привязке данных в пользовательском интерфейсе. ADO (в сочетании со [службой курсора Майкрософт для OLE DB](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md)) позволяет разработчику создавать пустой объект **Recordset** , указывая сведения о столбцах и вызывая **Open**. В следующем примере к новому объекту **набора записей** добавляются три новых поля. Затем открывается **набор записей** , добавляются две новые записи, а **набор записей** сохраняется в файле. (Дополнительные сведения о сохранении **набора записей** см. в разделе [обновление и сохранение данных](../../../ado/guide/data/updating-and-persisting-data.md).)  
  
```  
'BeginFabricate  
    Dim objRs As ADODB.Recordset  
    Set objRs = New ADODB.Recordset  
  
    With objRs.Fields  
        .Append "StudentID", adChar, 11, adFldUpdatable  
        .Append "FullName", adVarChar, 50, adFldUpdatable  
        .Append "PhoneNmbr", adVarChar, 20, adFldUpdatable  
    End With  
  
    With objRs  
        .Open  
  
        .AddNew  
        .Fields(0) = "123-45-6789"  
        .Fields(1) = "John Doe"  
        .Fields(2) = "(425) 555-5555"  
        .Update  
  
        .AddNew  
        .Fields(0) = "123-45-6780"  
        .Fields(1) = "Jane Doe"  
        .Fields(2) = "(615) 555-1212"  
        .Update  
    End With  
  
    objRs.Save App.Path & "FabriTest.adtg", adPersistADTG  
  
    objRs.Close  
'EndFabricate  
```  
  
 Использование метода **append полей** отличается между объектом **Recordset** и объектом **Record** . Дополнительные сведения об объекте **Record** см. в разделе [записи и потоки](../../../ado/guide/data/records-and-streams.md).  
  
## <a name="see-also"></a>См. также:  
 [Составление иерархических наборов записей](../../../ado/guide/data/fabricating-hierarchical-recordsets.md)
