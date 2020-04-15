---
title: Обыкновенные Аргументы Документы Майкрософт
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81282472"
---
# <a name="ordinary-arguments"></a>Обычные аргументы
Когда аргумент строки функции функции каталога является обычным аргументом, он рассматривается как буквальная строка. Обычный аргумент не принимает ни шаблон ажурного поиска, ни список значений. Случай обычного аргумента значителен, и символы цитаты в шнуре приняты буквальн. Эти аргументы рассматриваются как обычные аргументы, если атрибут SQL_ATTR_METADATA_ID оператора установлен на SQL_FALSE; вместо этого они рассматриваются как аргументы идентификатора, если этот атрибут установлен SQL_TRUE.  
  
 Если обычный аргумент установлен на нулевую точку, а аргумент является обязательным аргументом, функция возвращается SQL_ERROR и S'LSTATE HY009 (Недействительное использование нулевого указателя). Если обычный аргумент установлен на нулевую точку, а аргумент не является обязательным аргументом, поведение аргумента зависит от водителя. Необходимые аргументы перечислены в следующей таблице.  
  
|Компонент|Необходимые аргументы|  
|--------------|------------------------|  
|**SQLColumnPrivileges**|*Tablename*|  
|**SQLForeignKeys**|*PKTableName*, *FKTableName*|  
|**SQLPrimaryKeys**|*Tablename*|  
|**SQLSpecialColumns**|*Tablename*|  
|**SQLStatistics**|*Tablename*|
