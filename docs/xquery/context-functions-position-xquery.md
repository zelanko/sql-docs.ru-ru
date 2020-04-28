---
title: Функция позиционирования (XQuery) | Документация Майкрософт
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
- position function
- fn:position function
ms.assetid: f1bab9e4-1715-4c06-9cb0-06c7e0c9c97f
author: rothja
ms.author: jroth
ms.openlocfilehash: de9f30c3c63030aa956366c222b7cbda94e2becb
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68038978"
---
# <a name="context-functions---position-xquery"></a>Функции контекста — position (XQuery)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает целочисленное значение, указывающее позицию контекстного элемента в последовательности обрабатываемых в данный момент элементов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
fn:position() as xs:integer  
```  
  
## <a name="remarks"></a>Remarks  
 В [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]функция **fn: положением ()** может использоваться только в контексте зависимого от контекста предиката. Конкретно ее можно использовать только внутри квадратных скобок ([]). Сравнение с данной функцией не приводит к снижению количества элементов в процессе статического определения типов.  
  
## <a name="examples"></a>Примеры  
 В этом разделе приведены примеры запросов XQuery к экземплярам XML, хранящимся в различных столбцах [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] типа **XML** в базе данных.  
  
### <a name="a-using-the-position-xquery-function-to-retrieve-the-first-two-product-features"></a>А) Использование функции position() в запросе XQuery для получения первых двух характеристик продукта  
 Следующий запрос получает первые две функции — первые два дочерних элемента <`Features`> элемента из описания каталога модели продукта. При наличии дополнительных функций он добавляет к результату элемент `there-is-more/`> <.  
  
```  
SELECT CatalogDescription.query('  
     declare namespace pd="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
     <Product>   
          { /pd:ProductDescription/@ProductModelID }  
          { /pd:ProductDescription/@ProductModelName }   
          {  
            for $f in /pd:ProductDescription/pd:Features/*[position()<=2]  
            return  
            $f   
          }  
          {  
            if (count(/pd:ProductDescription/pd:Features/*) > 2)  
            then <there-is-more/>  
            else ()  
          }   
     </Product>          
') as x  
FROM Production.ProductModel  
WHERE CatalogDescription is not null  
```  
  
 Обратите внимание на следующие данные из предыдущего запроса:  
  
-   Ключевое слово **Namespace** в [прологе XQuery](../xquery/modules-and-prologs-xquery-prolog.md) определяет префикс пространства имен, используемый в теле запроса.  
  
-   Текст запроса конструирует XML, который содержит элемент> \<продукта с атрибутами **ProductModelID** и **ProductModelName** и содержит функции продукта, возвращаемые как дочерние элементы.  
  
-   Функция **позиционирования ()** используется в предикате для определения расположения \<компонентов> дочернего элемента в контексте. Если он является первой или второй функцией, он возвращается.  
  
-   Инструкция IF добавляет \<к результату элемент-more/>, если в каталоге продуктов содержится более двух компонентов.  
  
-   Так как не для всех моделей продуктов их описание из каталога хранится в таблице, используется предложение WHERE для отсева строк, для которых значение CatalogDescriptions равно NULL.  
  
 Частичный результат:  
  
```  
<Product ProductModelID="19" ProductModelName="Mountain 100">  
  <p1:Warranty xmlns:p1="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain">  
    <p1:WarrantyPeriod>3 year</p1:WarrantyPeriod>  
    <p1:Description>parts and labor</p1:Description>  
  </p1:Warranty>  
  <p2:Maintenance xmlns:p2="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain">  
    <p2:NoOfYears>10</p2:NoOfYears>  
    <p2:Description>maintenance contact available through your dealer or  
                    any AdventureWorks retail store.</p2:Description>  
  </p2:Maintenance>  
  <there-is-more/>  
</Product>   
...  
```  
  
## <a name="see-also"></a>См. также:  
 [Функции XQuery для типа данных xml](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
