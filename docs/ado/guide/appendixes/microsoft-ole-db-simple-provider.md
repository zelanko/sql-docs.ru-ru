---
title: Простой поставщик Microsoft OLE DB | Документы Microsoft
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
helpviewer_keywords:
- simple provider [ADO]
- providers [ADO], OLE DB simple provider
- OLE DB simple provider [ADO]
ms.assetid: 1e7dc6f0-482c-4103-8187-f890865e40fc
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b7e4a5742b9d5b084d10540737ac87c55d441d0a
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="microsoft-ole-db-simple-provider-overview"></a>Общие сведения о простой поставщик Microsoft OLE DB
Microsoft OLE DB простого поставщика (Обещание) обеспечивает доступ к данным, для которых поставщик будет записана с помощью ADO [OLE DB простого поставщика (OSP) Toolkit](http://msdn.microsoft.com/en-us/6e7b7931-9e4a-4151-ae51-672abd3f84a6). Простые поставщики предназначены для доступа к источникам данных, которые требуют только основных поддержки OLE DB, например в памяти массивов или XML-документов.

## <a name="connection-string-parameters"></a>Параметры строки соединения
 Чтобы подключиться к Библиотеки OLE-DB простого поставщика, установите *поставщика* аргумент [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) свойства:

```
MSDAOSP
```

 Это значение можно также задать или прочитать с помощью [поставщика](../../../ado/reference/ado-api/provider-property-ado.md) свойство.

 Можно подключиться к простые поставщики, зарегистрированные как полный поставщики OLE DB с помощью зарегистрированного поставщика имя, определяется модулем записи поставщика.

## <a name="typical-connection-string"></a>Обычная строка соединения
 — Строка соединения для данного поставщика:

```
"Provider=MSDAOSP;Data Source=serverName"
```

 Строка состоит из следующих ключевых слов:

|Ключевое слово|Описание|
|-------------|-----------------|
|**Поставщик**|Определяет поставщик OLE DB для SQL Server.|
|**Источник данных**|Указывает имя сервера.|

## <a name="xml-document-example"></a>Пример документа XML
 OLE DB простого поставщика (OSP) MDAC 2.7 или более поздней версии и компоненты доступа к данным Windows (Windows DAC) был расширен и теперь поддерживает открытие иерархических ADO **наборы записей** через произвольные файлы XML. Эти XML-файлы могут содержать схему сохраняемости ADO XML, но он не является обязательным. Реализована путем подключения Обещания для **MSXML2.DLL**; поэтому **MSXML2.DLL** или более поздней версии.

 **Portfolio.xml** файл используется в следующем примере, содержит следующее дерево:

```
Portfolio
   Stock
      Shares
      Symbol
      Price
      Info
         Company Name
         WebSite
```

 XML DSO использует встроенные эвристику для преобразования узлов в XML-дерева в главах в иерархической **записей**.

 С помощью таких встроенных методов, XML-дерева преобразуется в двухуровневой иерархические **записей** следующего вида:

```
Parent Recordset
Shares, Symbol, Price, $Text
   Child Recordset
      Company Name, WebSite, $Text
```

 Обратите внимание, что теги портфеля и сведения не отображаются в иерархическое **записей**. Объяснение как XML DSO преобразует XML-деревьев в иерархической **наборы записей**, см. следующие правила. Столбец $Text рассматривается в следующем разделе.

## <a name="rules-for-assigning-xml-elements-and-attributes-to-columns-and-rows"></a>Правила назначения XML-элементы и атрибуты для столбцов и строк
 XML DSO ниже процедуру для назначения элементы и атрибуты столбцов и строк в приложениях с привязкой к данным. XML моделируется в виде дерева с помощью одного тега, содержащего всей иерархии. Например XML-описание книги может содержать теги главе, теги и раздел тегов. Тег книги, содержащий главе вложенные элементы, рисунок и разделе бы на самом высоком уровне. При XML DSO сопоставляет XML-элементов строк и столбцов, преобразование подэлементы, а не элемент верхнего уровня.

 XML DSO использует эту процедуру для преобразования вложенные элементы:

-   Каждый дочерний элемент и атрибут соответствует столбцу в некоторых **записей** в иерархии.

-   Представляет имя столбца совпадает с именем вложенного элемента или атрибута, если только родительский элемент имеет атрибут и подчиненный элемент с тем же именем в этом случае «!» добавляется в начало имени столбца дочерний элемент.

-   Каждый столбец является либо *простой* столбец, содержащий скалярные значения (обычно строки) или **записей** столбец, содержащий дочерние **наборы записей**.

-   Столбцы, соответствующие атрибуты всегда являются простыми.

-   Столбцы, соответствующие дочерние элементы являются **записей** столбцы, если подэлемент имеет свой собственный вложенных элементов или атрибутов (или оба), либо дочерний элемент родительского имеет более одного экземпляра вложенного элемента как дочерний элемент. В противном случае столбец является простой.

-   При наличии нескольких экземпляров вложенного (в разных родительских элементов), его столбец используется **записей** столбца Если *любой* экземпляров подразумевают **записей** столбца; его столбец является простым только тогда, когда *все* экземпляров подразумевают простой столбец.

-   Все **наборы записей** дополнительный столбец с именем $Text.

 Код, который необходим для создания **записей** выглядит следующим образом:

```
Dim adoConn as ADODB.Connection
Dim adoRS as ADODB.Recordset

Set adoRS = New ADODB.Connection
Set adoRS = New ADODB.Recordset

adoConn.Open "Provider=MSDAOSP; Data Source=MSXML2.DSOControl.2.6;"
adoRS.Open "http://WebServer/VRoot/portfolio.xml, adoConn
```

> [!NOTE]
>  Путь к файлу данных можно указать с помощью четырех различных соглашения об именовании.

```
'HTTP://
adoRS.Open "http://WebServer/VRoot/portfolio.xml", adoConn
'FILE://
adoRS.Open "file:/// C:\\Directory\\portfolio.xml", adoConn
'UNC Path
adoRS.Open "\\ComputerName\ShareName\portfolio.xml", adoConn
'Full DOS Path
adoRS.Open "C:\Directory\portfolio.xml", adoConn
```

 Как можно скорее **записей** открыт, обычные ADO **записей** можно использовать команды навигации.

 **Наборы записей** созданные Обещание действует ряд ограничений:

-   Клиентские курсоры (**adUseClient**) не поддерживаются.

-   Иерархические **наборы записей** создается произвольный XML не могут быть сохранены с помощью **Recordset.Save**.

-   **Наборы записей** созданными Обещание доступны только для чтения.

-   XMLDSO добавляет дополнительный столбец данных ($Text) к каждому **записей** в иерархии.

 Дополнительные сведения о поставщике OLE DB простой см. в разделе [создание простого поставщика](http://msdn.microsoft.com/en-us/b31a6cba-58ae-4ee8-9039-700973d354d6).

## <a name="code-example"></a>Пример кода
 Следующий код Visual Basic показано открытие произвольных XML-файл, создав иерархической **набора записей**и каждая запись каждого рекурсивно **набора записей** в окно отладки.

 Ниже приведен простой XML-файл, содержащий котировки акций. Этот файл следующий код используется для создания иерархических двухуровневой **записей**.

```
<portfolio>
   <stock>
      <shares>100</shares>
      <symbol>MSFT</symbol>
      <price>$70.00</price>
      <info>
         <companyname>Microsoft Corporation</companyname>
         <website>http://www.microsoft.com</website>
      </info>
   </stock>
   <stock>
      <shares>100</shares>
      <symbol>AAPL</symbol>
      <price>$107.00</price>
      <info>
         <companyname>Apple Computer, Inc.</companyname>
         <website>http://www.apple.com</website>
      </info>
   </stock>
   <stock>
      <shares>100</shares>
      <symbol>DELL</symbol>
      <price>$50.00</price>
      <info>
         <companyname>Dell Corporation</companyname>
         <website>http://www.dell.com</website>
      </info>
    </stock>
    <stock>
       <shares>100</shares>
       <symbol>INTC</symbol>
       <price>$115.00</price>
       <info>
          <companyname>Intel Corporation</companyname>
          <website>http://www.intel.com</website>
       </info>
   </stock>
</portfolio>
```

 Ниже приведены две процедуры sub в Visual Basic. В первом создается **записей** и передает их в *WalkHier* sub процедура, какие рекурсивно вниз по иерархии, каждая запись **поле** в каждой записи в каждом **Записей** в окно отладки.

```
Private Sub BrowseHierRecordset()
' Add ADO 2.7 or later to Project/References
' No need to add MSXML2, ADO just passes the ProgID through to the OSP.

    Dim adoConn As ADODB.Connection
    Dim adoRS As ADODB.Recordset
    Dim adoChildRS As ADODB.Recordset

    Set adoConn = New ADODB.Connection
    Set adoRS = New ADODB.Recordset
    Set adoChildRS = ADODB.Recordset

    adoConn.Open "Provider=MSDAOSP; Data Source=MSXML2.DSOControl.2.6;"
    adoRS.Open "http://bwillett3/Kowalski/portfolio.xml", adoConn

    Dim iLevel As Integer
    iLevel = 0
    WalkHier iLevel, adoRS

End Sub

Sub WalkHier(ByVal iLevel As Integer, ByVal adoRS As ADODB.Recordset)
    iLevel = iLevel + 1
    PriorLevel = iLevel
    While Not adoRS.EOF
        For ndx = 0 To adoRS.Fields.Count - 1
            If adoRS.Fields(ndx).Name <> "$Text" Then
                If adoRS.Fields(ndx).Type = adChapter Then
                    Set adoChildRS = adoRS.Fields(ndx).Value
                    WalkHier iLevel, adoChildRS
                Else
                    Debug.Print iLevel & ": adoRS.Fields(" & ndx & _
                       ") = " & adoRS.Fields(ndx).Name & " = " & _
                       adoRS.Fields(ndx).Value
                End If
            End If
        Next ndx
        adoRS.MoveNext
    Wend
    iLevel = PriorLevel
End Sub
```
