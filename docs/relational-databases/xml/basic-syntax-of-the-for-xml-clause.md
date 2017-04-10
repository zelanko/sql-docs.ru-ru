---
title: "Базовый синтаксис предложения FOR XML | Microsoft Docs"
ms.custom: ""
ms.date: "03/06/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-xml"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "BINARY BASE64, директива"
  - "ROOT, директива"
  - "предложение FOR XML, директива BINARY BASE64"
  - "предложение FOR XML, синтаксис"
  - "предложение FOR XML, директива ROOT"
ms.assetid: df19ecbf-d28e-4e9c-aaa3-700f8bbd3be4
caps.latest.revision: 38
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 38
---
# Базовый синтаксис предложения FOR XML
  Режимом предложения FOR XML может быть RAW, AUTO, EXPLICIT или PATH. Он определяет форму получаемого в результате XML-документа.  
  
> [!IMPORTANT]  
>  Директива XMLDATA для параметра XML FOR является устаревшей. В режимах RAW и AUTO следует использовать создание XSD-схем. В режиме EXPLICT для директивы XMLDATA замены нет. [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 Далее приводится базовый синтаксис, описанный в [предложении FOR (Transact-SQL)](../Topic/FOR%20Clause%20\(Transact-SQL\).md):  
  
```  
[ FOR { BROWSE | <XML> } ]  
<XML> ::=  
XML   
    {   
      { RAW [ ('ElementName') ] | AUTO }   
        [   
           <CommonDirectives>   
           [ , { XMLDATA | XMLSCHEMA [ ('TargetNameSpaceURI') ]} ]   
           [ , ELEMENTS [ XSINIL | ABSENT ]   
        ]  
      | EXPLICIT   
        [   
           <CommonDirectives>   
           [ , XMLDATA ]   
        ]  
      | PATH [ ('ElementName') ]   
        [   
           <CommonDirectives>   
           [ , ELEMENTS [ XSINIL | ABSENT ] ]  
        ]  
     }   
  
 <CommonDirectives> ::=   
   [ , BINARY BASE64 ]  
   [ , TYPE ]  
   [ , ROOT [ ('RootName') ] ]  
```  
  
## Аргументы  
 RAW[('*ElementName*')]  
 Берет результаты запроса и преобразует каждую строку в результирующем наборе в элемент XML с универсальным идентификатором \<row /> в качестве тега элемента. При использовании этой директивы можно дополнительно указать имя для элемента строки. Полученный в результате XML-документ будет использовать указанное имя *ElementName* в качестве элемента, сформированного для каждой строки. Дополнительные сведения см. в статье [Использование с RAW Mode для FOR XML](../../relational-databases/xml/use-raw-mode-with-for-xml.md).  
  
 AUTO  
 Возвращает результаты запроса в виде простого вложенного дерева XML. Каждая таблица в предложении FROM, в которой хотя бы один столбец перечислен в предложении SELECT, представлена в виде элемента XML. Столбцы, перечисленные в предложении SELECT, сопоставлены с соответствующими атрибутами элемента. Дополнительные сведения см. в статье [Использование с AUTO Mode для FOR XML](../../relational-databases/xml/use-auto-mode-with-for-xml.md).  
  
 EXPLICIT  
 Указывает, что форма конечного дерева XML определена явно. В этом режиме запросы должны быть составлены особым образом, при котором необходимые данные о вложенности определяются явно. Дополнительные сведения см. в статье [Использование с EXPLICIT Mode для FOR XML](../../relational-databases/xml/use-explicit-mode-with-for-xml.md).  
  
 PATH  
 Предоставляет более простой способ смешивания элементов и атрибутов, а также введения дополнительной вложенности для представления сложных свойств. Чтобы создать такой тип XML из набора строк, можно использовать запросы режима FOR XML EXPLICIT, однако режим PATH представляет собой более простую альтернативу потенциально громоздким запросам режима EXPLICIT. Режим PATH дополнительно к возможности записи вложенных запросов FOR XML и возвращения экземпляров типа **xml** с помощью директивы TYPE позволяет писать менее сложные запросы. Он является альтернативой написанию большинства запросов в режиме EXPLICIT. По умолчанию режим PATH формирует упаковщик элемента \<row> для каждой строки в результирующем наборе. Также можно указать имя элемента. Если имя указывается, оно используется в качестве имени упаковщика элемента. При предоставлении пустой строки (FOR XML PATH ('')) упаковщик элемента не формируется. Дополнительные сведения см. в статье [Использование с PATH Mode для FOR XML](../../relational-databases/xml/use-path-mode-with-for-xml.md).  
  
 XMLDATA  
 Указывает, что будет возвращена встроенная XDR-схема. Эта схема присоединяется к документу в качестве встроенной схемы. Работающий пример см. в статье [Использование с RAW Mode для FOR XML](../../relational-databases/xml/use-raw-mode-with-for-xml.md).  
  
 XMLSCHEMA  
 Возвращает встроенную XML-схему W3C (XSD). Также при определении этой директивы можно указать целевой URI пространства имен. При этом в схему возвращается указанное пространство имен. Дополнительные сведения см. в разделе [Создание встроенных схем XSD](../../relational-databases/xml/generate-an-inline-xsd-schema.md). Работающий пример см. в статье [Использование с RAW Mode для FOR XML](../../relational-databases/xml/use-raw-mode-with-for-xml.md).  
  
 ELEMENTS  
 Если указан параметр ELEMENTS, столбцы возвращаются в виде вложенных элементов. В противном случае они сопоставляются с XML-атрибутами. Этот параметр поддерживается только режимами RAW, AUTO и PATH. Пи использовании этой директивы можно дополнительно указать ключевые слова XSINIL или ABSENT. Ключевое слово XSINIL указывает на то, что элемент имеет атрибут **xsi:nil** , установленный в значение True для столбцов со значением NULL. По умолчанию или при указании вместе с параметром ELEMENTS ключевого слова ABSENT, для значений NULL столбцы не создаются. Работающий пример см. в статьях [Использование с RAW Mode для FOR XML](../../relational-databases/xml/use-raw-mode-with-for-xml.md) и [Использование режима AUTO совместно с FOR XML](../../relational-databases/xml/use-auto-mode-with-for-xml.md).  
  
 BINARY BASE64  
 Если указан параметр BINARY Base64, любые двоичные данные, возвращенные запросом, будут представлены в формате base64. Чтобы получить двоичные данные при помощи режимов RAW и EXPLICIT, необходимо указать этот параметр. В режиме AUTO двоичные данные возвращаются по умолчанию. Работающий пример см. в статье [Использование с RAW Mode для FOR XML](../../relational-databases/xml/use-raw-mode-with-for-xml.md).  
  
 TYPE  
 Указывает на то, что запрос возвращает результаты в виде типа **xml**. Дополнительные сведения см. в статье [TYPE Directive in FOR XML Queries](../../relational-databases/xml/type-directive-in-for-xml-queries.md).  
  
 ROOT [('*RootName*')]  
 Указывает, что к результирующему XML-документу будет добавлен один элемент верхнего уровня. Дополнительно можно указать имя корневого элемента, который необходимо сформировать. Значение по умолчанию — «root».  
  
## См. также:  
 [Использование с RAW Mode для FOR XML](../../relational-databases/xml/use-raw-mode-with-for-xml.md)   
 [Использование режима AUTO совместно с FOR XML](../../relational-databases/xml/use-auto-mode-with-for-xml.md)   
 [Использование режима EXPLICIT совместно с предложением FOR XML](../../relational-databases/xml/use-explicit-mode-with-for-xml.md)   
 [Использование режима PATH совместно с FOR XML](../../relational-databases/xml/use-path-mode-with-for-xml.md)   
 [SELECT (Transact-SQL)](../../t-sql/queries/select-transact-sql.md)   
 [FOR XML (SQL Server)](../../relational-databases/xml/for-xml-sql-server.md)  
  
  