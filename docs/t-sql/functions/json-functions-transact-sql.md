---
title: Функции JSON (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 07/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: genemi
ms.technology: t-sql
ms.topic: language-reference
helpviewer_keywords:
- JSON functions
ms.assetid: ec97d451-06af-44a3-8304-305d410cfc8e
author: jovanpop-msft
ms.author: jovanpop
manager: craigg
monikerRange: = azuresqldb-current||= azure-sqldw-latest||>= sql-server-2016||>= sql-server-linux-2017||= sqlallproducts-allversions
ms.openlocfilehash: bd5ea0433b1cbdee6adf97dbab9a2dcdddcb8389
ms.sourcegitcommit: dda9a1a7682ade466b8d4f0ca56f3a9ecc1ef44e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/14/2019
ms.locfileid: "65577462"
---
# <a name="json-functions-transact-sql"></a>Функции JSON (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2016-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-asdw-xxx-md.md)]

С помощью функций, описанных на страницах в этом разделе, можно проверять или изменять текст в формате JSON, а также извлекать простые или сложные значения.  
  
|Компонент|Описание|  
|--------------|-----------------|  
|[ISJSON](../../t-sql/functions/isjson-transact-sql.md)|Проверяет, что строка содержит допустимые данные JSON.|  
|[JSON_VALUE](../../t-sql/functions/json-value-transact-sql.md)|Извлекает скалярное значение из строки JSON.|  
|[JSON_QUERY](../../t-sql/functions/json-query-transact-sql.md)|Извлекает объект или массив из строки JSON.|  
|[JSON_MODIFY](../../t-sql/functions/json-modify-transact-sql.md)|Обновляет значение свойства в строке JSON и возвращает обновленную строку JSON.|

 Дополнительные сведения о встроенной поддержке формата JSON в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] см. в статье [Данные JSON (SQL Server)](../../relational-databases/json/json-data-sql-server.md).  

## <a name="see-also"></a>См. также:

 - [Проверка, построение запросов и изменение данных JSON с помощью встроенных функций (SQL Server)](../../relational-databases/json/validate-query-and-change-json-data-with-built-in-functions-sql-server.md)
 - [Выражения пути JSON (SQL Server)](../../relational-databases/json/json-path-expressions-sql-server.md)
 - [Данные JSON (SQL Server)](../../relational-databases/json/json-data-sql-server.md)  
