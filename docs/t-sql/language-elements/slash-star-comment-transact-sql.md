---
title: "Косая черта звезда комментария (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/27/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- /*...*/_TSQL
- Comment
- /*...*/
dev_langs:
- TSQL
helpviewer_keywords:
- nonexecuting text strings [SQL Server]
- /*...*/ (comment)
- remarks [SQL Server]
- comments [SQL Server]
ms.assetid: 4d9ab1b2-4bbb-4c16-beb1-cafc1af7417c
caps.latest.revision: 30
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3e617c6f0108906046d6c6ea983d1bbc26082709
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="slash-star-comment-transact-sql"></a>Комментарий типа «звезда» косая черта (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Обозначает текст комментария пользователя. Текст, помещенный между / * и \*/, не вычисляется сервером.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
/*  
text_of_comment  
*/  
```  
  
## <a name="arguments"></a>Аргументы  
 *text_of_comment*  
 Текст комментария. Это одна или более символьных строк.  
  
## <a name="remarks"></a>Замечания  
 Комментарии могут вставляться в отдельную строку или в пределах инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)]. Многострочные комментарии должны обозначаться символами / * и \*/. Для многострочных комментариев часто используется многострочных является начинается с первой строки или\*последующие строки — с \* \*и заканчиваться \*/.  
  
 Длина комментариев не ограничена.  
  
 Поддерживаются вложенные комментарии. Если / * комбинация символов используется в пределах существующего комментария, он рассматривается как начало вложенного комментария и, таким образом, требует метки \*/, закрывающей этот комментарий. Если метки, закрывающей комментарий, нет, выдается ошибка.  
  
 Например, следующий код вызовет ошибку:  
  
```  
DECLARE @comment AS varchar(20);  
GO  
/*  
SELECT @comment = '/*';  
*/   
SELECT @@VERSION;  
GO   
```  
  
 Чтобы избежать этой ошибки, внесите следующее изменение:  
  
```  
DECLARE @comment AS varchar(20);  
GO  
/*  
SELECT @comment = '/*';  
*/ */  
SELECT @@VERSION;  
GO  
  
```  
  
## <a name="examples"></a>Примеры  
 В приведенном ниже примере комментарии используются для пояснения действий, выполняемых блоком кода.  
  
```  
USE AdventureWorks2012;  
GO  
/*  
This section of the code joins the Person table with the Address table,   
by using the Employee and BusinessEntityAddress tables in the middle to   
get a list of all the employees in the AdventureWorks2012 database   
and their contact information.  
*/  
SELECT p.FirstName, p.LastName, a.AddressLine1, a.AddressLine2, a.City, a.PostalCode  
FROM Person.Person AS p  
JOIN HumanResources.Employee AS e ON p.BusinessEntityID = e.BusinessEntityID   
JOIN Person.BusinessEntityAddress AS ea ON e.BusinessEntityID = ea.BusinessEntityID  
JOIN Person.Address AS a ON ea.AddressID = a.AddressID;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [--&#40; Комментарий &#41; &#40; Transact-SQL &#41;](../../t-sql/language-elements/comment-transact-sql.md)   
 [Язык управления выполнением &#40; Transact-SQL &#41;](~/t-sql/language-elements/control-of-flow.md)  
  
  


