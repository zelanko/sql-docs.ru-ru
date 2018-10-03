---
title: Доступ к строкам в иерархических наборах записей | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- hierarchical Recordsets [ADO]
- data shaping [ADO], hierarchical Recordsets
ms.assetid: 25f1d2a1-6d5e-4457-aa07-5db5c75dee18
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 83b8334b4891d0b12cac59030ebf7fced871c5dd
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47773382"
---
# <a name="accessing-rows-in-a-hierarchical-recordset-example"></a>Доступ к строкам в иерархических наборах записей (например)
В следующем примере показано шаги, необходимые для получают доступ к строкам в иерархической [записей](../../../ado/reference/ado-api/recordset-object-ado.md):

1.  **Набор записей** объектов из **авторов** и **titleauthor** таблицы связаны по идентификатору автора.

2.  Внешний цикл отображает имя и фамилия каждого автора, состояние и идентификатор.

3.  Добавленная коллекция **записей** для каждой строки извлекается из [поля](../../../ado/reference/ado-api/fields-collection-ado.md) коллекции и назначены *rstTitleAuthor*.

4.  Внутренний цикл отображаются четыре поля из каждой строки в присоединенных **записей**.

 [StayInSync](../../../ado/reference/ado-api/stayinsync-property.md) свойству **false** для иллюстративных целей, чтобы вы могли видеть главу изменяет явно в каждой итерации внешнего цикла. Для повышения эффективности в примере кода, можно переместить назначения на шаге 3 перед первой строкой в шаге 2, таким образом, назначение выполняется только один раз. Затем установите [StayInSync](../../../ado/reference/ado-api/stayinsync-property.md) свойства **true**, так что *rstTitleAuthor* неявно и автоматически изменится на соответствующие главы всякий раз, когда *rst* перемещается на новую строку.

## <a name="example"></a>Пример

```
Sub datashape()
   Dim cnn As New ADODB.Connection
   Dim rst As New ADODB.Recordset
   Dim rstTitleAuthor As New ADODB.Recordset

   cnn.Provider = "MSDataShape"
   cnn.Open    "Data Provider=MSDASQL;" & _
               "Data Source=SRV;Integrated Security=SSPI;Database=Pubs"
' STEP 1
   rst.StayInSync = FALSE
   rst.Open    "SHAPE  {select * from authors} "  & _
               "APPEND ({select * from titleauthor} " & _
               "RELATE au_id TO au_id) AS chapTitleAuthor", _
               cnn
' STEP 2
   While Not rst.EOF
      Debug.Print    rst("au_fname"), rst("au_lname"), _
                     rst("state"), rst("au_id")
' STEP 3
      Set rstTitleAuthor = rst("chapTitleAuthor").Value
' STEP 4
      While Not rstTitleAuthor.EOF
         Debug.Print rstTitleAuthor(0), rstTitleAuthor(1), _
                     rstTitleAuthor(2), rstTitleAuthor(3)
         rstTitleAuthor.MoveNext
      Wend
      rst.MoveNext
   Wend
End Sub
```

## <a name="see-also"></a>См. также
 [Общие сведения о формировании данных](../../../ado/guide/data/data-shaping-overview.md) [поле объекта](../../../ado/reference/ado-api/field-object.md) [коллекция (ADO) поля](../../../ado/reference/ado-api/fields-collection-ado.md) [Грамматика формального формирования](../../../ado/guide/data/formal-shape-grammar.md) [Майкрософт служба формирования данных для OLE DB (Поставщик услуг ADO) ](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md) [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md) [необходимые поставщики для формирования данных](../../../ado/guide/data/required-providers-for-data-shaping.md) [фигуры предложении APPEND](../../../ado/guide/data/shape-append-clause.md) [фигуры команд в Общие](../../../ado/guide/data/shape-commands-in-general.md) [предложение COMPUTE для формирования](../../../ado/guide/data/shape-compute-clause.md) [Visual Basic для приложений-функций](../../../ado/guide/data/visual-basic-for-applications-functions.md)
