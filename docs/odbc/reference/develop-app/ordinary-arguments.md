---
description: Обычные аргументы
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
ms.openlocfilehash: b6e4e7a30efe5735aa87665d7d0247bef06390ce
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88429176"
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
