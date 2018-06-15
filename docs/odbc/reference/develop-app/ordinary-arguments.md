---
title: Обычные аргументы | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- arguments in catalog functions [ODBC], ordinary
- catalog functions [ODBC], arguments
- ordinary arguments [ODBC]
ms.assetid: a18cdae1-6b85-41cb-875c-b5a01ec90aeb
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7ecdcf5e697bcf3235cadbe3d8f3f8f981406575
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32911649"
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
