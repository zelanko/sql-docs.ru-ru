---
title: Обычные аргументы | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- arguments in catalog functions [ODBC], ordinary
- catalog functions [ODBC], arguments
- ordinary arguments [ODBC]
ms.assetid: a18cdae1-6b85-41cb-875c-b5a01ec90aeb
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 97362f93e91ccd8b592b4c05a0714b7602c1ba94
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81282472"
---
# <a name="ordinary-arguments"></a>Обычные аргументы
Если строковый аргумент функции каталога является обычным аргументом, он рассматривается как литеральная строка. Обычный аргумент не принимает ни шаблон поиска строки, ни список значений. Регистр обычного аргумента важен, а символы кавычек в строке выполняются буквально. Эти аргументы обрабатываются как обычные аргументы, если атрибуту инструкции SQL_ATTR_METADATA_ID присвоено значение SQL_FALSE. Вместо этого они обрабатываются как аргументы идентификатора, если для этого атрибута задано значение SQL_TRUE.  
  
 Если для обычного аргумента задан пустой указатель, а аргумент является обязательным аргументом, функция возвращает SQL_ERROR и SQLSTATE HY009 (недопустимое использование пустого указателя). Если для обычного аргумента задан пустой указатель, а аргумент не является обязательным аргументом, поведение аргумента зависит от драйвера. Необходимые аргументы перечислены в следующей таблице.  
  
|Функция|Обязательные аргументы|  
|--------------|------------------------|  
|**SQLColumnPrivileges**|*TableName*|  
|**SQLForeignKeys**|*PKTableName*, *фктабленаме*|  
|**SQLPrimaryKeys**|*TableName*|  
|**SQLSpecialColumns**|*TableName*|  
|**SQLStatistics**|*TableName*|
