---
title: "С помощью внешнего набора данных со службами Reporting Services | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- DataSet objects [Reporting Services]
- data processing extensions [Reporting Services], custom DataSet objects
- custom DataSet objects [Reporting Services]
- external DataSet objects [Reporting Services]
ms.assetid: 11daa013-ec17-4760-80e3-6d84cd8d5722
caps.latest.revision: 49
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: add18839976ae919686cbd488385531de3bf684e
ms.contentlocale: ru-ru
ms.lasthandoff: 08/12/2017

---
# <a name="using-an-external-dataset-with-reporting-services"></a>Использование внешнего набора данных со службами Reporting Services
  **DataSet** является центральным элементом поддержки разъединенных распределенных сценариев данных в [!INCLUDE[vstecado](../../../includes/vstecado-md.md)]. **DataSet** объекта является находящихся в памяти представлением данных, обеспечивающим согласованную реляционную программную модель независимо от источника данных. Он может использоваться с несколькими различными источниками данных, XML-данными или для управления данными, локальными по отношению к приложению. **DataSet** объект представляет полный набор данных, включая связанные таблицы, ограничения и связи между таблицами. Из-за **DataSet** объекта обладает высокой гибкостью хранения и представления данных, данные могут часто обрабатываются и преобразуются в **DataSet** объекта перед созданием отчетов по этим данным.  
  
 С [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] модулей обработки данных, можно интегрировать любые пользовательские **DataSet** объекты, созданные внешними приложениями. Чтобы сделать это, создайте пользовательский модуль обработки данных в [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] который действует как мост между вашей **DataSet** объект и на сервере отчетов. Большая часть кода для обработки данного **DataSet** объект содержится в **DataReader** создаваемого класса.  
  
 Первым шагом в представлении вашей **DataSet** объекта на сервер отчетов является реализация характерного для поставщика метода в вашей **DataReader** класс, который может заполнить **набора данных** объекта. В следующем примере показано, как загрузить статические данные в **DataSet** объекта с помощью метода поставщика в вашей **DataReader** класса.  
  
```vb  
'Private members of the DataReader class  
Private m_dataSet As System.Data.DataSet  
Private m_currentRow As Integer  
  
'Method to create a dataset  
Friend Sub CreateDataSet()  
   ' Create a dataset.  
   Dim ds As New System.Data.DataSet("myDataSet")  
   ' Create a data table.   
   Dim dt As New System.Data.DataTable("myTable")  
   ' Create a data column and set various properties.   
   Dim dc As New System.Data.DataColumn()  
   dc.DataType = System.Type.GetType("System.Decimal")  
   dc.AllowDBNull = False  
   dc.Caption = "Number"  
   dc.ColumnName = "Number"  
   dc.DefaultValue = 25  
   ' Add the column to the table.   
   dt.Columns.Add(dc)  
   ' Add 10 rows and set values.   
   Dim dr As System.Data.DataRow  
   Dim i As Integer  
   For i = 0 To 9  
      dr = dt.NewRow()  
      dr("Number") = i + 1  
      ' Be sure to add the new row to the DataRowCollection.   
      dt.Rows.Add(dr)  
   Next i  
  
   ' Fill the dataset.  
   ds.Tables.Add(dt)  
  
   ' Use a private variable to store the dataset in your  
   ' DataReader.  
   m_dataSet = ds  
  
   ' Set the current row to -1.  
   m_currentRow = - 1  
End Sub 'CreateDataSet  
```  
  
```csharp  
// Private members of the DataReader class  
private System.Data.DataSet m_dataSet;  
private int m_currentRow;  
  
// Method to create a dataset  
internal void CreateDataSet()  
{  
   // Create a dataset.  
   System.Data.DataSet ds = new System.Data.DataSet("myDataSet");  
   // Create a data table.   
   System.Data.DataTable dt = new System.Data.DataTable("myTable");  
   // Create a data column and set various properties.   
   System.Data.DataColumn dc = new System.Data.DataColumn();   
   dc.DataType = System.Type.GetType("System.Decimal");   
   dc.AllowDBNull = false;   
   dc.Caption = "Number";   
   dc.ColumnName = "Number";   
   dc.DefaultValue = 25;   
   // Add the column to the table.   
   dt.Columns.Add(dc);   
   // Add 10 rows and set values.   
   System.Data.DataRow dr;   
   for(int i = 0; i < 10; i++)  
   {   
      dr = dt.NewRow();   
      dr["Number"] = i + 1;   
      // Be sure to add the new row to the DataRowCollection.   
      dt.Rows.Add(dr);  
   }  
  
   // Fill the dataset.  
   ds.Tables.Add(dt);  
  
   // Use a private variable to store the dataset in your  
   // DataReader.  
   m_dataSet = ds;  
  
   // Set the current row to -1.  
   m_currentRow = -1;  
}  
```  
  
```csharp  
public bool Read()  
{  
   m_currentRow++;  
   if (m_currentRow >= m_dataSet.Tables[0].Rows.Count)   
   {  
      return (false);  
   }   
   else   
   {  
      return (true);  
   }  
}  
  
public int FieldCount  
{  
   // Return the count of the number of columns, which in  
   // this case is the size of the column metadata  
   // array.  
   get { return m_dataSet.Tables[0].Columns.Count; }  
}  
  
public string GetName(int i)  
{  
   return m_dataSet.Tables[0].Columns[i].ColumnName;  
}  
  
public Type GetFieldType(int i)  
{  
   // Return the actual Type class for the data type.  
   return m_dataSet.Tables[0].Columns[i].DataType;  
}  
  
public Object GetValue(int i)  
{  
   return m_dataSet.Tables[0].Rows[m_currentRow][i];  
}  
  
public int GetOrdinal(string name)  
{  
   // Look for the ordinal of the column with the same name and return it.  
   // Returns -1 if not found.  
   return m_dataSet.Tables[0].Columns[name].Ordinal;  
}  
```  
  
 После создания или получения набора данных, можно использовать **DataSet** объекта в реализации методов **чтения**, **GetValue**, **GetName**, **GetOrdinal**, **GetFieldType**, и **FieldCount** члены **DataReader** класса.  
  
## <a name="see-also"></a>См. также:  
 [Модули служб Reporting Services](../../../reporting-services/extensions/reporting-services-extensions.md)   
 [Реализация модуля обработки данных](../../../reporting-services/extensions/data-processing/implementing-a-data-processing-extension.md)   
 [Библиотека служб Reporting Services расширения](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
