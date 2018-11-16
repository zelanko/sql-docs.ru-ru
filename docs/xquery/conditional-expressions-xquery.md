---
title: Условные выражения (XQuery) | Документация Майкрософт
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- XQuery, conditional expressions
- expressions [XQuery], conditional
- effective Boolean value [XQuery]
- if-then-else statement [XQuery]
- conditional expressions [XQuery]
- EBV
ms.assetid: b280dd96-c80f-4c51-bc06-a88d42174acb
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 3164d17169e0a90416c8131825c3d61b1ff5fe16
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/15/2018
ms.locfileid: "51677593"
---
# <a name="conditional-expressions-xquery"></a>Выражения условий (XQuery)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  XQuery поддерживает следующий условный **if-then-else** инструкции:  
  
```  
if (<expression1>)  
then  
  <expression2>  
else  
  <expression3>  
```  
  
 В зависимости от действительного логического значения вычисляется выражение `expression1`, `expression2` или `expression3`. Пример:  
  
-   Если выражение условия `expression1` соответствует пустой последовательности, результат имеет значение False.  
  
-   Если выражение `expression1` соответствует простому логическому значению, оно и является результатом выражения.  
  
-   Если выражение `expression1` соответствует последовательности из одного или более узлов, результатом выражения является значение True.  
  
-   иначе возникает статическая ошибка.  
  
 Имейте в виду следующее.  
  
-   Выражение условия должно быть заключено в скобки.  
  
-   **Else** выражение является обязательным. Если оно не требуется, можно возвратить « ( ) », как показано в примерах, приведенных в этом подразделе.  
  
 Например, следующий запрос адресован **xml** переменной типа. **Если** проверяется значение SQL-переменной (@v) внутри выражения XQuery с помощью [функции SQL: variable()](../xquery/xquery-extension-functions-sql-variable.md) функцию расширения. Если оно равно «FirstName», возвращается элемент <`FirstName`>. В противном случае возвращается элемент <`LastName`>.  
  
```  
declare @x xml  
declare @v varchar(20)  
set @v='FirstName'  
set @x='  
<ROOT rootID="2">  
  <FirstName>fname</FirstName>  
  <LastName>lname</LastName>  
</ROOT>'  
SELECT @x.query('  
if ( sql:variable("@v")="FirstName" ) then  
  /ROOT/FirstName  
 else  
   /ROOT/LastName  
')  
```  
  
 Результат:  
  
```  
<FirstName>fname</FirstName>  
```  
  
 Следующий запрос получает описания первых двух характеристик конкретной модели продукции из каталога товаров. Если в документе описано большее число характеристик, в результат добавляется пустой элемент <`there-is-more`>.  
  
```  
SELECT CatalogDescription.query('  
     declare namespace p1="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
     <Product>   
          { /p1:ProductDescription/@ProductModelID }  
          { /p1:ProductDescription/@ProductModelName }   
          {  
            for $f in /p1:ProductDescription/p1:Features/*[position()\<=2]  
            return  
            $f   
          }  
          {  
            if (count(/p1:ProductDescription/p1:Features/*) > 2)  
            then \<there-is-more/>  
            else ()  
          }   
     </Product>          
') as x  
FROM Production.ProductModel  
WHERE ProductModelID = 19  
```  
  
 В предыдущем запросе, то условие в **Если** выражение проверяет наличие более двух дочерних элементов в <`Features`>. Если да, в результат запроса включается элемент `\<there-is-more/>`.  
  
 Результат:  
  
```  
<Product ProductModelID="19" ProductModelName="Mountain 100">  
  \<p1:Warranty xmlns:p1="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain">  
    \<p1:WarrantyPeriod>3 years\</p1:WarrantyPeriod>  
    \<p1:Description>parts and labor\</p1:Description>  
  \</p1:Warranty>  
  \<p2:Maintenance xmlns:p2="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain">  
    \<p2:NoOfYears>10 years\</p2:NoOfYears>  
    \<p2:Description>maintenance contract available through your dealer or any AdventureWorks retail store.\</p2:Description>  
  \</p2:Maintenance>  
  \<there-is-more />  
</Product>  
```  
  
 Следующий запрос возвращает элемент <`Location`> с атрибутом LocationID, если для цеха не задано рабочее время.  
  
```  
SELECT Instructions.query('  
     declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
        for $WC in //AWMI:root/AWMI:Location  
        return  
        if ( $WC[not(@SetupHours)] )  
        then  
          <WorkCenterLocation>  
             { $WC/@LocationID }   
          </WorkCenterLocation>  
         else  
           ()  
') as Result  
FROM Production.ProductModel  
where ProductModelID=7  
```  
  
 Результат:  
  
```  
<WorkCenterLocation LocationID="30" />  
<WorkCenterLocation LocationID="45" />  
<WorkCenterLocation LocationID="60" />  
```  
  
 Этот запрос может быть записан без **Если** предложения, как показано в следующем примере:  
  
```  
SELECT Instructions.query('  
     declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
for $WC in //AWMI:root/AWMI:Location[not(@SetupHours)]   
        return  
          <Location>  
             { $WC/@LocationID }   
          </Location>  
') as Result  
FROM Production.ProductModel  
where ProductModelID=7  
```  
  
## <a name="see-also"></a>См. также  
 [Выражения XQuery](../xquery/xquery-expressions.md)  
  
  
