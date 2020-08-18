---
description: Функции JSON (Transact-SQL)
title: Функции JSON (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 06/03/2020
ms.prod: sql
ms.technology: t-sql
ms.topic: language-reference
helpviewer_keywords:
- JSON functions
ms.assetid: ec97d451-06af-44a3-8304-305d410cfc8e
author: jovanpop-msft
ms.author: jovanpop
ms.reviewer: jroth
monikerRange: = azuresqldb-current||= azure-sqldw-latest||>= sql-server-2016||>= sql-server-linux-2017||= sqlallproducts-allversions
ms.openlocfilehash: 06bf0965714c893d5b7684335edbb191e86ee77a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88364330"
---
# <a name="json-functions-transact-sql"></a>Функции JSON (Transact-SQL)

[!INCLUDE [sqlserver2016-asdb-asdbmi-asa](../../includes/applies-to-version/sqlserver2016-asdb-asdbmi-asa.md)]

С помощью функций, описанных на страницах в этом разделе, можно проверять или изменять текст в формате JSON, а также извлекать простые или сложные значения.  
  
|Функция|Описание|  
|--------------|-----------------|  
|[ISJSON](../../t-sql/functions/isjson-transact-sql.md)|Проверяет, что строка содержит допустимые данные JSON.|  
|[JSON_VALUE](../../t-sql/functions/json-value-transact-sql.md)|Извлекает скалярное значение из строки JSON.|  
|[JSON_QUERY](../../t-sql/functions/json-query-transact-sql.md)|Извлекает объект или массив из строки JSON.|  
|[JSON_MODIFY](../../t-sql/functions/json-modify-transact-sql.md)|Обновляет значение свойства в строке JSON и возвращает обновленную строку JSON.|

 Дополнительные сведения о встроенной поддержке формата JSON в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] см. в статье [Данные JSON (SQL Server)](../../relational-databases/json/json-data-sql-server.md).  

## <a name="see-also"></a>См. также

 - [Проверка, построение запросов и изменение данных JSON с помощью встроенных функций (SQL Server)](../../relational-databases/json/validate-query-and-change-json-data-with-built-in-functions-sql-server.md)
 - [Выражения пути JSON (SQL Server)](../../relational-databases/json/json-path-expressions-sql-server.md)
 - [Данные JSON (SQL Server)](../../relational-databases/json/json-data-sql-server.md)  
