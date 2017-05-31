---
title: "Написание инструкций Transact-SQL, адаптированных к международному использованию | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- writing international statements
- Transact-SQL international considerations
- international considerations [SQL Server], Transact-SQL
- Database Engine international considerations [SQL Server], Transact-SQL
- statements [SQL Server], international
- database international considerations [SQL Server], Transact-SQL
- dates [SQL Server], international considerations
ms.assetid: f0b10fee-27f7-45fe-aece-ccc3f63bdcdb
caps.latest.revision: 35
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 8c73a4b7e8d9c3e470136942c830a0ba879ed420
ms.contentlocale: ru-ru
ms.lasthandoff: 04/11/2017

---
# <a name="write-international-transact-sql-statements"></a>Написание инструкций Transact-SQL, адаптированных к международному использованию
  В базах данных и использующих их приложениях, в которых применяются инструкции языка [!INCLUDE[tsql](../../includes/tsql-md.md)] , можно обеспечить большую степень языковой переносимости или поддержку нескольких языков при условии соблюдения следующих требований.  
  
-   Все элементы с типами данных **char**, **varchar**и **text** замените элементами с типами данных **nchar**, **nvarchar**и **nvarchar(max)**. Такая замена устраняет возможные проблемы с преобразованием кодовых страниц. Дополнительные сведения см. в статье [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md).  
  
-   При выполнении сравнения и других операций со значениями месяцев и дней недели следует использовать числовые эквиваленты вместо строковых имен. При различных языковых настройках возвращаются различные названия месяцев и дней недели. Например, функция DATENAME(MONTH,GETDATE()) при выбранном английском (США) языке возвращает значение «May», при немецком — «Mai», а при французском — «mai». Вместо нее следует использовать функцию DATEPART(), в которой вместо названия месяца используется его номер. При выводе результирующих наборов пользователю лучше использовать названия из функции DATEPART(), так как они зачастую более информативны, чем числовое представление даты. Однако не следует кодировать какую-либо логику, зависящую от отображаемых названий на том или ином языке.  
  
-   При указании дат для сравнения либо ввода с помощью инструкций INSERT или UPDATE следует использовать константы, интерпретируемые одним и тем же образом для всех языковых настроек.  
  
    -   В приложениях ADO, OLE DB и ODBC следует использовать принятые в ODBC форматы отметок времени, даты и времени:  
  
         **{ ts'**гггг**-***мм***-***дд**чч***:***мм***:***сс*[**.***fff*] **'}** , например: **{ ts'**1998**-**09**-**24 10**:**02**:**20**' }**  
  
         **{ d'** *yyyy* **-** *mm* **-** *dd* **'}** such as: **{ d'**1998**-**09**-**24**'}**  
  
         **{ t'** *hh* **:** *mm* **:** *ss* **'}** such as: **{ t'**10:02:20**'}**  
  
    -   В приложениях с использованием других прикладных программных API-интерфейсов, а также в скриптах языка [!INCLUDE[tsql](../../includes/tsql-md.md)] , хранимых процедурах и триггерах следует использовать числовые строки без разделителей. Например, *yyyymmdd* в виде 19980924.  
  
    -   В приложениях с использованием других программных интерфейсов API, а также в скриптах языка [!INCLUDE[tsql](../../includes/tsql-md.md)] , хранимых процедурах и триггерах следует использовать инструкцию CONVERT с явно заданным параметром стиля для всех преобразований между типами данных **time**, **date**, **smalldate**, **datetime**, **datetime2**и **datetimeoffset** , а также строковыми типами данных. Например, следующая инструкция интерпретируется одинаково для любых настроек языка и формата даты в соединении:  
  
        ```  
        SELECT *  
        FROM AdventureWorks2012.Sales.SalesOrderHeader  
        WHERE OrderDate = CONVERT(DATETIME, '20060719', 101)  
        ```  
  
         Дополнительные сведения см. в разделе [Функции CAST и CONVERT (Transact-SQL)](../../t-sql/functions/cast-and-convert-transact-sql.md).  
  
  
