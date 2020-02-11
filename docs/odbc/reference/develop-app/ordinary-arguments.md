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
ms.openlocfilehash: 997604b4376656d36d2bc4bc31f1959aa6c8a229
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67987827"
---
# <a name="ordinary-arguments"></a>Обычные аргументы
Если строковый аргумент функции каталога является обычным аргументом, он рассматривается как литеральная строка. Обычный аргумент не принимает ни шаблон поиска строки, ни список значений. Регистр обычного аргумента важен, а символы кавычек в строке выполняются буквально. Эти аргументы обрабатываются как обычные аргументы, если атрибуту инструкции SQL_ATTR_METADATA_ID присвоено значение SQL_FALSE. Вместо этого они обрабатываются как аргументы идентификатора, если для этого атрибута задано значение SQL_TRUE.  
  
 Если для обычного аргумента задан пустой указатель, а аргумент является обязательным аргументом, функция возвращает SQL_ERROR и SQLSTATE HY009 (недопустимое использование пустого указателя). Если для обычного аргумента задан пустой указатель, а аргумент не является обязательным аргументом, поведение аргумента зависит от драйвера. Необходимые аргументы перечислены в следующей таблице.  
  
|Компонент|Обязательные аргументы|  
|--------------|------------------------|  
|**SQLColumnPrivileges**|*TableName*|  
|**SQLForeignKeys**|*PKTableName*, *фктабленаме*|  
|**SQLPrimaryKeys**|*TableName*|  
|**SQLSpecialColumns**|*TableName*|  
|**SQLStatistics**|*TableName*|
