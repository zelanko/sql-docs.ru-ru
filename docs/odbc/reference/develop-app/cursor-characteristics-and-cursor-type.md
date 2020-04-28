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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8354fdabf6830780ec2d128492c86cc1edd582ac
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81301631"
---
# <a name="cursor-characteristics-and-cursor-type"></a>Характеристики и тип курсора
Приложение может указать характеристики курсора вместо того, чтобы указывать тип курсора (только последовательный, статический, управляемый набором ключей или динамический). Для этого приложение выбирает возможность прокрутки курсора (путем установки атрибута SQL_ATTR_CURSOR_SCROLLABLE оператора) и чувствительности (путем установки атрибута SQL_ATTR_CURSOR_SENSITIVITY инструкции) перед открытием курсора в маркере инструкции. Затем драйвер выбирает тип курсора, который наиболее эффективно предоставляет характеристики, запрошенные приложением.  
  
 Всякий раз, когда приложение устанавливает любой атрибут инструкции SQL_ATTR_CONCURRENCY, SQL_ATTR_CURSOR_SCROLLABLE, SQL_ATTR_CURSOR_SENSITIVITY или SQL_ATTR_CURSOR_TYPE, драйвер вносит необходимые изменения в другие атрибуты инструкции в этом наборе четырех атрибутов, чтобы их значения оставались постоянными. В результате, когда приложение задает характеристику курсора, драйвер может изменить атрибут, указывающий тип курсора на основе этого неявного выбора. Если приложение указывает тип, драйвер может изменить любые другие атрибуты в соответствии с характеристиками выбранного типа. Дополнительные сведения об этих атрибутах инструкций см. в описании функции [SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md) .  
  
 Приложение, устанавливающее атрибуты инструкции для указания как типа курсора, так и характеристик курсора, выполняет риск получения курсора, который не является самым эффективным методом, доступным на этом драйвере для удовлетворения требований приложения.  
  
 Неявный параметр атрибутов инструкции определяется драйвером, за исключением того, что он должен соответствовать следующим правилам:  
  
-   Однонаправленные курсоры никогда не поддаются прокрутке; см. Определение SQL_ATTR_CURSOR_SCROLLABLE в [SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md).  
  
-   Нечувствительные курсоры никогда не обновляются (поэтому их параллелизм доступен только для чтения); Это основано на определении нечувствительных курсоров в стандарте ISO SQL.  
  
 Следовательно, неявный параметр атрибутов инструкции происходит в случаях, описанных в следующей таблице.  
  
|Приложение задает для атрибута значение|Другие атрибуты заданы неявно|  
|-----------------------------------|-------------------------------------|  
|SQL_ATTR_CONCURRENCY SQL_CONCUR_READ_ONLY|SQL_ATTR_CURSOR_SENSITIVITY SQL_INSENSITIVE.|  
|SQL_ATTR_CONCURRENCY SQL_CONCUR_LOCK, SQL_CONCUR_ROWVER или SQL_CONCUR_VALUES|SQL_ATTR_CURSOR_SENSITIVITY SQL_UNSPECIFIED или SQL_SENSITIVE, как определено драйвером. Он не может быть установлен в SQL_INSENSITIVE, поскольку нечувствительные курсоры всегда доступны только для чтения.|  
|SQL_ATTR_CURSOR_SCROLLABLE SQL_NONSCROLLABLE|SQL_ATTR_CURSOR_TYPE SQL_CURSOR_FORWARD_ONLY|  
|SQL_ATTR_CURSOR_SCROLLABLE SQL_SCROLLABLE|SQL_ATTR_CURSOR_TYPE SQL_CURSOR_STATIC, SQL_CURSOR_KEYSET_DRIVEN или SQL_CURSOR_DYNAMIC, как указано в драйвере. Для него никогда не задается значение SQL_CURSOR_FORWARD_ONLY.|  
|SQL_ATTR_CURSOR_SENSITIVITY SQL_INSENSITIVE|SQL_ATTR_CONCURRENCY SQL_CONCUR_READ_ONLY.<br /><br /> SQL_ATTR_CURSOR_TYPE SQL_CURSOR_STATIC.|  
|SQL_ATTR_CURSOR_SENSITIVITY SQL_SENSITIVE|SQL_ATTR_CONCURRENCY SQL_CONCUR_LOCK, SQL_CONCUR_ROWVER или SQL_CONCUR_VALUES, как указано в драйвере. Для него никогда не задается значение SQL_CONCUR_READ_ONLY.<br /><br /> SQL_ATTR_CURSOR_TYPE для SQL_CURSOR_FORWARD_ONLY, SQL_CURSOR_STATIC, SQL_CURSOR_KEYSET_DRIVEN или SQL_CURSOR_DYNAMIC, как указано в драйвере.|  
|SQL_ATTR_CURSOR_SENSITIVITY SQL_UNSPECIFIED|SQL_ATTR_CONCURRENCY для SQL_CONCUR_READ_ONLY, SQL_CONCUR_LOCK, SQL_CONCUR_ROWVER или SQL_CONCUR_VALUES, как указано в драйвере.<br /><br /> SQL_ATTR_CURSOR_TYPE для SQL_CURSOR_FORWARD_ONLY, SQL_CURSOR_STATIC, SQL_CURSOR_KEYSET_DRIVEN или SQL_CURSOR_DYNAMIC, как указано в драйвере.|  
|SQL_ATTR_CURSOR_TYPE SQL_CURSOR_DYNAMIC|SQL_ATTR_SCROLLABLE SQL_SCROLLABLE.<br /><br /> SQL_ATTR_CURSOR_SENSITIVITY SQL_SENSITIVE. (Но только если SQL_ATTR_CONCURRENCY не равно SQL_CONCUR_READ_ONLY. Обновляемые динамические курсоры всегда чувствительны к изменениям, внесенным в их собственной транзакции.)|  
|SQL_ATTR_CURSOR_TYPE SQL_CURSOR_FORWARD_ONLY|SQL_ATTR_CURSOR_SCROLLABLE SQL_NONSCROLLABLE.|  
|SQL_ATTR_CURSOR_TYPE SQL_CURSOR_KEYSET_DRIVEN|SQL_ATTR_SCROLLABLE SQL_SCROLLABLE.<br /><br /> SQL_ATTR_SENSITIVITY SQL_UNSPECIFIED или SQL_SENSITIVE (в соответствии с определенными драйверами условиями, если SQL_ATTR_CONCURRENCY не SQL_CONCUR_READ_ONLY).|  
|SQL_ATTR_CURSOR_TYPE SQL_CURSOR_STATIC|SQL_ATTR_SCROLLABLE SQL_SCROLLABLE.<br /><br /> SQL_ATTR_SENSITIVITY SQL_INSENSITIVE (если SQL_ATTR_CONCURRENCY SQL_CONCUR_READ_ONLY).<br /><br /> SQL_ATTR_SENSITIVITY SQL_UNSPECIFIED или SQL_SENSITIVE (если SQL_ATTR_CONCURRENCY не SQL_CONCUR_READ_ONLY).|
