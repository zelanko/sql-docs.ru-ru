---
title: Запуск DiffGram с помощью управляемых классов SQLXML | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- DiffGrams [SQLXML], Managed Classes
- SQLXML Managed Classes, DiffGrams
- Managed Classes [SQLXML], DiffGrams
- SQLXML, Managed Classes
ms.assetid: 81c687ca-8c9f-4f58-801f-8dabcc508a06
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3d8756bb3dc7b030541159c2aa127162907aa4b5
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66013049"
---
# <a name="executing-a-diffgram-by-using-sqlxml-managed-classes"></a>Выполнение дельты с использованием управляемых классов SQLXML
  В этом примере показано, как выполнить файл DiffGram в среде [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework, чтобы применить обновления данных к [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] таблицам с помощью управляемых классов SQLXML (Microsoft. Data. SQLXML).  
  
 В этом примере дельта обновляет CompanyName и ContactName для клиента ALFKI.  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql" sql:mapping-schema="DiffGramSchema.xml">  
  <diffgr:diffgram   
           xmlns:msdata="urn:schemas-microsoft-com:xml-msdata"   
           xmlns:diffgr="urn:schemas-microsoft-com:xml-diffgram-v1">  
    <DataInstance>  
      <Customer diffgr:id="Customer1"   
                msdata:rowOrder="0" diffgr:hasChanges="modified"   
                CustomerID="ALFKI">  
          <CompanyName>Bottom Dollar Markets</CompanyName>  
          <ContactName>Antonio Moreno</ContactName>  
      </Customer>  
    </DataInstance>  
    <diffgr:before>  
     <Customer diffgr:id="Customer1"   
               msdata:rowOrder="0"   
               CustomerID="ALFKI">  
        <CompanyName>Alfreds Futterkiste</CompanyName>  
        <ContactName>Maria Anders</ContactName>  
      </Customer>  
    </diffgr:before>  
  </diffgr:diffgram>  
</ROOT>  
```  
  
 Блок ** \<Before>** включает элемент ** \<>Customer** (**diffgr: ID = "Customer1"**). Блок>instance содержит соответствующий ** \<элемент>Customer** с тем же **идентификатором**. ** \<** Элемент ** \<Customer>** в ** \<невдатасет>** также указывает **diffgr: hasChanges = "Modified"**. Это указывает на операцию по обновлению, и запись о заказчике в таблице Cust соответствующим образом обновляется. Обратите внимание, что если атрибут **diffgr: hasChanges** не указан, логика обработки DiffGram игнорирует этот элемент и обновления не выполняются.  
  
 Ниже приведен код для учебного приложения C#, в котором показано, как использовать управляемые классы SQLXML для выполнения приведенного выше DiffGram и обновления двух таблиц (Cust, пособий), которые также будут созданы в базе данных **tempdb** .  
  
```  
using System;  
using System.Data;  
using Microsoft.Data.SqlXml;  
using System.IO;  
class Test  
{  
   static string ConnString = "Provider=SQLOLEDB;Server=MyServer;database=tempdb;Integrated Security=SSPI;";  
   public static int testParams()  
   {  
      SqlXmlAdapter ad;  
      // Need a memory stream to hold diff gram temporarily  
      MemoryStream ms = new MemoryStream();  
      SqlXmlCommand cmd = new SqlXmlCommand(ConnString);  
      cmd.RootTag = "ROOT";  
      cmd.CommandStream = new FileStream("MyDiffgram.xml", FileMode.Open, FileAccess.Read);  
      cmd.CommandType = SqlXmlCommandType.DiffGram;  
      cmd.SchemaPath = "DiffGramSchema.xml";  
      // Load data set  
      DataSet ds = new DataSet();  
      ad = new SqlXmlAdapter(cmd);  
      ad.Fill(ds);  
      ad.Update(ds);  
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
  
1.  Проследите за тем, чтобы на вашем компьютере была установлена инфраструктура .NET Framework.  
  
2.  Сохраните в папке следующую схему XSD (DiffGramSchema.xml):  
  
    ```  
    <xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
                xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
     <xsd:annotation>  
      <xsd:documentation>  
        Diffgram Customers/Orders Schema.  
      </xsd:documentation>  
      <xsd:appinfo>  
           <sql:relationship name="CustomersOrders"   
                      parent="Cust"  
                      parent-key="CustomerID"  
                      child-key="CustomerID"  
                      child="Ord"/>  
      </xsd:appinfo>  
     </xsd:annotation>  
     <xsd:element name="Customer" sql:relation="Cust">  
      <xsd:complexType>  
        <xsd:sequence>  
          <xsd:element name="CompanyName"    type="xsd:string"/>  
          <xsd:element name="ContactName"    type="xsd:string"/>  
           <xsd:element name="Order" sql:relation="Ord" sql:relationship="CustomersOrders">  
            <xsd:complexType>  
              <xsd:attribute name="OrderID" type="xsd:int" sql:field="OrderID"/>  
              <xsd:attribute name="CustomerID" type="xsd:string"/>  
            </xsd:complexType>  
          </xsd:element>  
        </xsd:sequence>  
        <xsd:attribute name="CustomerID" type="xsd:string" sql:field="CustomerID"/>  
      </xsd:complexType>  
     </xsd:element>  
    </xsd:schema>  
    ```  
  
3.  Создайте эти таблицы в базе данных **tempdb** .  
  
    ```  
    CREATE TABLE Cust(  
            CustomerID  nchar(5) Primary Key,  
            CompanyName nvarchar(40) NOT NULL ,  
            ContactName nvarchar(60) NULL)  
    GO  
  
    CREATE TABLE Ord(  
       OrderID    int Primary Key,  
       CustomerID nchar(5) Foreign Key REFERENCES Cust(CustomerID))  
    GO  
    ```  
  
4.  Добавьте следующий образец данных:  
  
    ```  
    INSERT INTO Cust(CustomerID, CompanyName, ContactName) VALUES  
         (N'ALFKI', N'Alfreds Futterkiste', N'Maria Anders')  
    INSERT INTO Cust(CustomerID, CompanyName, ContactName) VALUES  
         (N'ANATR', N'Ana Trujillo Emparedados y helados', N'Ana Trujillo')  
    INSERT INTO Cust(CustomerID, CompanyName, ContactName) VALUES  
         (N'ANTON', N'Antonio Moreno Taquer??a', N'Antonio Moreno')  
  
    INSERT INTO Ord(OrderID, CustomerID) VALUES(1, N'ALFKI')  
    INSERT INTO Ord(OrderID, CustomerID) VALUES(2, N'ANATR')  
    INSERT INTO Ord(OrderID, CustomerID) VALUES(3, N'ANTON')  
    ```  
  
5.  Скопируйте приведенную выше дельту и вставьте ее в текстовый файл. Сохраните файл с именем MyDiffGram.xml в папке, которая использовалась на шаге 1.  
  
6.  Сохраните помещенный выше код на языке C# (DiffgramSample.cs) в той же папке, в которой при выполнении предшествующих шагов были сохранены файлы DiffGramSchema.xml и MyDiffGram.xml.  
  
    > [!NOTE]  
    >  При этом потребуется обновить имя экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в строке соединения, то есть заменить имя «`MyServer`» на фактическое имя установленного экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
     Если сохранить файлы в разных папках, то придется изменить код, указав путь к каталогу, в котором находится схема сопоставления.  
  
7.  Скомпилируйте код. Чтобы скомпилировать код из командной строки, введите следующую команду.  
  
    ```  
    csc /reference:Microsoft.Data.SqlXML.dll DiffgramSample.cs  
    ```  
  
     В результате создается исполняемый файл (DiffgramSample.exe).  
  
8.  Из командной строки выполните файл DiffgramSample.exe.  
  
## <a name="see-also"></a>См. также  
 [Примеры DiffGram &#40;SQLXML 4,0&#41;](diffgram-examples-sqlxml-4-0.md)  
  
  
