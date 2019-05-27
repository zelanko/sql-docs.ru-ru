---
title: Доступ к функциональным возможностям SQLXML в среде .NET | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- Managed Classes [SQLXML], accessing SQLXML functionality
- SQLXML Managed Classes, accessing SQLXML functionality
- DiffGrams [SQLXML], accessing SQLXML functionality
- .NET Framework [SQLXML], accessing SQLXML functionality
ms.assetid: 74744535-2945-414d-9a5b-7e8cc363953a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5d4055c52f8d7a9401bf3c9b89754db831d94bb3
ms.sourcegitcommit: 45a9d7ffc99502c73f08cb937cbe9e89d9412397
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/22/2019
ms.locfileid: "66012568"
---
# <a name="accessing-sqlxml-functionality-in-the-net-environment"></a>Доступ к функциональным возможностям SQLXML в среде .NET
  В этом примере показано следующее.  
  
-   Как использовать [!INCLUDE[msCoName](../../../includes/msconame-md.md)] управляемых классов SQLXML (Microsoft.Data.SqlXml) для доступа к Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в [!INCLUDE[msCoName](../../../includes/msconame-md.md)] среды .NET Framework.  
  
-   Как дельты, сформированные в среде .NET Framework, могут применять изменения данных к таблицам [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 В этом приложении запрос XPath выполняется применительно к схеме XSD. Запрос XPath возвращает XML-документ, содержащий данные контактов (**FirstName**, **LastName**). Приложение загружает XML-документ в набор данных в среде .NET Framework. Данные в наборе данных изменяются: имя первого контакта в наборе данных меняется на «Сьюзен». Из набора данных создается дельта, и обновление, заданное в дельте (изменение имени сотрудника), применяется к таблице Person.Contact.  
  
> [!NOTE]  
>  В коде необходимо задать имя экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в строке соединения.  
  
```  
using System;  
using System.Data;  
using Microsoft.Data.SqlXml;  
using System.IO;  
class Test  
{  
   static string ConnString = "Provider=SQLOLEDB;Server=SqlServerName;database=AdventureWorks;Integrated Security=SSPI;";  
   public static int testParams()  
   {  
      DataRow row;  
      SqlXmlAdapter ad;  
      //need a memory stream to hold diff gram temporarily  
      MemoryStream ms = new MemoryStream();  
      SqlXmlCommand cmd = new SqlXmlCommand(ConnString);  
      cmd.RootTag = "ROOT";  
      cmd.CommandText = "Con";  
      cmd.CommandType = SqlXmlCommandType.XPath;  
      cmd.SchemaPath = "MySchema.xml";  
      //load data set  
      DataSet ds = new DataSet();  
      ad = new SqlXmlAdapter(cmd);  
      ad.Fill(ds);  
      row = ds.Tables["Con"].Rows[0];  
      row["FName"] = "Susan";  
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
  
 **Чтобы протестировать пример:**  
  
 Чтобы проверить этот пример, необходимо установить на компьютер платформу [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework.  
  
1.  Сохраните эту схему XSD (MySchema.xml) в папке.  
  
    ```  
    <xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
                xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
      <xsd:element name="Con" sql:relation="Person.Contact" >  
       <xsd:complexType>  
         <xsd:sequence>  
            <xsd:element name="FName"    
                         sql:field="FirstName"   
                         type="xsd:string" />   
            <xsd:element name="LName"    
                         sql:field="LastName"    
                         type="xsd:string" />  
         </xsd:sequence>  
         <xsd:attribute name="ContactID" type="xsd:integer" />  
        </xsd:complexType>  
      </xsd:element>  
    </xsd:schema>  
    ```  
  
2.  Сохраните код на языке C# (файл DocSample.cs), приведенный в этом примере, в той папке, где хранится схема (если сохранить файлы в разных папках, то придется изменить код, указав путь к каталогу, в котором находится схема сопоставления).  
  
3.  Скомпилируйте код. Чтобы скомпилировать код из командной строки, введите следующую команду.  
  
    ```  
    csc /reference:Microsoft.Data.SqlXML.dll DocSample.cs  
    ```  
  
     Будет создан исполняемый файл (DocSample.exe).  
  
 Запустите файл DocSample.exe из командной строки.  
  
  
