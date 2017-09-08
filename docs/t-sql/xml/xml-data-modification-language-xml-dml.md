---
title: "Язык модификации XML-данных (XML DML) | Документы Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- modifying data [SQL Server], XML DML
- XML [SQL Server], DML
- XML DML [SQL Server]
- data modification language [XML DML]
- data modifications [XML DML]
- DML [XML in SQL Server]
- XQuery, XML DML
- xml data type [SQL Server], XML DML
ms.assetid: 20ce50d2-c07b-4e41-93a7-1380d2cd49cb
caps.latest.revision: 29
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 18fb5825297754c59f2824b6f05150ddaed7bb9c
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="xml-data-modification-language-xml-dml"></a>Язык модификации XML-данных (XML DML)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Язык модификации XML-данных (XML DML) является расширением языка XQuery. Как определено консорциумом W3C, в языке XQuery отсутствует часть, касающаяся манипулирования данными (DML). XML DML, представленный в этом разделе, а также язык XQuery обеспечивает полнофункциональный запросов и языка модификации данных, который можно использовать для **xml** тип данных.  
  
 В язык XML DML добавлены следующие ключевые слова с учетом регистра, которые отсутствуют в языке XQuery:  
  
-   **Вставка**  
  
-   **удалить**  
  
-   **Замените значение**  
  
 Как описано в [тип данных XML и столбцами &#40; SQL Server &#41; ](../../relational-databases/xml/xml-data-type-and-columns-sql-server.md), можно создать переменные и столбцы типа **xml** и присваивать им XML-документы или фрагменты. Чтобы модифицировать или обновить эти экземпляры XML, выполните следующее:  
  
-   Используйте [xml метод modify() типа данных)](../../t-sql/xml/modify-method-xml-data-type.md) из **xml** тип данных.  
  
-   Укажите соответствующие инструкции XML DML внутри **modify()** метод.  
  
 Заметим, что существуют атрибуты, которые нельзя добавить, удалить или изменить их значение. Например:  
  
-   Для типизированного или нетипизированного **xml,** атрибуты имеют **xmlns**, **xmlns:\***, и **XML: Base**.  
  
-   Для типизированного **xml** только атрибуты имеют **xsi: nil**, и **xsi: Type**.  
  
 К другим ограничениям также относятся:  
  
-   Для типизированного или нетипизированного **xml**, добавление атрибута **XML: Base** завершится ошибкой.  
  
-   Для типизированного **xml**, удаление и изменение **xsi: nil** атрибут завершится ошибкой. Для нетипизированного **xml**, можно удалить атрибут или модифицировать его значение.  
  
-   Для типизированного **xml**, изменив значение **xs: Type** атрибут завершится ошибкой. Для нетипизированного **xml**, можно изменить значение атрибута.  
  
 При модификации экземпляра типизированного xml конечный формат должен являться допустимым экземпляром типа, иначе возвращается ошибка проверки.  
  
## <a name="see-also"></a>См. также:  
 [Добавить &#40; Язык XML DML &#41;](../../t-sql/xml/insert-xml-dml.md)   
 [Удалить &#40; Язык XML DML &#41;](../../t-sql/xml/delete-xml-dml.md)   
 [Замените значение &#40; Язык XML DML &#41;](../../t-sql/xml/replace-value-of-xml-dml.md)   
 [Сравнение типизированного и нетипизированного XML](../../relational-databases/xml/compare-typed-xml-to-untyped-xml.md)   
 [Создание экземпляров XML-данных](../../relational-databases/xml/create-instances-of-xml-data.md)   
 [Методы для типа данных XML](../../t-sql/xml/xml-data-type-methods.md)  
  
  
