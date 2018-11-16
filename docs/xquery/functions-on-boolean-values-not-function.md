---
title: Функция (XQuery) | Документация Майкрософт
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
manager: craigg
ms.openlocfilehash: 5a39312142a2d81761320c1e5f75cefe2a85b9d7
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/15/2018
ms.locfileid: "51673493"
---
# <a name="functions-on-boolean-values---not-function"></a>Функции с логическими значениями — функция not 
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Возвращает значение TRUE, если действительное логическое значение *$arg* значение false, а значение FALSE, если действительное логическое значение *$arg* имеет значение true.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
fn:not($arg as item()*) as xs:boolean  
```  
  
## <a name="arguments"></a>Аргументы  
 *$arg*  
 Последовательность элементов, которым соответствует действительное логическое значение.  
  
## <a name="examples"></a>Примеры  
 В этом разделе приведены примеры запросов XQuery к экземплярам XML, которые хранятся в различных **xml** -столбец базы данных AdventureWorks.  
  
### <a name="a-using-the-not-xquery-function-to-find-product-models-whose-catalog-descriptions-do-not-include-the-specifications-element"></a>A. Использование функции not() XQuery для поиска моделей продуктов, описания которых в каталоге не включают \<спецификации > элемента.  
 В результате выполнения приведенного ниже запроса создается XML-документ, содержащий идентификаторы моделей продуктов, не содержащие элемент <`Specifications`>.  
  
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
  
-   Так как в документе используются пространства имен, то в образце применяется инструкция WITH NAMESPACES. Другой вариант — использовать **объявить пространство имен** ключевое слово в [прологе XQuery](../xquery/modules-and-prologs-xquery-prolog.md) для определения префикса.  
  
-   Запрос создает XML, который включает <`Product`> элемент и его **ProductModelID** атрибута.  
  
-   Предложение WHERE использует [метод exist() (тип данных XML)](../t-sql/xml/exist-method-xml-data-type.md) для фильтрации строк. **Exist()** метод возвращает значение True, если \<ProductDescription > элементов, у которых нет \<спецификации > дочерних элементов. Обратите внимание на использование **not()** функции.  
  
 Этот результирующий набор пуст, так как каждый описания каталога моделей продуктов включает \<спецификации > элемента.  
  
### <a name="b-using-the-not-xquery-function-to-retrieve-work-center-locations-that-do-not-have-a-machinehours-attribute"></a>Б. Использование функции XQuery not() для получения информации о расположении цехов, не имеющих атрибута «MachineHours»  
 Следующий запрос адресован столбцу «Инструкции». В указанном столбце хранятся производственные инструкции для моделей продуктов.  
  
 Для любой модели продукта запрос извлекает информацию о расположении цехов, для которых не задан атрибут "MachineHours". То есть атрибут **MachineHours** не указано для \<расположение > элемента.  
  
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
  
-   **Declarenamespace** в [прологе XQuery](../xquery/modules-and-prologs-xquery-prolog.md) определяет Adventure Works, производственные инструкции префикс пространства имен. Здесь представлено пространство имен, используемое в документе производственных инструкций.  
  
-   В запросе **не (@MachineHours)** предикат возвращает значение True, если не **MachineHours** атрибута.  
  
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
  
-   **Not()** функция поддерживает только аргументы типа xs: Boolean, node() * или пустую последовательность.  
  
## <a name="see-also"></a>См. также  
 [Функции XQuery для типа данных XML](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
