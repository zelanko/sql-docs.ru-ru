---
title: "Доступ к строк в иерархических записей | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- hierarchical Recordsets [ADO]
- data shaping [ADO], hierarchical Recordsets
ms.assetid: 25f1d2a1-6d5e-4457-aa07-5db5c75dee18
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 351650e6445c0d8f85751349d243bc8870fd8c2f
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="accessing-rows-in-a-hierarchical-recordset-example"></a>Доступ к строк в иерархических записей (например)
В следующем примере показано шаги, необходимые для доступа к строкам в иерархической [записей](../../../ado/reference/ado-api/recordset-object-ado.md):

1.  **Набор записей** объектов из **авторов** и **titleauthor** таблицы связаны через идентификатор автора.

2.  Внешний цикл отображает имя и фамилия каждого автора, состояние и идентификатор.

3.  Добавленный **записей** для каждой строки, извлекается из [поля](../../../ado/reference/ado-api/fields-collection-ado.md) коллекции и назначены *rstTitleAuthor*.

4.  Внутренний цикл отображаются четыре поля из каждой строки в добавленных **записей**.

 [StayInSync](../../../ado/reference/ado-api/stayinsync-property.md) свойству **false** для наглядности, чтобы вы могли видеть главе изменяет явно в каждой итерации внешнего цикла. Для повышения эффективности в примере кода, можно переместить назначения на шаге 3 перед первой строкой в шаге 2, чтобы назначение выполняется только один раз. Установите [StayInSync](../../../ado/reference/ado-api/stayinsync-property.md) свойства **true**, после чего *rstTitleAuthor* неявно и автоматически изменится на соответствующий главе всякий раз, когда *rst* перемещается на новую строку.

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

## <a name="see-also"></a>См. также:
 [Обзор формирования данных](../../../ado/guide/data/data-shaping-overview.md) [поле объекта](../../../ado/reference/ado-api/field-object.md) [поля коллекции (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md) [грамматики формальных фигуры](../../../ado/guide/data/formal-shape-grammar.md) [службы для формирования данных Microsoft OLE DB (ADO поставщиком услуг)](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md) [объекта набора записей (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md) [необходимые поставщики данных формировать](../../../ado/guide/data/required-providers-for-data-shaping.md) [фигуры в предложении APPEND](../../../ado/guide/data/shape-append-clause.md) [Фигуры в целом команды](../../../ado/guide/data/shape-commands-in-general.md) [предложение COMPUTE фигуры](../../../ado/guide/data/shape-compute-clause.md) [Visual Basic для приложений функций](../../../ado/guide/data/visual-basic-for-applications-functions.md)
