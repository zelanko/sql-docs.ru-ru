---
description: Обзор простого поставщика Microsoft OLE DB
title: Простой поставщик Microsoft OLE DB | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- simple provider [ADO]
- providers [ADO], OLE DB simple provider
- OLE DB simple provider [ADO]
ms.assetid: 1e7dc6f0-482c-4103-8187-f890865e40fc
author: rothja
ms.author: jroth
ms.openlocfilehash: 4eb4635aafa67d2b6c96f88580811c204ff73423
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88990985"
---
# <a name="microsoft-ole-db-simple-provider-overview"></a>Обзор простого поставщика Microsoft OLE DB
Microsoft OLE DB Simple Provider (ОБЕЩАНие) позволяет ADO получать доступ к любым данным, для которых поставщик был написан с помощью [набора средств OLE DB простого поставщика (обещание)](/previous-versions/windows/desktop/ms715822(v=vs.85)). Простые поставщики предназначены для доступа к источникам данных, которым требуется только фундаментальная OLE DBная поддержка, например массивы в памяти или XML-документы.

## <a name="connection-string-parameters"></a>Параметры строки соединения
 Чтобы подключиться к библиотеке DLL простого поставщика OLE DB, задайте для аргумента *поставщика* в качестве значения свойства [ConnectionString](../../reference/ado-api/connectionstring-property-ado.md) значение:

```vb
MSDAOSP
```

 Это значение также может быть задано или считано с помощью свойства [provider](../../reference/ado-api/provider-property-ado.md) .

 Вы можете подключиться к простым поставщикам, зарегистрированным в качестве полных поставщиков OLE DB, используя зарегистрированное имя поставщика, определяемое модулем записи поставщика.

## <a name="typical-connection-string"></a>Типичная строка подключения
 Типичная строка подключения для этого поставщика:

```vb
"Provider=MSDAOSP;Data Source=serverName"
```

 Строка состоит из следующих ключевых слов:

|Ключевое слово|Описание|
|-------------|-----------------|
|**Поставщик**|Указывает поставщика OLE DB для SQL Server.|
|**Источник данных**|Указывает имя сервера.|

## <a name="xml-document-example"></a>Пример XML-документа
 OLE DB простой поставщик (ОБЕЩАНие) в MDAC 2,7 или более поздней версии и компоненты доступа к данным Windows (Windows DAC) были улучшены для поддержки открытия иерархических **наборов записей** ADO для ПРОИЗВОЛЬНЫХ XML-файлов. Эти XML-файлы могут содержать схему сохраняемости XML-данных ADO, но это необязательно. Это реализовано путем подключения ОБЕЩАНий к **MSXML2.DLL**; Поэтому требуется **MSXML2.DLL** или более поздней версии.

 Файл **portfolio.xml** , используемый в следующем примере, содержит следующее дерево:

```console
Portfolio
   Stock
      Shares
      Symbol
      Price
      Info
         Company Name
         WebSite
```

 XML-объекты DSO используют встроенные эвристики для преобразования узлов XML-дерева в главы в иерархическом **наборе записей**.

 Используя эти встроенные эвристики, XML-дерево преобразуется в иерархический **набор записей** следующего уровня:

```console
Parent Recordset
Shares, Symbol, Price, $Text
   Child Recordset
      Company Name, WebSite, $Text
```

 Обратите внимание, что теги Portfolio и info не представлены в иерархическом **наборе записей**. Объяснение того, как XML-объекты DSO преобразуют XML-деревья в иерархические **наборы записей**, см. в следующих правилах. $Text столбец рассматривается в следующем разделе.

## <a name="rules-for-assigning-xml-elements-and-attributes-to-columns-and-rows"></a>Правила назначения XML-элементов и атрибутов столбцам и строкам
 Объекты DSO XML следуют процедуре назначения элементов и атрибутов столбцам и строкам в приложениях, привязанных к данным. XML моделируется как дерево с одним тегом, содержащим всю иерархию. Например, XML-описание книги может содержать теги глав, Теги рисунков и теги разделов. На самом верхнем уровне будет использоваться тег Book, содержащий подэлементы главы, Figure и Section. Когда XML DSO сопоставляет XML-элементы со строками и столбцами, преобразуются вложенные элементы, а не элементы верхнего уровня.

 XML-объекты DSO используют эту процедуру для преобразования подэлементов.

-   Каждый подэлемент и атрибут соответствует столбцу в каком-либо **наборе записей** в иерархии.

-   Имя столбца совпадает с именем подэлемента или атрибута, если только родительский элемент не имеет атрибута и вложенного элемента с тем же именем. в этом случае "!" добавляется в начало имени столбца подэлемента.

-   Каждый столбец представляет собой либо *простой* столбец, содержащий скалярные значения (обычно строки), либо столбец **набора записей** , содержащий дочерние **наборы записей**.

-   Столбцы, соответствующие атрибутам, всегда просты.

-   Столбцы, соответствующие подэлементам, являются столбцами **набора записей** , если либо вложенный элемент имеет собственные подэлементы или атрибуты (или оба), либо родительский элемент имеет более одного экземпляра вложенного элемента. В противном случае столбец является простым.

-   Если имеется несколько экземпляров вложенного элемента (в разных родительских элементах), то его столбец является столбцом **набора записей** , если *любой* из экземпляров предполагает наличие столбца **набора записей** . его столбец является простым, только если *все* экземпляры предполагают простой столбец.

-   Все **наборы записей** имеют дополнительный столбец с именем $text.

 Код, необходимый для создания **набора записей** , выглядит следующим образом:

```vb
Dim adoConn as ADODB.Connection
Dim adoRS as ADODB.Recordset

Set adoRS = New ADODB.Connection
Set adoRS = New ADODB.Recordset

adoConn.Open "Provider=MSDAOSP; Data Source=MSXML2.DSOControl.2.6;"
adoRS.Open "https://WebServer/VRoot/portfolio.xml, adoConn
```

> [!NOTE]
>  Путь к файлу данных можно указать с помощью четырех различных соглашений об именовании.

```vb
'HTTP://
adoRS.Open "https://WebServer/VRoot/portfolio.xml", adoConn
'FILE://
adoRS.Open "file:/// C:\\Directory\\portfolio.xml", adoConn
'UNC Path
adoRS.Open "\\ComputerName\ShareName\portfolio.xml", adoConn
'Full DOS Path
adoRS.Open "C:\Directory\portfolio.xml", adoConn
```

 Как только **набор записей** будет открыт, можно использовать обычные команды навигации по **набору записей** ADO.

 **Наборы записей** , созданные обещанием, имеют ряд ограничений.

-   Клиентские курсоры (**адусеклиент**) не поддерживаются.

-   Иерархические **наборы записей** , созданные для ПРОИЗВОЛЬНЫХ XML-данных, не могут быть сохранены с помощью **Recordset. Save**.

-   **Наборы записей** , созданные с помощью обещаний, доступны только для чтения.

-   КСМЛДСО добавляет дополнительный столбец данных ($Text) к каждому **набору записей** в иерархии.

 Дополнительные сведения о OLE DB простого поставщика см. в разделе [Создание простого поставщика](/previous-versions/windows/desktop/ms721067(v=vs.85)).

## <a name="code-example"></a>Пример кода
 В следующем Visual Basic коде демонстрируется открытие произвольного XML-файла, создание иерархического **набора записей**и рекурсивное написание каждой записи каждого **набора записей** в окне отладки.

 Ниже приведен простой XML-файл, содержащий котировки котировок. В следующем коде этот файл используется для создания иерархического **набора записей**с двумя уровнями.

```xml
<portfolio>
   <stock>
      <shares>100</shares>
      <symbol>MSFT</symbol>
      <price>$70.00</price>
      <info>
         <companyname>Microsoft Corporation</companyname>
         <website>https://www.microsoft.com</website>
      </info>
   </stock>
   <stock>
      <shares>100</shares>
      <symbol>AAPL</symbol>
      <price>$107.00</price>
      <info>
         <companyname>Apple Computer, Inc.</companyname>
         <website>https://www.apple.com</website>
      </info>
   </stock>
   <stock>
      <shares>100</shares>
      <symbol>DELL</symbol>
      <price>$50.00</price>
      <info>
         <companyname>Dell Corporation</companyname>
         <website>https://www.dell.com</website>
      </info>
    </stock>
    <stock>
       <shares>100</shares>
       <symbol>INTC</symbol>
       <price>$115.00</price>
       <info>
          <companyname>Intel Corporation</companyname>
          <website>https://www.intel.com</website>
       </info>
   </stock>
</portfolio>
```

 Ниже приведены две процедуры Visual Basic. Первый создает **набор записей** и передает его в процедуру *валкхиер* , которая рекурсивно проходит по иерархии, записывая каждое **поле** в каждой записи в каждом **наборе записей** в окне отладки.

```vb
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
    adoRS.Open "https://bwillett3/Kowalski/portfolio.xml", adoConn

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