---
title: "Выполнение запросов SQL (управляемые классы SQLXML) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: sqlxml
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-xml
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- queries [SQLXML], SQLXML Managed Classes
- SQLXML Managed Classes, executing SQL queries
- Managed Classes [SQLXML], executing SQL queries
- ExecuteToStream method
- SQL queries [SQLXML]
ms.assetid: a561ae83-a8b6-4b9b-a819-9b86839546b4
caps.latest.revision: "22"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0b5646075e480a00f5d3c9b78a45493b918c5229
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="executing-sql-queries-sqlxml-managed-classes"></a>Выполнение запросов SQL (управляемые классы SQLXML)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]В этом примере показано:  
  
-   Создание параметров (объекты SqlXmlParameter).  
  
-   Присвоение значений свойств объектов SqlXmlParameter (имя и значение).  
  
 В этом примере выполняется простой SQL-запрос, который получает фамилию, имя и дату рождения сотрудника, чья фамилия передается в качестве параметра. При указании параметра (*LastName*), задать свойство Value. Свойство Name не задано, так как в этом запросе параметр является позиционным, имя не является обязательным.  
  
 Свойство CommandType SqlXmlCommand, объект по умолчанию является **Sql**. Поэтому ему явно не присваивается значение.  
  
> [!NOTE]  
>  В коде необходимо задать имя экземпляра Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в строке соединения.  
  
 Далее приведен код C#.  
  
```  
using System;  
  
using Microsoft.Data.SqlXml;  
using System.IO;  
class Test  
{  
      static string ConnString = "Provider=SQLOLEDB;Server=(local);database=AdventureWorks;Integrated Security=SSPI";  
      public static int testParams()  
      {  
         Stream strm;  
         SqlXmlParameter p;  
         SqlXmlCommand cmd = new SqlXmlCommand(ConnString);        
         cmd.CommandText = "SELECT FirstName, LastName FROM Person.Contact WHERE LastName=? For XML Auto";  
         p = cmd.CreateParameter();  
         p.Value = "Achong";  
         string strResult;  
         try   
         {  
            strm = cmd.ExecuteStream();  
            strm.Position = 0;  
            using(StreamReader sr = new StreamReader(strm))  
            {  
               Console.WriteLine(sr.ReadToEnd());  
            }  
         }  
         catch (SqlXmlException e)  
         {  
            //in case of an error, this prints error returned.  
            e.ErrorStream.Position=0;  
            strResult=new StreamReader(e.ErrorStream).ReadToEnd();  
            System.Console.WriteLine(strResult);  
         }  
  
         return 0;  
   }  
public static int Main(String[] args)  
{  
    testParams();  
    return 0;  
}  
}  
```  
  
### <a name="to-test-the-application"></a>Тестирование приложения  
  
1.  Сохраните код C# (DocSample.cs), представленный в этом разделе, в папке.  
  
2.  Скомпилируйте код. Чтобы скомпилировать код из командной строки, введите следующую команду.  
  
    ```  
    csc /reference:Microsoft.Data.SqlXML.dll DocSample.cs  
    ```  
  
     Будет создан исполняемый файл (DocSample.exe).  
  
3.  Запустите файл DocSample.exe из командной строки.  
  
 Чтобы проверить этот пример, необходимо установить на компьютер платформу [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework.  
  
 Вместо указания запросов SQL в виде текста команды можно задать шаблон (как показано в следующем фрагменте кода), который выполняет диаграмму обновления (также шаблон) для вставки пользовательской записи. Можно задать шаблоны и диаграммы обновления в файлах и выполнить эти файлы. Дополнительные сведения см. в разделе [выполнение файлов шаблонов с помощью свойства CommandText](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/executing-template-files-by-using-the-commandtext-property.md).  
  
```  
SqlXmlCommand cmd = new SqlXmlCommand("Provider=SQLOLEDB;Data Source=SqlServerName;Initial Catalog=Database; Integrated Security=SSPI;");  
Stream stm;  
cmd.CommandType = SqlXmlCommandType.UpdateGram;  
cmd.CommandText = "<ROOT xmlns:sql='urn:schemas-microsoft-com:xml-sql' xmlns:updg='urn:schemas-microsoft-com:xml-updategram'>" +  
      "<updg:sync>" +  
       "<updg:before/>" +  
       "<updg:after>" +  
         "<Customer CustomerID='aaaaa' CustomerName='Some Name' CustomerTitle='SomeTitle' />" +  
       "</updg:after>" +  
       "</updg:sync>" +  
       "</ROOT>";  
  
stm = cmd.ExecuteStream();  
stm = null;  
cmd = null;  
```  
  
## <a name="using-executetostream"></a>Использование ExecuteToStream  
 Если имеется существующий поток, можно использовать метод ExecuteToStream вместо создания объекта потока и с помощью метода Execute. Код из предыдущего примера изменен для использования ExecuteToStream, метод:  
  
```  
using System;  
using Microsoft.Data.SqlXml;  
using System.IO;  
class Test  
{  
   static string ConnString = "Provider=SQLOLEDB;Server=SqlServerName;database=AdventureWorks;Integrated Security=SSPI;";  
   public static int testParams()  
   {  
      SqlXmlParameter p;  
      MemoryStream ms = new MemoryStream();  
      StreamReader sr = new StreamReader(ms);  
      ms.Position = 0;  
      SqlXmlCommand cmd = new SqlXmlCommand(ConnString);  
      cmd.CommandText = "select FirstName, LastName from Person.Contact where LastName = ? For XML Auto";  
      p = cmd.CreateParameter();  
      p.Value = "Achong";  
      cmd.ExecuteToStream(ms);  
      ms.Position = 0;  
      Console.WriteLine(sr.ReadToEnd());  
      return 0;        
   }  
   public static int Main(String[] args)  
   {  
      testParams();     
      return 0;  
   }  
}  
```  
  
> [!NOTE]  
>  Можно также использовать ExecuteXMLReadermethod, который возвращает объект XmlReader. Дополнительные сведения см. в разделе [выполнение запросов SQL с использованием метода ExecuteXMLReader](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/executing-sql-queries-by-using-the-executexmlreader-method.md).  
  
  
