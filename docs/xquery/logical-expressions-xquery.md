---
title: Логические выражения (XQuery) | Документация Майкрософт
description: Сведения о логических выражениях, поддерживаемых в XQuery.
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
ms.openlocfilehash: 62552e4e533126bc1e6b53e78e2b0456557e7f45
ms.sourcegitcommit: 5b7457c9d5302f84cc3baeaedeb515e8e69a8616
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/20/2020
ms.locfileid: "83689018"
---
# <a name="logical-expressions-xquery"></a>Логические выражения (XQuery)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  XQuery поддерживает логические операторы **and** и **or** .  
  
```  
expression1 and expression2  
expression1 or expression2  
```  
  
 Тестовые выражения, `expression1,``expression2` в [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] могут привести к созданию пустой последовательности, последовательности из одного или нескольких узлов или единственного логического значения. Основанное на результате действительное логическое значение определяется следующим способом:  
  
-   если результатом тестовых выражений является пустая последовательность, результатом выражения является значение False;  
  
-   если результатом тестовых выражений является одиночное логическое значение, это значение и будет являться результатом выражения;  
  
-   если результатом тестовых выражений является последовательность одного или нескольких узлов, результатом выражения является значение True;  
  
-   иначе возникает статическая ошибка.  
  
 Затем логический оператор **and** и **or** применяется к результирующим логическим значениям выражений со стандартной логической семантикой.  
  
 Следующий запрос извлекает из каталога продуктов небольшие изображения с передним углом, <`Picture`>, для конкретной модели продукта. Обратите внимание, что для каждого документа с описанием продукта каталог может хранить одно или несколько изображений продукта с различными атрибутами, такими как размер и угол.  
  
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
  
## <a name="see-also"></a>См. также:  
 [Выражения языка XQuery](../xquery/xquery-expressions.md)  
  
  
