---
title: Синтаксис запроса XML для XML-данных отчета (службы SSRS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- namespaces [Reporting Services]
- data processing extensions [Reporting Services], data sources
- xmldp [Reporting Services]
- XML [Reporting Services], data retrieval
ms.assetid: d203886f-faa1-4a02-88f5-dd4c217181ef
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f5f8840e0204847d447ea794e94312221ec1cc72
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/28/2020
ms.locfileid: "80380795"
---
# <a name="xml-query-syntax-for-xml-report-data-ssrs"></a>Синтаксис запроса XML для XML-данных отчета (SSRS)
  В службах [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]можно создавать наборы данных для источников XML-данных. После определения источника данных можно создать запрос для получения набора данных. В зависимости от типа XML-данных, на которые указывает источник данных, этот запрос создается путем включения либо элемента XML `Query`, либо пути к элементу. XML `Query` начинается с тега ** \<>запроса** и включает в себя области имен и элементы XML, которые варьируются в зависимости от источника данных. Путь к элементу не зависит от пространства имен и указывает необходимые узлы и атрибуты узлов в базовых XML-данных при помощи XPath-подобного синтаксиса. Дополнительные сведения о путях к элементу см. в разделе [Синтаксис пути к элементу для XML-данных отчета (службы SSRS)](report-data-ssrs.md).  
  
 Источник данных XML можно создать для следующих типов XML-данных:  
  
-   XML-документы, на которые указывает URL-адрес по протоколу HTTP;  
  
-   конечные точки веб-службы, возвращающей XML-данные;  
  
-   встроенные XML-данные.  
  
 Способ указания элемента XML `Query` или пути к элементу зависит от типа XML-данных.  
  
 Для XML-документа элемент XML `Query` необязателен. Если он включен, то может содержать необязательный элемент XML `ElementPath`. В значении элемента XML `ElementPath` используется синтаксис пути к элементу. Элементы XML `Query` и XML `ElementPath` включаются, чтобы обеспечить правильную обработку пространства имен, если это нужно для XML-данных источника данных.  
  
 Для конечной точки веб-службы, на которую указывает URL-адрес строки соединения, элемент XML `Query` определяет метод веб-службы, действие SOAP или и то, и другое. Поставщик XML-данных создает запрос веб-службы, который получает XML-данные для отчета.  
  
> [!NOTE]  
>  Если пространство имен веб-службы содержит символ косой черты (`/)`, включите как метод веб-службы, так и действие SOAP, чтобы модуль обработки XML-данных мог правильно определить пространство имен.  
  
 Для встроенных XML-документов элемент XML `Query` определяет встроенные XML-данные, включает дополнительные пространства имен и содержит необязательный элемент XML `ElementPath`.  
  
## <a name="specifying-query-parameters-for-xml-data"></a>Указание параметров запроса XML-данных  
 Для XML-документов можно указать параметры запроса.  
  
-   Параметры включаются в URL-адрес как стандартные URL-параметры.  
  
-   В случае запросов к веб-службе параметры запросов передаются методу веб-службы. Для определения параметра запроса используется страница **Параметры** диалогового окна **Свойства набора данных** . Дополнительные сведения см. в статье [Диалоговое окно "Свойства набора данных" — "Параметры"](dataset-properties-dialog-box-parameters.md).  
  
### <a name="example"></a>Пример  
 Примеры, представленные в следующей таблице, иллюстрируют получение данных от веб-службы сервера отчетов, из XML-документа, а также встроенных XML-данных.  
  
|Источник данных XML|Пример запроса|  
|---------------------|-------------------|  
|XML-данные веб-службы с помощью метода ListChildren .|`<Query>`<br /><br /> `<Method Name="ListChildren" Namespace="https://schemas.microsoft.com/sqlserver/2005/06/30/reporting/reportingservices" />`<br /><br /> `</Query>`|  
|XML-данные веб-службы при помощи действия SoapAction.|`<Query xmlns=namespace>`<br /><br /> `<SoapAction>http://schemas/microsoft.com/sqlserver/2005/03/23/reporting/reportingservices/ListChildren</SoapAction>`<br /><br /> `</Query>`|  
|XML-документ или внедренные XML-данные, использующие пространства имен.<br /><br /> Элемент запроса, задающий пространства имен для пути к элементу.|`<Query xmlns:es="https://schemas.microsoft.com/StandardSchemas/ExtendedSales">`<br /><br /> `<ElementPath>/Customers/Customer/Orders/Order/es:LineItems/es:LineItem</ElementPath>`<br /><br /> `</Query>`|  
|Встроенный XML-документ.|`<Query>`<br /><br /> `<XmlData>`<br /><br /> `<Customers>`<br /><br /> `<Customer ID="1">Bobby</Customer>`<br /><br /> `</Customers>`<br /><br /> `</XmlData>`<br /><br /> `<ElementPath>Customer {@}</ElementPath>`<br /><br /> `</Query>`|  
|XML-документ, использующий значения по умолчанию.|*No query*.<br /><br /> Путь к элементу определяется на основе самого XML-документа и не зависит от пространства имен.|  
  
> [!NOTE]  
>  Первый пример веб-службы перечисляет содержимое сервера отчетов, применяющего метод <xref:ReportService2006.ReportingService2006.ListChildren%2A> . Для выполнения этого запроса необходимо создать новый источник данных и задать строку подключения: http://localhost/reportserver/reportservice2006.asmx. Метод <xref:ReportService2006.ReportingService2006.ListChildren%2A> имеет два параметра: `Item` и `Recursive`. Для `Item` установите значение по умолчанию `/`, а для параметра `Recursive` — значение `1`.  
  
## <a name="specifying-namespaces"></a>Указание пространств имен  
 Для указания пространств имен, используемых XML-данными из источника данных, используется элемент XML `Query`. Следующий XML-запрос использует пространство имен `sales`. Узлы XML `ElementPath` для элементов `sales:LineItems` и `sales:LineItem` используют пространство имен `sales`.  
  
```  
<Query xmlns:sales=  
"https://schemas.microsoft.com/StandardSchemas/ExtendedSales">  
   <SoapAction>  
      https://schemas.microsoft.com/SalesWebService/ListOrders   
   </SoapAction>  
   <ElementPath>  
      Customers/Customer/Orders/Order/sales:LineItems/sales:LineItem  
   </ElementPath>  
</Query>  
```  
  
 Чтобы указать пространство имен поставщика данных, оставив пространство имен по умолчанию пустым, используется `xmldp`. Это показано в следующем примере.  
  
### <a name="example"></a>Пример  
 В следующих примерах используется XML-документ DPNamespace.xml, который для наглядности приводится после таблицы. В таблице представлены два примера синтаксиса пути XML ElementPath, включающие префиксы пространства имен.  
  
|Элемент XML-запроса|Полученные в результате поля набора данных|  
|-----------------------|-------------------------------------|  
|\<Query/>|Значение A: `https://schemas.microsoft.com/..`.<br /><br /> Значение B: `https://schemas.microsoft.com/..`.<br /><br /> Значение C: `https://schemas.microsoft.com/.`..|  
|\<xmldp:Запрос xmlns:xmldp"https://schemas.microsoft.com/sqlserver/2005/02/reporting/XmlDPQuery" xmlns:ns"https://schemas.microsoft.com/..." ><br /><br /> \<xmldp:ElementPath>{}Root /ns:Element2/Node\</xmldp:ElementPath><br /><br /> \</xmldp: Запрос>|Значение D<br /><br /> Значение E<br /><br /> Значение F|  
  
#### <a name="xml-document-dpnamespacexml"></a>XML-документ: DPNamespace.xml  
 Можно скопировать этот XML-документ и сохранить его по URL-адресу, который конструктор отчетов будет использовать в качестве источника XML-данных, например http://localhost/DPNamespace.xml.  
  
```  
<Root xmlns:ns="https://schemas.microsoft.com/...">  
   <ns:Element1>  
      <Node>Value A</Node>  
      <Node>Value B</Node>  
      <Node>Value C</Node>  
   </ns:Element1>  
   <ns:Element2>  
      <Node>Value D</Node>  
      <Node>Value E</Node>  
      <Node>Value F</Node>  
   </ns:Element2>  
</Root>  
```  
  
## <a name="see-also"></a>См. также  
 [XML Тип соединения &#40;sSRS&#41;](xml-connection-type-ssrs.md)   
 [Учебники по службам Reporting Services (SSRS)](../reporting-services-tutorials-ssrs.md)  
  
  
