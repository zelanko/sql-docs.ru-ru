---
title: Функция not (XQuery) | Документация Майкрософт
description: Сведения о том, как функция XQuery not () используется с логическими значениями.
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
- effective Boolean value [XQuery]
- fn:not function
- not function [XQuery]
- EBV
ms.assetid: 93dfc377-45f1-4384-9392-560d9331a915
author: rothja
ms.author: jroth
ms.openlocfilehash: 24235099ec742d4c6d62e3d97ee1f551af24f7d4
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/08/2020
ms.locfileid: "84524430"
---
# <a name="functions-on-boolean-values---not-function"></a>Функции с логическими значениями — функция not 
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Возвращает значение TRUE, если действительное логическое значение *$arg* равно false, и возвращает значение false, если действительное логическое значение *$arg* равно true.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
fn:not($arg as item()*) as xs:boolean  
```  
  
## <a name="arguments"></a>Аргументы  
 *$arg*  
 Последовательность элементов, которым соответствует действительное логическое значение.  
  
## <a name="examples"></a>Примеры  
 В этом разделе приведены примеры запросов XQuery к экземплярам XML, хранящимся в различных столбцах типа **XML** в базе данных AdventureWorks.  
  
### <a name="a-using-the-not-xquery-function-to-find-product-models-whose-catalog-descriptions-do-not-include-the-specifications-element"></a>А) Использование функции XQuery not () для поиска моделей продуктов, описания каталогов которых не включают \<Specifications> элемент.  
 Следующий запрос конструирует XML-код, содержащий идентификаторы модели продукта для моделей продукции, описания каталогов которых не включают `Specifications` элемент <>.  
  
```  
WITH XMLNAMESPACES ('https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS pd)  
SELECT ProductModelID, CatalogDescription.query('  
       <Product   
           ProductModelID="{ sql:column("ProductModelID") }"  
        />  
') as Result  
FROM Production.ProductModel  
WHERE CatalogDescription.exist('  
     /pd:ProductDescription[not(pd:Specifications/*)]  '  
     ) = 0  
```  
  
 Обратите внимание на следующие данные из предыдущего запроса:  
  
-   Так как в документе используются пространства имен, то в образце применяется инструкция WITH NAMESPACES. Другой вариант — использовать ключевое слово **declare namespace** в [прологе XQuery](../xquery/modules-and-prologs-xquery-prolog.md) для определения префикса.  
  
-   Затем запрос конструирует XML, содержащий `Product` элемент <> и его атрибут **ProductModelID** .  
  
-   В предложении WHERE для фильтрации строк используется [метод exist () (тип данных XML)](../t-sql/xml/exist-method-xml-data-type.md) . Метод **exist ()** возвращает значение true, если имеются \<ProductDescription> элементы, не имеющие \<Specification> дочерних элементов. Обратите внимание на использование функции **NOT ()** .  
  
 Этот результирующий набор пуст, так как каждое описание каталога модели продукции включает \<Specifications> элемент.  
  
### <a name="b-using-the-not-xquery-function-to-retrieve-work-center-locations-that-do-not-have-a-machinehours-attribute"></a>Б. Использование функции XQuery not() для получения информации о расположении цехов, не имеющих атрибута «MachineHours»  
 Следующий запрос адресован столбцу «Инструкции». В указанном столбце хранятся производственные инструкции для моделей продуктов.  
  
 Для любой модели продукта запрос извлекает информацию о расположении цехов, для которых не задан атрибут "MachineHours". То есть атрибут **«MachineHours»** не указан для \<Location> элемента.  
  
```  
SELECT ProductModelID, Instructions.query('  
declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions" ;  
     for $i in /AWMI:root/AWMI:Location[not(@MachineHours)]  
     return  
       <Location LocationID="{ $i/@LocationID }"   
                   LaborHrs="{ $i/@LaborHours }" >  
        </Location>  
') as Result  
FROM Production.ProductModel  
WHERE ProductModelID=7   
```  
  
 В предыдущем запросе отметим следующее.  
  
-   В [прологе](../xquery/modules-and-prologs-xquery-prolog.md) **декларенамеспаце** в XQuery определен префикс пространства имен для производственных инструкций Adventure Works. Здесь представлено пространство имен, используемое в документе производственных инструкций.  
  
-   В запросе предикат **NOT ( @MachineHours )** возвращает значение true, если отсутствует атрибут **«MachineHours»** .  
  
 Результат:  
  
```  
ProductModelID Result   
-------------- --------------------------------------------  
7              <Location LocationID="30" LaborHrs="1"/>  
               <Location LocationID="50" LaborHrs="3"/>  
               <Location LocationID="60" LaborHrs="4"/>  
```  
  
### <a name="implementation-limitations"></a>Ограничения реализации  
 Существуют следующие ограничения:  
  
-   Функция **NOT ()** поддерживает только аргументы типа xs: Boolean или node () * или пустую последовательность.  
  
## <a name="see-also"></a>См. также:  
 [Функции XQuery для типа данных xml](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
