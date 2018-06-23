---
title: Выполнение файлов шаблонов через свойство CommandStream | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Managed Classes [SQLXML], executing template files
- SQLXML Managed Classes, executing template files
- templates [SQLXML], SQLXML Managed Classes
- CommandStream property
ms.assetid: 55c564e3-56d1-4d85-bcaa-703e2905dd57
caps.latest.revision: 21
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: fd2f29f14d4af758581e368986398720dd3b5a0b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36110119"
---
# <a name="executing-template-files-by-using-the-commandstream-property"></a>Выполнение файлов шаблонов через свойство CommandStream
  В этом примере показано, как можно указать файлы шаблонов, состоящие из запросов SQL или XPath, используя свойство CommandStream SqlXmlCommand, объект. В этом приложении FileStreamobject открывается для командного файла и файловый поток устанавливается как CommandStream, который выполняется.  
  
 В следующем примере Если свойство CommandType задается как SqlXmlCommandType.Template (не как TemplateFile).  
  
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
  
  