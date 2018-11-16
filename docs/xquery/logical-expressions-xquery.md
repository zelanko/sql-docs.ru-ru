---
title: Логические выражения (XQuery) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- logical operators [SQL Server], XQuery
- effective Boolean value [XQuery]
- logical expressions [XQuery]
- EBV
- expressions [XQuery], logical
ms.assetid: de94cd2e-2d48-49fb-9ebd-a2d90c79bf62
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: fd6417c10be286164b9d56a0c2587dfd63a1de23
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/15/2018
ms.locfileid: "51670342"
---
# <a name="logical-expressions-xquery"></a>Логические выражения (XQuery)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  XQuery поддерживает логические **и** и **или** операторы.  
  
```  
expression1 and expression2  
expression1 or expression2  
```  
  
 Результатом тестовых выражений `expression1,``expression2`в [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] может привести к пустой последовательности, последовательность одного или нескольких узлов или одиночное логическое значение. Основанное на результате действительное логическое значение определяется следующим способом:  
  
-   если результатом тестовых выражений является пустая последовательность, результатом выражения является значение False;  
  
-   если результатом тестовых выражений является одиночное логическое значение, это значение и будет являться результатом выражения;  
  
-   если результатом тестовых выражений является последовательность одного или нескольких узлов, результатом выражения является значение True;  
  
-   иначе возникает статическая ошибка.  
  
 Логический **и** и **или** оператор применяется к итоговый логическим значениям выражений со стандартной логической семантикой.  
  
 Следующий запрос получает из каталога продуктов маленькие фронтальные картинки (элемент <`Picture`>) для указанной модели продукции. Обратите внимание, что для каждого документа с описанием продукта каталог может хранить одно или несколько изображений продукта с различными атрибутами, такими как размер и угол.  
  
```  
SELECT CatalogDescription.query('  
     declare namespace PD="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
     for $F in /PD:ProductDescription/PD:Picture[PD:Size="small"   
                                                 and PD:Angle="front"]  
     return   
         $F   
    ') as Result  
FROM  Production.ProductModel  
where ProductModelID=19  
```  
  
 Результат:  
  
```  
<PD:Picture   
  xmlns:PD="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription">  
  <PD:Angle>front</PD:Angle>  
  <PD:Size>small</PD:Size>  
  <PD:ProductPhotoID>31</PD:ProductPhotoID>  
</PD:Picture>  
  
```  
  
## <a name="see-also"></a>См. также  
 [Выражения XQuery](../xquery/xquery-expressions.md)  
  
  
