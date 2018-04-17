---
title: Характеристики курсора и тип курсора | Документы Microsoft
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
- scrollable cursors [ODBC]
- cursors [ODBC], scrollable
- cursors [ODBC], creating
ms.assetid: 6f67edd2-ae71-4ca0-9b2d-abf4c20dc17b
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f54cc2f954a67d7a9cb3a4dfa6f6a006b652611d
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="cursor-characteristics-and-cursor-type"></a>Характеристики курсора и тип курсора
Приложение может указать характеристики курсора вместо указания типа курсора (однонаправленные, статические, управляемые набором ключей или динамического). Для этого приложение выбирает курсор прокрутки (путем установки атрибута инструкции SQL_ATTR_CURSOR_SCROLLABLE) и чувствительности (путем установки атрибута инструкции SQL_ATTR_CURSOR_SENSITIVITY) перед открытием курсора на инструкции дескриптор. Драйвер выбирает тип курсора, который наиболее эффективно предоставляет характеристики, запрошенное приложение.  
  
 Каждый раз, когда приложение задает атрибуты инструкции SQL_ATTR_CONCURRENCY, SQL_ATTR_CURSOR_SCROLLABLE, SQL_ATTR_CURSOR_SENSITIVITY или SQL_ATTR_CURSOR_TYPE, драйвер делает все необходимое изменение в другие атрибуты инструкции, в рамках этого курса четыре атрибутов, чтобы их значения остаются согласованными. В результате, когда приложение задает характеристики курсора, драйвер можно изменить атрибут, указывающий тип курсора, на основе неявных выбора; Когда приложение задает тип, драйвер можно изменить другие атрибуты для соответствия характеристики выбранного типа. Дополнительные сведения об этих атрибутах инструкции см. в разделе [SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md) описание функции.  
  
 Приложение, которое задает атрибуты инструкции, чтобы указать тип курсора и характеристики курсора грозит получения в курсор, который не является самым эффективным методом, доступные для этого драйвера для соответствия требованиям приложения.  
  
 Неявный параметр атрибуты инструкции определяется от драйвера, за исключением того, необходимо соблюдать следующие правила:  
  
-   Однопроходные курсоры никогда не могут быть прокручены; просмотреть определение SQL_ATTR_CURSOR_SCROLLABLE в [SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md).  
  
-   Нечувствительных курсоров никогда не являются обновляемыми (и, следовательно их параллелизма только для чтения); Следующий пример основан на их определение нечувствительных курсоров в стандарте ISO SQL.  
  
 Следовательно неявный параметр атрибуты инструкции происходит случаев, описанных в следующей таблице.  
  
|Приложение устанавливает атрибут|Неявно других атрибутов|  
|-----------------------------------|-------------------------------------|  
|SQL_ATTR_CONCURRENCY для SQL_CONCUR_READ_ONLY|SQL_ATTR_CURSOR_SENSITIVITY для SQL_INSENSITIVE.|  
|SQL_ATTR_CONCURRENCY SQL_CONCUR_LOCK, SQL_CONCUR_ROWVER или SQL_CONCUR_VALUES|SQL_ATTR_CURSOR_SENSITIVITY SQL_UNSPECIFIED или SQL_SENSITIVE в соответствии с драйвером. Он может никогда не будет присвоено SQL_INSENSITIVE, так как без учета курсоры всегда доступны только для чтения.|  
|SQL_ATTR_CURSOR_SCROLLABLE для SQL_NONSCROLLABLE|SQL_ATTR_CURSOR_TYPE для SQL_CURSOR_FORWARD_ONLY|  
|SQL_ATTR_CURSOR_SCROLLABLE для SQL_SCROLLABLE|SQL_ATTR_CURSOR_TYPE SQL_CURSOR_STATIC, SQL_CURSOR_KEYSET_DRIVEN или SQL_CURSOR_DYNAMIC в соответствии с помощью драйвера. Он никогда не имеет значение SQL_CURSOR_FORWARD_ONLY.|  
|SQL_ATTR_CURSOR_SENSITIVITY для SQL_INSENSITIVE|SQL_ATTR_CONCURRENCY для SQL_CONCUR_READ_ONLY.<br /><br /> SQL_ATTR_CURSOR_TYPE для SQL_CURSOR_STATIC.|  
|SQL_ATTR_CURSOR_SENSITIVITY значение SQL_SENSITIVE|SQL_ATTR_CONCURRENCY SQL_CONCUR_LOCK, SQL_CONCUR_ROWVER или SQL_CONCUR_VALUES в соответствии с помощью драйвера. Он никогда не имеет значение SQL_CONCUR_READ_ONLY.<br /><br /> SQL_ATTR_CURSOR_TYPE SQL_CURSOR_FORWARD_ONLY, SQL_CURSOR_STATIC, SQL_CURSOR_KEYSET_DRIVEN или SQL_CURSOR_DYNAMIC в соответствии с помощью драйвера.|  
|SQL_ATTR_CURSOR_SENSITIVITY для SQL_UNSPECIFIED|SQL_ATTR_CONCURRENCY для SQL_CONCUR_LOCK SQL_CONCUR_READ_ONLY, SQL_CONCUR_ROWVER или SQL_CONCUR_VALUES в соответствии с помощью драйвера.<br /><br /> SQL_ATTR_CURSOR_TYPE SQL_CURSOR_FORWARD_ONLY, SQL_CURSOR_STATIC, SQL_CURSOR_KEYSET_DRIVEN или SQL_CURSOR_DYNAMIC в соответствии с помощью драйвера.|  
|SQL_ATTR_CURSOR_TYPE для SQL_CURSOR_DYNAMIC|SQL_ATTR_SCROLLABLE для SQL_SCROLLABLE.<br /><br /> SQL_ATTR_CURSOR_SENSITIVITY значение SQL_SENSITIVE. (Но только в том случае, если не равен SQL_CONCUR_READ_ONLY SQL_ATTR_CONCURRENCY. Обновляемые динамические курсоры всегда могут чувствительные к изменениям, которые были сделаны в собственную транзакцию.)|  
|SQL_ATTR_CURSOR_TYPE для SQL_CURSOR_FORWARD_ONLY|Значением параметра SQL_ATTR_CURSOR_SCROLLABLE SQL_NONSCROLLABLE.|  
|SQL_ATTR_CURSOR_TYPE для SQL_CURSOR_KEYSET_DRIVEN|SQL_ATTR_SCROLLABLE для SQL_SCROLLABLE.<br /><br /> SQL_ATTR_SENSITIVITY SQL_UNSPECIFIED или SQL_SENSITIVE (в соответствии с определяемым драйвером критерии, если не SQL_ATTR_CONCURRENCY SQL_CONCUR_READ_ONLY).|  
|SQL_ATTR_CURSOR_TYPE для SQL_CURSOR_STATIC|SQL_ATTR_SCROLLABLE для SQL_SCROLLABLE.<br /><br /> SQL_ATTR_SENSITIVITY для SQL_INSENSITIVE (если SQL_ATTR_CONCURRENCY SQL_CONCUR_READ_ONLY).<br /><br /> SQL_ATTR_SENSITIVITY SQL_UNSPECIFIED или SQL_SENSITIVE (если SQL_ATTR_CONCURRENCY не SQL_CONCUR_READ_ONLY).|
