---
title: Простой поставщик Microsoft OLE DB | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- simple provider [ADO]
- providers [ADO], OLE DB simple provider
- OLE DB simple provider [ADO]
ms.assetid: 1e7dc6f0-482c-4103-8187-f890865e40fc
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: bc17df7bad00205803b33cb4af17cb3c6ddaac56
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66701284"
---
# <a name="microsoft-ole-db-simple-provider-overview"></a>Общие сведения о простой поставщик Microsoft OLE DB
Microsoft OLE DB простой поставщик (OSP) позволяет ADO на доступ к данным, для которого поставщик написанное с использованием [OLE DB простой поставщик (OSP) Toolkit](https://msdn.microsoft.com/6e7b7931-9e4a-4151-ae51-672abd3f84a6). Простые поставщики предназначены для доступа к источникам данных, требующих только фундаментальную поддержку OLE DB, таких как массивы в памяти или XML-документов.

## <a name="connection-string-parameters"></a>Параметры строки соединения
 Чтобы подключиться к OLE DB простой поставщик библиотеки DLL, задайте *поставщика* аргумент [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) свойства:

```vb
MSDAOSP
```

 Это значение можно также задать или прочитать с помощью [поставщика](../../../ado/reference/ado-api/provider-property-ado.md) свойство.

 Можно подключиться к простые поставщики, которые были зарегистрированы как полный поставщики OLE DB, используя имя зарегистрированного поставщика, определяется модулем записи поставщика.

## <a name="typical-connection-string"></a>Типичная строка подключения
 — Строка соединения для данного поставщика:

```vb
"Provider=MSDAOSP;Data Source=serverName"
```

 Строка состоит из следующих ключевых слов:

|Ключевое слово|Описание|
|-------------|-----------------|
|**Поставщик**|Определяет поставщика OLE DB для SQL Server.|
|**Источник данных**|Указывает имя сервера.|

## <a name="xml-document-example"></a>Пример XML-документа
 OLE DB простой поставщик (OSP) в MDAC 2.7 или более поздней версии и компоненты доступа к данным Windows (Windows DAC) была улучшена для поддержки, открыв иерархических ADO **наборы записей** через произвольные файлы XML. Эти XML-файлы могут содержать схему сохраняемости ADO XML, но это не обязательно. Это реализовано путем подключения Обещания для **MSXML2.DLL**; поэтому **MSXML2.DLL** или более поздней.

 **Portfolio.xml** следующее дерево содержит файл, используемый в следующем примере:

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

 XML DSO использует встроенные эвристические методы для преобразования узлов в дерево XML главы в иерархической **записей**.

 Используя эти встроена эвристика, XML-дерева преобразуется в двухуровневой иерархической **записей** следующего вида:

```console
Parent Recordset
Shares, Symbol, Price, $Text
   Child Recordset
      Company Name, WebSite, $Text
```

 Обратите внимание, что теги портфеля и сведения не представлены в иерархическое **записей**. Объяснение как XML DSO преобразует XML-деревьев, в иерархической **наборы записей**, см. следующие правила. Столбец $Text рассматривается в следующем разделе.

## <a name="rules-for-assigning-xml-elements-and-attributes-to-columns-and-rows"></a>Правила назначения XML-элементы и атрибуты для столбцов и строк
 XML DSO ниже процедуры для назначения элементов и атрибутов для столбцов и строк в приложениях с привязкой к данным. XML моделируется в виде дерева с помощью одного тега, содержащего всей иерархии. Например XML-описание книги может содержать теги Глава, теги и раздел тегов. На самом высоком уровне бы книга тег, содержащий подэлементов Глава, рисунок и разделе. При XML DSO сопоставляет XML-элементов, строк и столбцов, вложенные элементы, не элемент верхнего уровня, будут преобразованы.

 XML DSO использует эту процедуру для преобразования вложенные элементы:

-   Каждый дочерний элемент и атрибут соответствует столбцу в некоторых **записей** в иерархии.

-   Имя столбца совпадает имя вложенного элемента или атрибута, если только родительский элемент имеет атрибут и подэлемент с тем же именем, в этом случае «!» добавляется в начало имени столбца подэлемента.

-   Каждый столбец является либо *простой* столбец, содержащий скалярные значения (обычно строки) или **записей** столбец, содержащий дочерний **наборы записей**.

-   Столбцы, соответствующие атрибуты всегда являются простыми.

-   Столбцы, соответствующие дочерние элементы являются **записей** столбцы, если подэлемент имеет свой собственный вложенные элементы или атрибуты (или оба), либо дочерний элемент родителя есть несколько экземпляров вложенного элемента как дочерний элемент. В противном случае столбец является простой.

-   При наличии нескольких экземпляров вложенным элементом (разные родительские), соответствующий столбец используется **записей** столбец Если *любой* экземпляров подразумевают **записей** столбца; его столбец является простой только если *все* экземпляров подразумевают простой столбец.

-   Все **наборы записей** имеет дополнительный столбец с именем $Text.

 Код, который необходим для создания **записей** выглядит следующим образом:

```vb
Dim adoConn as ADODB.Connection
Dim adoRS as ADODB.Recordset

Set adoRS = New ADODB.Connection
Set adoRS = New ADODB.Recordset

adoConn.Open "Provider=MSDAOSP; Data Source=MSXML2.DSOControl.2.6;"
adoRS.Open "https://WebServer/VRoot/portfolio.xml, adoConn
```

> [!NOTE]
>  Путь к файлу данных можно указать с помощью четырех различных соглашения об именовании.

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

 Как только **набор записей** было установлено, обычные ADO **набор записей** команды навигации можно использовать.

 **Наборы записей** созданные Обещание действует ряд ограничений:

-   Клиентские курсоры (**adUseClient**) не поддерживаются.

-   Иерархические **наборы записей** создан для произвольных XML не могут быть сохранены с помощью **Recordset.Save**.

-   **Наборы записей** созданные с помощью Обещания доступны только для чтения.

-   XMLDSO добавляет дополнительный столбец данных ($Text) для каждой **записей** в иерархии.

 Дополнительные сведения о OLE DB простого поставщика, см. в разделе [создание простого поставщика](https://msdn.microsoft.com/b31a6cba-58ae-4ee8-9039-700973d354d6).

## <a name="code-example"></a>Пример кода
 Следующий код Visual Basic показано открытие произвольное XML-файл, создав иерархической **записей**и каждая запись каждого рекурсивно **записей** в окно отладки.

 Ниже приведен простой XML-файл, содержащий котировки акций. В следующем коде этот файл используется для создания двухуровневой иерархической **записей**.

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

 Ниже приведены две процедуры sub в Visual Basic. Создает первый **записей** и передает его *WalkHier* sub процедуры, какие рекурсивно вниз по иерархии, написание каждого **поле** в каждой записи в каждом **Записей** в окно отладки.

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
