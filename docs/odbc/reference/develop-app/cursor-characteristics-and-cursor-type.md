---
title: Характеристики курсора и тип курсора (ru) Документы Майкрософт
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301631"
---
# <a name="cursor-characteristics-and-cursor-type"></a>Характеристики и тип курсора
Приложение может указать характеристики курсора вместо указания типа курсора (только вперед, статического, управляемого ключем или динамического). Для этого приложение выбирает прокрутку курсора (установив атрибут SQL_ATTR_CURSOR_SCROLLABLE оператора) и чувствительность (установив атрибут SQL_ATTR_CURSOR_SENSITIVITY оператора) перед открытием курсора на рукоятке оператора. Затем драйвер выбирает тип курсора, который наиболее эффективно обеспечивает характеристики, запрошенные приложением.  
  
 Всякий раз, когда приложение устанавливает какие-либо атрибуты оператора SQL_ATTR_CONCURRENCY, SQL_ATTR_CURSOR_SCROLLABLE, SQL_ATTR_CURSOR_SENSITIVITY или SQL_ATTR_CURSOR_TYPE, драйвер вносит необходимые изменения в другие атрибуты оператора в этом наборе из четырех атрибутов, чтобы их значения оставались согласованными. В результате, когда приложение определяет характеристику курсора, драйвер может изменить атрибут, указывающий тип курсора на основе этого неявного выбора; когда приложение определяет тип, драйвер может изменить любой из других атрибутов, чтобы соответствовать характеристикам выбранного типа. Для получения более подробной информации [SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md) об этих атрибутах оператора см.  
  
 Приложение, которое устанавливает атрибуты оператора для указания типа курсора и характеристики курсора, рискует получить курсор, который не является наиболее эффективным методом, доступным на этом драйвере, удовлетворяющий требованиям приложения.  
  
 Неявная настройка атрибутов оператора определяется драйвером, за исключением того, что она должна следовать следующим правилам:  
  
-   Курсоры только вперед никогда не прокручиваются; см. определение SQL_ATTR_CURSOR_SCROLLABLE в [S'LSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md).  
  
-   Нечувствительные курсоры никогда не updatable (и, таким образом, их параллелизм читается только); это основано на их определении бесчувственных курсоров в стандарте ISO S'L.  
  
 Следовательно, неявное установление атрибутов оператора происходит в случаях, описанных в следующей таблице.  
  
|Наборы приложений attributeto to|Другие атрибуты, установленные неявно|  
|-----------------------------------|-------------------------------------|  
|SQL_ATTR_CONCURRENCY to SQL_CONCUR_READ_ONLY|SQL_ATTR_CURSOR_SENSITIVITY to SQL_INSENSITIVE.|  
|SQL_ATTR_CONCURRENCY SQL_CONCUR_LOCK, SQL_CONCUR_ROWVER или SQL_CONCUR_VALUES|SQL_ATTR_CURSOR_SENSITIVITY SQL_UNSPECIFIED или SQL_SENSITIVE, как это определено водителем. Он никогда не может быть установлен на SQL_INSENSITIVE, потому что бесчувственные курсоры всегда читать только.|  
|SQL_ATTR_CURSOR_SCROLLABLE to SQL_NONSCROLLABLE|SQL_ATTR_CURSOR_TYPE to SQL_CURSOR_FORWARD_ONLY|  
|SQL_ATTR_CURSOR_SCROLLABLE to SQL_SCROLLABLE|SQL_ATTR_CURSOR_TYPE SQL_CURSOR_STATIC, SQL_CURSOR_KEYSET_DRIVEN или SQL_CURSOR_DYNAMIC, как указано водителем. Он никогда не установлен на SQL_CURSOR_FORWARD_ONLY.|  
|SQL_ATTR_CURSOR_SENSITIVITY to SQL_INSENSITIVE|SQL_ATTR_CONCURRENCY to SQL_CONCUR_READ_ONLY.<br /><br /> SQL_ATTR_CURSOR_TYPE to SQL_CURSOR_STATIC.|  
|SQL_ATTR_CURSOR_SENSITIVITY to SQL_SENSITIVE|SQL_ATTR_CONCURRENCY SQL_CONCUR_LOCK, SQL_CONCUR_ROWVER или SQL_CONCUR_VALUES, как указано водителем. Он никогда не установлен на SQL_CONCUR_READ_ONLY.<br /><br /> SQL_ATTR_CURSOR_TYPE SQL_CURSOR_FORWARD_ONLY, SQL_CURSOR_STATIC, SQL_CURSOR_KEYSET_DRIVEN или SQL_CURSOR_DYNAMIC, как указано водителем.|  
|SQL_ATTR_CURSOR_SENSITIVITY to SQL_UNSPECIFIED|SQL_ATTR_CONCURRENCY SQL_CONCUR_READ_ONLY, SQL_CONCUR_LOCK, SQL_CONCUR_ROWVER или SQL_CONCUR_VALUES, как указано водителем.<br /><br /> SQL_ATTR_CURSOR_TYPE SQL_CURSOR_FORWARD_ONLY, SQL_CURSOR_STATIC, SQL_CURSOR_KEYSET_DRIVEN или SQL_CURSOR_DYNAMIC, как указано водителем.|  
|SQL_ATTR_CURSOR_TYPE to SQL_CURSOR_DYNAMIC|SQL_ATTR_SCROLLABLE to SQL_SCROLLABLE.<br /><br /> SQL_ATTR_CURSOR_SENSITIVITY to SQL_SENSITIVE. (Но только в том случае, если SQL_ATTR_CONCURRENCY не равна SQL_CONCUR_READ_ONLY. Динамические курсоры Updatable всегда чувствительны к изменениям, внесенным в их собственной транзакции.)|  
|SQL_ATTR_CURSOR_TYPE to SQL_CURSOR_FORWARD_ONLY|SQL_ATTR_CURSOR_SCROLLABLE to SQL_NONSCROLLABLE.|  
|SQL_ATTR_CURSOR_TYPE to SQL_CURSOR_KEYSET_DRIVEN|SQL_ATTR_SCROLLABLE to SQL_SCROLLABLE.<br /><br /> SQL_ATTR_SENSITIVITY SQL_UNSPECIFIED или SQL_SENSITIVE (в соответствии с критериями, установленными водителем, если SQL_ATTR_CONCURRENCY не SQL_CONCUR_READ_ONLY).|  
|SQL_ATTR_CURSOR_TYPE в SQL_CURSOR_STATIC|SQL_ATTR_SCROLLABLE to SQL_SCROLLABLE.<br /><br /> SQL_ATTR_SENSITIVITY SQL_INSENSITIVE (если SQL_ATTR_CONCURRENCY SQL_CONCUR_READ_ONLY).<br /><br /> SQL_ATTR_SENSITIVITY SQL_UNSPECIFIED или SQL_SENSITIVE (если SQL_ATTR_CONCURRENCY не SQL_CONCUR_READ_ONLY).|
