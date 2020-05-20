---
title: Доступ к строкам в иерархическом наборе записей | Документация Майкрософт
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 2eacfa8122589dbf594040f3279d466ef9c113cd
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82761492"
---
# <a name="accessing-rows-in-a-hierarchical-recordset-example"></a>Доступ к строкам в иерархическом наборе записей (пример)
В следующем примере показаны шаги, необходимые для доступа к строкам в иерархическом [наборе записей](../../../ado/reference/ado-api/recordset-object-ado.md).

1.  Объекты **набора записей** из таблиц **authors** и **титлеаусор** связаны по идентификатору автора.

2.  Внешний цикл отображает имя и фамилию каждого автора, состояние и идентификацию.

3.  Добавленный **набор записей** для каждой строки извлекается из коллекции [полей](../../../ado/reference/ado-api/fields-collection-ado.md) и назначается *рсттитлеаусор*.

4.  Внутренний цикл отображает четыре поля из каждой строки в присоединенном **наборе записей**.

 Для иллюстрации в качестве значения свойства [StayInSync](../../../ado/reference/ado-api/stayinsync-property.md) задано **значение false** , чтобы можно было увидеть изменение главы явным образом в каждой итерации внешнего цикла. Чтобы сделать пример кода более эффективным, можно переместить назначение на шаге 3 перед первой строкой шага 2, чтобы назначение выполнялось только один раз. Затем задайте для свойства [StayInSync](../../../ado/reference/ado-api/stayinsync-property.md) **значение true**, чтобы *рсттитлеаусор* неявно и автоматически переменялся в соответствующую главу, когда *RST* перейдет в новую строку.

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
 [Общие сведения об обработке данных](../../../ado/guide/data/data-shaping-overview.md) [поле](../../../ado/reference/ado-api/field-object.md) [коллекции Fields (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md) [формальное описание грамматики фигур](../../../ado/guide/data/formal-shape-grammar.md) [Служба формирования данных Майкрософт для OLE DB (поставщик служб ADO)](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md) [объекты набора записей (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md) [необходимые поставщики для операций](../../../ado/guide/data/required-providers-for-data-shaping.md) [добавления](../../../ado/guide/data/shape-append-clause.md) формы формирования данных [команды Shape в общем](../../../ado/guide/data/shape-commands-in-general.md) [Visual Basic для приложений](../../../ado/guide/data/visual-basic-for-applications-functions.md) [предложении COMPUTE](../../../ado/guide/data/shape-compute-clause.md)
