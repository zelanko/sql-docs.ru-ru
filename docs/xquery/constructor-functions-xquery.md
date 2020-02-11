---
title: Функции-конструкторы (XQuery) | Документация Майкрософт
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- constructor functions [XQuery]
ms.assetid: 98562d0e-d0e0-4f62-b001-90acbac67277
author: rothja
ms.author: jroth
ms.openlocfilehash: 7f64c9ff6664410983d9c3ce7ebdbf07e493ca03
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68038992"
---
# <a name="constructor-functions-xquery"></a>Функции-конструкторы (XQuery)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Функции-конструкторы по указанным входным данным создают экземпляры любых встроенных атомарных типов XSD или пользовательских атомарных типов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
TYP($atomicvalue as xdt:anyAtomicType?  
  
) as TYP?  
  
```  
  
## <a name="arguments"></a>Аргументы  
 *$strval*  
 Строка, которая будет преобразована.  
  
 *Тип*  
 Любой встроенный тип XSD.  
  
## <a name="remarks"></a>Remarks  
 Конструкторы поддерживаются и базовыми, и производными атомарными типами XSD. Однако подтипы **xs: Duration**, включающие **xdt: еармонсдуратион и xdt: dayTimeDuration**, и **xs: QName**, **xs: NMTOKEN**и **xs: Notation** , не поддерживаются. Пользовательские атомарные типы, доступные в ассоциированных коллекциях схем, также доступны, если они прямо или косвенно произведены от следующих типов.  
  
#### <a name="supported-base-types"></a>Поддерживаемые базовые типы  
 Функции-конструкторы поддерживаются следующими базовыми типами:  
  
-   xs:string  
  
-   xs:boolean  
  
-   xs:decimal  
  
-   xs:float  
  
-   xs:double  
  
-   xs:duration  
  
-   xs:dateTime  
  
-   xs:time  
  
-   xs:date  
  
-   xs:gYearMonth  
  
-   xs:gYear  
  
-   xs:gMonthDay  
  
-   xs:gDay  
  
-   xs:gMonth  
  
-   xs:hexBinary  
  
-   xs:base64Binary  
  
-   xs:anyURI  
  
#### <a name="supported-derived-types"></a>Поддерживаемые производные типы  
 Функции-конструкторы поддерживаются следующими производными типами:  
  
-   xs:normalizedString  
  
-   xs:token  
  
-   xs:language  
  
-   xs:Name  
  
-   xs:NCName  
  
-   xs:ID  
  
-   xs:IDREF  
  
-   xs:ENTITY  
  
-   xs:integer  
  
-   xs:nonPositiveInteger  
  
-   xs:negativeInteger  
  
-   xs:long  
  
-   xs:int  
  
-   xs:short  
  
-   xs:byte  
  
-   xs:nonNegativeInteger  
  
-   xs:unsignedLong  
  
-   xs:unsignedInt  
  
-   xs:unsignedShort  
  
-   xs:unsignedByte  
  
-   xs:positiveInteger  
  
 Кроме того, SQL Server поддерживает свертывание констант при вызове функций-конструкторов:  
  
-   Если аргумент является строковым литералом, выражение оценивается во время компиляции. Если значение не соответствует ограничениям типа, возвращается статическая ошибка.  
  
-   Если аргумент является литералом другого типа, выражение оценивается во время компиляции. Если значение не соответствует ограничениям типа, возвращается пустая последовательность.  
  
## <a name="examples"></a>Примеры  
 В этом разделе приведены примеры запросов XQuery к экземплярам XML, хранящимся в различных столбцах типа **XML** в базе данных AdventureWorks.  
  
### <a name="a-using-the-datetime-xquery-function-to-retrieve-older-product-descriptions"></a>A. Использование функции dateTime() языка XQuery для получения описаний старой продукции  
 В этом примере образец XML-документа сначала присваивается переменной типа **XML** . Этот документ содержит три примера <`ProductDescription`> элементов, каждый из которых содержит дочерний `DateCreated` элемент <>.  
  
 После этого выполняется запрос переменной, получающей описания только тех продуктов, которые были произведены до указанной даты. В целях сравнения запрос использует функцию конструктора **xs: DateTime ()** для ввода дат.  
  
```  
declare @x xml  
set @x = '<root>  
<ProductDescription ProductID="1" >  
  <DateCreated DateValue="2000-01-01T00:00:00Z" />  
  <Summary>Some Summary description</Summary>  
</ProductDescription>  
<ProductDescription  ProductID="2" >  
  <DateCreated DateValue="2001-01-01T00:00:00Z" />  
  <Summary>Some Summary description</Summary>  
</ProductDescription>  
<ProductDescription ProductID="3" >  
  <DateCreated DateValue="2002-01-01T00:00:00Z" />  
  <Summary>Some Summary description</Summary>  
</ProductDescription>  
</root>'  
  
select @x.query('  
     for $PD in  /root/ProductDescription  
     where xs:dateTime(data( ($PD/DateCreated/@DateValue)[1] )) < xs:dateTime("2001-01-01T00:00:00Z")  
     return  
        element Product  
       {   
        ( attribute ProductID { data($PD/@ProductID ) },  
        attribute DateCreated { data( ($PD/DateCreated/@DateValue)[1] ) } )  
        }  
 ')  
```  
  
 Обратите внимание на следующие данные из предыдущего запроса:  
  
-   ДЛЯ... Структура цикла WHERE используется для получения элемента> \<ProductDescription, удовлетворяющего условию, заданному в предложении WHERE.  
  
-   Функция-конструктор **DateTime ()** используется для создания значений типа **DateTime** , чтобы их можно было сравнивать соответствующим образом.  
  
-   После этого запрос создает итоговый XML-код. Так как при этом создается последовательность атрибутов, при формировании XML-кода используются запятые и скобки.  
  
 Результат:  
  
```  
<Product   
   ProductID="1"   
   DateCreated="2000-01-01T00:00:00Z"/>  
```  
  
## <a name="see-also"></a>См. также:  
 [Создание XML &#40;XQuery&#41;](../xquery/xml-construction-xquery.md)   
 [Функции XQuery для типа данных xml](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
