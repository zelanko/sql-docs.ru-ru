---
title: Проверка XML с использованием задачи "XML" | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- XML validation
- XML, validating
ms.assetid: 224fc025-c21f-4d43-aa9d-5ffac337f9b0
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 8ea74ad195b97541147c3d1b19dc01c5033b962c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37182832"
---
# <a name="validate-xml-with-the-xml-task"></a>Validate XML with the XML Task
  Проверка XML-документов и настроить вывод подробных сведений об ошибках, включив `ValidationDetails` свойства задачи «XML».  
  
 На следующем снимке экрана показано окно **редактора задачи XML** с необходимыми параметрами для проверки XML, позволяющими настроить вывод подробных сведений об ошибках.  
  
 ![Свойства задачи "XML" в редакторе задачи "XML"](../media/xmltaskproperties.jpg "Свойства задачи \"XML\" в редакторе задачи \"XML\"")  
  
 Прежде чем `ValidationDetails` был предусмотрен, проверка XML в задачах XML возвращаются только true или false, без сведений об ошибках и их расположении. Теперь, если для свойства `ValidationDetails` в значение true, выходной файл содержит подробные сведения обо всех ошибках, включая номер строки и позиции. Эти сведения можно использовать для анализа, поиска и исправления ошибок в XML-документах.  
  
 Функция проверки XML легко масштабируется в соответствии с размером XML-документов и количеством ошибок. Так как выходной файл имеет формат XML, можно запрашивать и анализировать содержащиеся в нем данные. Например, если выходные данные содержат большое количество ошибок, их можно сгруппировать, используя запрос [!INCLUDE[tsql](../../../includes/tsql-md.md)] , как описано в этом разделе.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ([!INCLUDE[ssIS](../../includes/ssis-md.md)]) появился `ValidationDetails` свойство в [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] с пакетом обновления 2. Свойство также доступно в [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] и в SQL Server 2016.  
  
## <a name="sample-output-for-xml-thats-valid"></a>Пример выходных данных в допустимом XML-файле  
 Ниже приведен пример допустимого выходного XML-файла с результатами проверки.  
  
```xml  
  
<root xmlns:ns="http://schemas.microsoft.com/xmltools/2002/xmlvalidation">  
    <metadata>  
        <result>true</result>  
        <errors>0</errors>  
        <warnings>0</warnings>  
        <startTime>2015-05-28T10:27:22.087</startTime>  
        <endTime>2015-05-28T10:29:07.007</endTime>  
        <xmlFile>d:\Temp\TestData.xml</xmlFile>  
        <xsdFile>d:\Temp\TestSchema.xsd</xsdFile>  
    </metadata>  
    <messages />  
</root>  
```  
  
## <a name="sample-output-for-xml-thats-not-valid"></a>Пример выходных данных в недопустимом XML-файле  
 Ниже приведен пример выходного XML-файла с результатами проверки, который содержит небольшое количество ошибок. Текст элементов \<error> скрыт для удобства чтения.  
  
```xml  
  
<root xmlns:ns="http://schemas.microsoft.com/xmltools/2002/xmlvalidation">  
    <metadata>  
        <result>false</result>  
        <errors>2</errors>  
        <warnings>0</warnings>  
        <startTime>2015-05-28T10:45:09.538</startTime>  
        <endTime>2015-05-28T10:45:09.558</endTime>  
        <xmlFile>C:\Temp\TestData.xml</xmlFile>  
        <xsdFile>C:\Temp\TestSchema.xsd</xsdFile>  
    </metadata>  
    <messages>  
        <error line="5" position="26">The 'ApplicantRole' element is invalid - The value 'wer3' is invalid  
    according to its datatype 'ApplicantRoleType' - The Enumeration constraint failed.</error>  
        <error line="16" position="28">The 'Phone' element is invalid - The value 'we3056666666' is invalid  
     according to its datatype 'phone' - The Pattern constraint failed.</error>  
    </messages>  
</root>  
```  
  
## <a name="analyze-xml-validation-output-with-a-transact-sql-query"></a>Анализ выходных данных проверки XML с помощью запроса Transact-SQL  
 Если результат проверки XML содержит большое количество ошибок, можно использовать запрос [!INCLUDE[tsql](../../../includes/tsql-md.md)] , чтобы загрузить выходные данные в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Затем можно проанализировать список ошибок, используя все возможности языка T-SQL, включая предложения WHERE, GROUP BY, ORDER BY, JOIN и т. д.  
  
```tsql  
DECLARE @xml XML;  
  
SELECT @xml = XmlDoc     
FROM OPENROWSET (BULK N'C:\Temp\XMLValidation_2016-02-212T10-41-00.xml', SINGLE_BLOB) AS Tab(XmlDoc);  
  
-- Query # 1, flat list of errors  
-- convert to relational/rectangular  
;WITH XMLNAMESPACES ('http://schemas.microsoft.com/xmltools/2002/xmlvalidation' AS ns), rs AS  
(  
SELECT col.value('@line','INT') AS line  
     , col.value('@position','INT') AS position  
     , col.value('.','VARCHAR(1024)') AS error  
FROM @XML.nodes('/root/messages/error') AS tab(col)  
)  
SELECT * FROM rs;  
-- WHERE error LIKE ‘%whatever_string%’  
  
-- Query # 2, count of errors grouped by the error message  
-- convert to relational/rectangular  
;WITH XMLNAMESPACES ('http://schemas.microsoft.com/xmltools/2002/xmlvalidation' AS ns), rs AS  
(  
SELECT col.value('@line','INT') AS line  
     , col.value('@position','INT') AS position  
     , col.value('.','VARCHAR(1024)') AS error  
FROM @XML.nodes('/root/messages/error') AS tab(col)  
)  
SELECT COALESCE(error,'Total # of errors:') AS [error], COUNT(*) AS [counter]  
FROM rs  
GROUP BY GROUPING SETS ((error), ())  
ORDER BY 2 DESC, COALESCE(error, 'Z');  
  
```  
  
 Ниже приведен результат запроса к [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] из второго примера, показанного выше.  
  
 ![Запрос на группирование ошибок XML в Management Studio](../media/queryforxmlerrors.jpg "Запрос на группирование ошибок XML в Management Studio")  
  
## <a name="see-also"></a>См. также  
 [Задача «XML»](xml-task.md)   
 [Редактор задачи XML &#40;страница "Общие"&#41;](../xml-task-editor-general-page.md)  
  
  
