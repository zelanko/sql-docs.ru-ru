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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 31d83b00fd70cd54587a19ebfea7310154167493
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62999286"
---
# <a name="ordinary-arguments"></a>Обычные аргументы
Обычный аргумент строкового аргумента функции каталога, считается строковым литералом. Обычный аргумент принимает список значений, ни шаблон поиска строки. В случае обычных аргумента важен, и буквально кавычек в строке. Эти аргументы рассматриваются как обычные аргументы, если атрибут инструкции SQL_ATTR_METADATA_ID имеет значение SQL_FALSE; они обрабатываются как аргументы идентификатора вместо Если этот атрибут имеет значение SQL_TRUE.  
  
 Если аргумент — это обязательный аргумент обычный аргумент имеет значение является пустым указателем, функция возвращает значение SQL_ERROR и SQLSTATE HY009 (недопустимое использование пустого указателя). Если аргумент не является обязательным аргументом обычный аргумент имеет значение является пустым указателем, аргумент поведение зависит от драйвера. В следующей таблице перечислены обязательные аргументы.  
  
|Компонент|Обязательные аргументы|  
|--------------|------------------------|  
|**SQLColumnPrivileges**|*TableName*|  
|**SQLForeignKeys**|*PKTableName*, *FKTableName*|  
|**SQLPrimaryKeys**|*TableName*|  
|**SQLSpecialColumns**|*TableName*|  
|**SQLStatistics**|*TableName*|
