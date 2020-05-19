---
title: Запуск файлов шаблонов с помощью свойства CommandStream | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- Managed Classes [SQLXML], executing template files
- SQLXML Managed Classes, executing template files
- templates [SQLXML], SQLXML Managed Classes
- CommandStream property
ms.assetid: 55c564e3-56d1-4d85-bcaa-703e2905dd57
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 0c90839d02bd2cebcf9424e38d35f9595a23d210
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82718039"
---
# <a name="executing-template-files-by-using-the-commandstream-property"></a>Выполнение файлов шаблонов через свойство CommandStream
  В этом примере показано, как можно указать файлы шаблонов, состоящие из запросов SQL или XPath, с помощью свойства CommandStream объекта SqlXmlCommand. В этом приложении открывается Филестреамобжект для командного файла, а файловый поток назначается как выполняемый CommandStream.  
  
 В следующем примере свойство CommandType указано как Склксмлкоммандтипе. Template (не AS TemplateFile).  
  
 Образец XML-шаблона:  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <sql:query>  
    SELECT TOP 2 ContactID, FirstName, LastName   
    FROM   Person.Contact  
    FOR XML AUTO  
  </sql:query>  
</ROOT>  
```  
  
 Образец приложения C#. Чтобы проверить приложение, сохраните шаблон (файл TemplateFile.xml), а затем выполните приложение. Приложение выполняет запрос, указанный в XML-шаблоне, и отображает созданный XML-документ на экране.  
  
> [!NOTE]  
>  В коде необходимо задать имя экземпляра Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в строке соединения.  
  
```  
using System;  
using Microsoft.Data.SqlXml;  
using System.IO;  
  
class Test  
{  
      static string ConnString = "Provider=SQLOLEDB;Server=(local);database=AdventureWorks;Integrated Security=SSPI";  
      public static int testParams()  
      {  
         //Stream strm;  
         MemoryStream ms = new MemoryStream();  
         StreamWriter sw = new StreamWriter(ms);  
         ms.Position = 0;  
         SqlXmlCommand cmd = new SqlXmlCommand(ConnString);  
         cmd.CommandStream = new FileStream("TemplateFile.xml", FileMode.Open, FileAccess.Read);  
         cmd.CommandType = SqlXmlCommandType.Template;  
         using (Stream strm = cmd.ExecuteStream())  
         {  
            using (StreamReader sr = new StreamReader(strm)){  
               Console.WriteLine(sr.ReadToEnd());  
            }  
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
  
1.  Сохраните в папке XML-шаблон (файл TemplateFile.xml), приведенный в этом примере.  
  
2.  Сохраните код на языке C# (файл DocSample.cs), приведенный в этом разделе, в той папке, где сохранена схема (если сохранить файлы в разных папках, то придется изменить код, указав путь к каталогу, в котором находится схема сопоставления).  
  
3.  Скомпилируйте код. Чтобы скомпилировать код из командной строки, введите следующую команду.  
  
    ```  
    csc /reference:Microsoft.Data.SqlXML.dll DocSample.cs  
    ```  
  
     Будет создан исполняемый файл (DocSample.exe).  
  
4.  Запустите файл DocSample.exe из командной строки.  
  
  
