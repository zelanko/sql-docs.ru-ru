---
title: Обычные аргументы | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- arguments in catalog functions [ODBC], ordinary
- catalog functions [ODBC], arguments
- ordinary arguments [ODBC]
ms.assetid: a18cdae1-6b85-41cb-875c-b5a01ec90aeb
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5575a477ddd9ce4e29204a0146a96fb56cd919f6
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="ordinary-arguments"></a>Обычные аргументы
Строковый аргумент функции каталога — обычный аргумент, считается строковым литералом. Обычный аргумент не принимает шаблон поиска строки, ни список значений. В случае с обычным аргумент имеет значение и буквально берутся символов кавычек в строке. Эти аргументы рассматриваются как обычные аргументы, если атрибут инструкции SQL_ATTR_METADATA_ID имеет значение SQL_FALSE; они рассматриваются как идентификатор аргументы вместо этого атрибута задано значение SQL_TRUE.  
  
 Если обычный аргумент имеет значение является пустым указателем, а аргумент является обязательным, функция возвращает значение SQL_ERROR и SQLSTATE HY009 (недопустимое использование пустого указателя). Если аргумент не является обязательным аргументом обычный аргумент имеет значение является пустым указателем, аргумент поведение зависит от драйвера. В следующей таблице перечислены обязательные аргументы.  
  
|Функция|Обязательные аргументы|  
|--------------|------------------------|  
|**SQLColumnPrivileges**|*TableName*|  
|**SQLForeignKeys**|*PKTableName*, *FKTableName*|  
|**SQLPrimaryKeys**|*TableName*|  
|**SQLSpecialColumns**|*TableName*|  
|**SQLStatistics**|*TableName*|
