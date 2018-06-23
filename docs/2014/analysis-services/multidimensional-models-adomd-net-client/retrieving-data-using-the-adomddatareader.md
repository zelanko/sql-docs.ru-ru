---
title: Получение данных с помощью объекта AdomdDataReader | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- retrieving data
- AdomdDataReader object
- data retrieval [ADOMD.NET], AdomdDataReader object
ms.assetid: 8ed7ea26-b5f8-4852-80fc-75dd62df5b3a
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 17ed47d13aab29ea47c5f1d041705029844e359e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36095144"
---
# <a name="retrieving-data-using-the-adomddatareader"></a>Получение данных с помощью объекта AdomdDataReader
  Что касается извлечения аналитических данных, объект <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> обеспечивает достижение приемлемого равновесия между издержками и интерактивностью. Объект <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> извлекает из источника аналитических данных поток данных, предназначенный только для чтения и последовательного доступа, преобразованный в плоский формат. Этот небуферизованный поток данных позволяет применять процедурные средства для последовательной обработки результатов, получаемых из источника аналитических данных, с высокой эффективностью. Поэтому объект <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> хорошо подходит для извлечения больших объемов данных в целях отображения, поскольку данные не кэшируются в памяти.  
  
 Применение объекта <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> способствует также повышению производительности приложения, поскольку обеспечивает извлечение данных по мере их поступления, не дожидаясь полного возврата результатов запроса. Кроме того, объект <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> сокращает системные издержки, поскольку по умолчанию этот модуль чтения сохраняет в памяти только одну строку одновременно.  
  
 Платой за оптимизированную производительность является то, что объект <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> предоставляет меньше сведений об извлеченных данных, чем другие методы получения данных. Объект <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> не поддерживает большие модели объектов для представления данных или метаданных, кроме того, эта модель объектов не позволяет использовать более сложные аналитические функции, такие как обратная запись в ячейку. Однако объект <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> все же предоставляет набор строго типизированных методов для извлечения данных набора ячеек, а также метод для извлечения метаданных набора ячеек в табличном формате. Кроме того <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> реализует **IDbDataReader** интерфейс для поддержки привязки данных, а также для получения данных с помощью `SelectCommand` метода из **System.Data** пространство имен Библиотека классов Microsoft .NET Framework.  
  
## <a name="retrieving-data-from-the-adomddatareader"></a>Извлечение данных из AdomdDataReader  
 Чтобы получить данные с помощью объекта <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>, выполните следующие действия.  
  
1.  **Создайте новый экземпляр объекта.**  
  
     Для создания нового экземпляра класса <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> вызывается метод <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.Execute%2A> или <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteReader%2A> объекта <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand>.  
  
2.  **Получение данных.**  
  
     По мере выполнения командой запроса компонент ADOMD.NET возвращает результаты в формате `Resultset`, т. е. табличном формате, описанном в спецификации протокола XML для аналитики, чтобы можно было преобразовать данные в плоскую форму для объекта <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>. С учетом переменной размерности аналитических данных табличный формат при запросе к ним используется редко.  
  
     Компонент ADOMD.NET хранит эти табличные результаты в сетевом буфере на клиенте, пока они не будут запрошены при помощи одного из следующих методов.  
  
    -   Вызовите метод <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader.Read%2A> объекта <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>.  
  
         Метод <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader.Read%2A> получает строку из результатов запроса. Затем можно передать имя или порядковый номер столбца свойству <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader.Item%2A>, чтобы получить доступ к каждому столбцу возвращенной строки. Например, имя первого столбца текущей строки — ColumnName. В этом случае либо метод `reader[0].ToString()`, либо метод `reader["ColumnName"].ToString()` возвратит содержимое первого столбца в текущей строке.  
  
    -   Вызовите один из типизированных методов доступа.  
  
         Объект <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> предоставляет ряд типизированных методов доступа — тех методов, которые позволяют получать доступ к значениям столбцов в собственных типах данных. Если базовый тип данных значения столбца известен, типизированный метод доступа позволяет сократить объем преобразования типов, необходимый при извлечении значения столбца, обеспечивая тем самым наивысшую производительность.  
  
         Некоторые типизированные методы доступа — <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader.GetDateTime%2A>, <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader.GetDouble%2A> и <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader.GetInt32%2A>. Полный список типизированных методов доступа см. в разделе <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>.  
  
3.  **Закройте средство чтения.**  
  
     Необходимо вызывать метод <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader.Close%2A> после завершения работы с объектом <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>. Пока открыт экземпляр объекта <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>, метод <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> используется исключительно этим объектом <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>. Невозможно выполнить какую-либо команду для экземпляра объекта <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>, включая создание еще одного объекта <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> или `System.Xml.XmlReader`, пока не закрыт исходный объект <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>.  
  
### <a name="example-of-retrieving-data-from-the-adomddatareader"></a>Пример извлечения данных из AdomdDataReader  
 В следующем примере кода просматриваются результаты, возвращенные объектом <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>, и возвращаются два первых значения для каждой строки в виде строк.  
  
```vb  
If Reader.HasRows Then  
    Do While objReader.Read()  
        Console.WriteLine(vbTab & "{0}" & vbTab & "{1}", _  
            objReader.GetString(0), objReader.GetString(1))  
    Loop  
Else  
  Console.WriteLine("No rows returned.")  
End If  
  
objReader.Close()  
```  
  
```csharp  
if (objReader.HasRows)  
  while (objReader.Read())  
    Console.WriteLine("\t{0}\t{1}", _  
        objReader.GetString(0), objReader.GetString(1));  
else  
  Console.WriteLine("No rows returned.");  
  
objReader.Close();  
```  
  
## <a name="retrieving-metadata-from-the-adomddatareader"></a>Извлечение метаданных из AdomdDataReader  
 Пока экземпляр объекта <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> открыт, можно извлечь данные схемы или метаданные о текущем наборе записей с помощью метода <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader.GetSchemaTable%2A>. <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader.GetSchemaTable%2A>Возвращает `DataTable` , заполненный данными схемы для текущего набора записей. Объект `DataTable` включает по одной строке для каждого столбца набора записей. Каждый столбец строки таблицы схемы соответствует свойству столбца, возвращенного в наборе ячеек, где `ColumnName` — это имя свойства, а значение столбца — это значение свойства.  
  
### <a name="example-of-retrieving-metadata-from-the-adomddatareader"></a>Пример извлечения метаданных из AdomdDataReader  
 В следующем примере кода на консоль выводятся данные схемы для объекта <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>.  
  
```vb  
Dim schemaTable As DataTable = objReader.GetSchemaTable()  
  
Dim objRow As DataRow  
Dim objColumn As DataColumn  
  
For Each objRow In schemaTable.Rows  
  For Each objColumn In schemaTable.Columns  
    Console.WriteLine(objColumn.ColumnName & " = " & objRow(objColumn).ToString())  
  Next  
  Console.WriteLine()  
Next  
DataTable schemaTable = objReader.GetSchemaTable();  
```  
  
```csharp  
foreach (DataRow objRow in schemaTable.Rows)  
{  
  foreach (DataColumn objColumn in schemaTable.Columns)  
    Console.WriteLine(objColumn.ColumnName + " = " + objRow[objColumn]);  
  Console.WriteLine();  
}  
```  
  
## <a name="retrieving-multiple-result-sets"></a>Извлечение нескольких результирующих наборов  
 Интеллектуальный анализ данных поддерживает концепцию вложенных таблиц, к которым ADOMD.NET предоставляет доступ как к вложенным наборам строк. Чтобы извлечь вложенный набор строк, связанный с каждой строкой, вызывается метод <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader.GetDataReader%2A>.  
  
## <a name="see-also"></a>См. также  
 [Получение данных из источника аналитических данных](retrieving-data-from-an-analytical-data-source.md)   
 [Получение данных с помощью набора ячеек](retrieving-data-using-the-cellset.md)   
 [Получение данных с помощью объекта XmlReader](retrieving-data-using-the-xmlreader.md)  
  
  