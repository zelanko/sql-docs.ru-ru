---
title: "Обычные аргументы | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- arguments in catalog functions [ODBC], ordinary
- catalog functions [ODBC], arguments
- ordinary arguments [ODBC]
ms.assetid: a18cdae1-6b85-41cb-875c-b5a01ec90aeb
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9aaaa374817d84eaa01dc96fa3783623e7b4b905
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="ordinary-arguments"></a>Обычные аргументы
Строковый аргумент функции каталога — обычный аргумент, считается строковым литералом. Обычный аргумент не принимает шаблон поиска строки, ни список значений. В случае с обычным аргумент имеет значение и буквально берутся символов кавычек в строке. Эти аргументы рассматриваются как обычные аргументы, если атрибут инструкции SQL_ATTR_METADATA_ID имеет значение SQL_FALSE; они рассматриваются как идентификатор аргументы вместо этого атрибута задано значение SQL_TRUE.  
  
 Если обычный аргумент имеет значение является пустым указателем, а аргумент является обязательным, функция возвращает значение SQL_ERROR и SQLSTATE HY009 (недопустимое использование пустого указателя). Если аргумент не является обязательным аргументом обычный аргумент имеет значение является пустым указателем, аргумент поведение зависит от драйвера. В следующей таблице перечислены обязательные аргументы.  
  
|Функция|Обязательные аргументы|  
|--------------|------------------------|  
|**SQLColumnPrivileges**|*Имя_таблицы*|  
|**SQLForeignKeys**|*PKTableName*, *FKTableName*|  
|**SQLPrimaryKeys**|*Имя_таблицы*|  
|**SQLSpecialColumns**|*Имя_таблицы*|  
|**SQLStatistics**|*Имя_таблицы*|

