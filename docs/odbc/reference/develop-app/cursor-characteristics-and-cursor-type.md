---
title: Характеристики курсора и тип курсора | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- scrollable cursors [ODBC]
- cursors [ODBC], scrollable
- cursors [ODBC], creating
ms.assetid: 6f67edd2-ae71-4ca0-9b2d-abf4c20dc17b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: dbef278f3f25b572ddc44e87d60b5cdcd33058c1
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63043829"
---
# <a name="cursor-characteristics-and-cursor-type"></a>Характеристики и тип курсора
Приложение может указать характеристики курсора вместо указания типа курсора (однопроходный, статический, управляемые набором ключей или динамического). Для этого приложение выбирает прокрутки курсора (путем установки атрибута инструкции SQL_ATTR_CURSOR_SCROLLABLE) и чувствительности (путем установки атрибута инструкции SQL_ATTR_CURSOR_SENSITIVITY) перед открытием курсора в инструкции дескриптор. Драйвер затем выбирает тип курсора, который наиболее эффективным образом предоставляет характеристики, запрошенное приложение.  
  
 Каждый раз, когда приложение задает атрибуты инструкции SQL_ATTR_CONCURRENCY, SQL_ATTR_CURSOR_SCROLLABLE, параметр SQL_ATTR_CURSOR_SENSITIVITY или SQL_ATTR_CURSOR_TYPE, драйвер производит любые необходимые изменения в другие атрибуты инструкции, в рамках этого курса четыре атрибутов таким образом, чтобы их значения остаются согласованными. Таким образом Если приложение задает характеристики курсора, драйвер можно изменить атрибут, указывающий тип курсора, на основе неявных выбора; Когда приложения указан тип, драйвер можно изменить другие атрибуты, для согласования с характеристики выбранного типа. Дополнительные сведения об этих атрибутах инструкции см. в разделе [SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md) описание функции.  
  
 Приложение, которое задает атрибуты инструкции, чтобы указать тип курсора и характеристики курсора выполняется риск получения в курсор, который не является самым эффективным методом, на этот драйвер для удовлетворения требований приложения.  
  
 Неявный параметр атрибуты инструкции определяется от драйвера, за исключением того, что он должен соответствовать следующим правилам:  
  
-   Однопроходные курсоры никогда не поддерживает прокрутку; просмотреть определение SQL_ATTR_CURSOR_SCROLLABLE в [SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md).  
  
-   Нечувствительных курсоров никогда не бывают обновляемыми (и таким образом их параллелизма только для чтения); Это основано на их определения нечувствительных курсоров в стандарте ISO SQL.  
  
 Следовательно неявный параметр атрибуты инструкции происходит в случаях, описанных в следующей таблице.  
  
|Приложение устанавливает атрибут|Неявно других атрибутов|  
|-----------------------------------|-------------------------------------|  
|SQL_ATTR_CONCURRENCY для SQL_CONCUR_READ_ONLY|Параметр SQL_ATTR_CURSOR_SENSITIVITY для SQL_INSENSITIVE.|  
|SQL_ATTR_CONCURRENCY SQL_CONCUR_LOCK, SQL_CONCUR_ROWVER или SQL_CONCUR_VALUES|SQL_ATTR_CURSOR_SENSITIVITY SQL_UNSPECIFIED или SQL_SENSITIVE, как определено с помощью драйвера. Его можно никогда не присвоить SQL_INSENSITIVE, так как без учета курсоры всегда доступны только для чтения.|  
|SQL_ATTR_CURSOR_SCROLLABLE для SQL_NONSCROLLABLE|SQL_ATTR_CURSOR_TYPE для SQL_CURSOR_FORWARD_ONLY|  
|SQL_ATTR_CURSOR_SCROLLABLE для SQL_SCROLLABLE|SQL_ATTR_CURSOR_TYPE SQL_CURSOR_STATIC, SQL_CURSOR_KEYSET_DRIVEN или SQL_CURSOR_DYNAMIC, как указано с помощью драйвера. Он никогда не будет присвоено SQL_CURSOR_FORWARD_ONLY.|  
|SQL_ATTR_CURSOR_SENSITIVITY для SQL_INSENSITIVE|SQL_ATTR_CONCURRENCY для SQL_CONCUR_READ_ONLY.<br /><br /> SQL_ATTR_CURSOR_TYPE для SQL_CURSOR_STATIC.|  
|SQL_ATTR_CURSOR_SENSITIVITY для SQL_SENSITIVE|SQL_ATTR_CONCURRENCY SQL_CONCUR_LOCK, SQL_CONCUR_ROWVER или SQL_CONCUR_VALUES, как указано с помощью драйвера. Он никогда не будет присвоено SQL_CONCUR_READ_ONLY.<br /><br /> SQL_ATTR_CURSOR_TYPE SQL_CURSOR_FORWARD_ONLY, SQL_CURSOR_STATIC, SQL_CURSOR_KEYSET_DRIVEN или SQL_CURSOR_DYNAMIC, как указано с помощью драйвера.|  
|SQL_ATTR_CURSOR_SENSITIVITY для SQL_UNSPECIFIED|SQL_ATTR_CONCURRENCY для SQL_CONCUR_LOCK SQL_CONCUR_READ_ONLY, SQL_CONCUR_ROWVER или SQL_CONCUR_VALUES, как указано с помощью драйвера.<br /><br /> SQL_ATTR_CURSOR_TYPE SQL_CURSOR_FORWARD_ONLY, SQL_CURSOR_STATIC, SQL_CURSOR_KEYSET_DRIVEN или SQL_CURSOR_DYNAMIC, как указано с помощью драйвера.|  
|SQL_ATTR_CURSOR_TYPE для SQL_CURSOR_DYNAMIC|SQL_ATTR_SCROLLABLE для SQL_SCROLLABLE.<br /><br /> Параметр SQL_ATTR_CURSOR_SENSITIVITY для SQL_SENSITIVE. (Но только в том случае, если не равно SQL_CONCUR_READ_ONLY SQL_ATTR_CONCURRENCY. Обновляемые динамические курсоры всегда доступны к изменениям, которые были внесены в собственную транзакцию.)|  
|SQL_ATTR_CURSOR_TYPE для SQL_CURSOR_FORWARD_ONLY|Значением параметра SQL_ATTR_CURSOR_SCROLLABLE SQL_NONSCROLLABLE.|  
|SQL_ATTR_CURSOR_TYPE для SQL_CURSOR_KEYSET_DRIVEN|SQL_ATTR_SCROLLABLE для SQL_SCROLLABLE.<br /><br /> SQL_ATTR_SENSITIVITY SQL_UNSPECIFIED или SQL_SENSITIVE (в соответствии с определяемым драйвером критериями, если SQL_ATTR_CONCURRENCY не SQL_CONCUR_READ_ONLY).|  
|SQL_ATTR_CURSOR_TYPE для SQL_CURSOR_STATIC|SQL_ATTR_SCROLLABLE для SQL_SCROLLABLE.<br /><br /> SQL_ATTR_SENSITIVITY для SQL_INSENSITIVE (если SQL_ATTR_CONCURRENCY SQL_CONCUR_READ_ONLY).<br /><br /> SQL_ATTR_SENSITIVITY SQL_UNSPECIFIED или SQL_SENSITIVE (если SQL_ATTR_CONCURRENCY не SQL_CONCUR_READ_ONLY).|
