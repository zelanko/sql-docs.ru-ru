---
title: Блок и совместимость Прокручиваемые курсоры ODBC 3.x | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- compatibility [ODBC], cursors
- backward compatibility [ODBC], cursors
- SQLExtendedFetch function [ODBC], block cursors
- cursors [ODBC], compatibility issues
- SQLFetchScroll function [ODBC], block cursors
ms.assetid: 82f6cf68-cfde-4417-9788-d6382ca14bf8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b0bc45169a3c5eee2e23f581a66d5232c22e89b0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47740318"
---
# <a name="block-cursors-scrollable-cursors-and-backward-compatibility-for-odbc-3x-applications"></a>Блочные курсоры, прокручиваемые курсоры и обратная совместимость для приложений ODBC 3.x
Наличие обоих **SQLFetchScroll** и **SQLExtendedFetch** представляет сначала удалить разделить между прикладного программного интерфейса (API), которого представляет собой набор функций ODBC приложение вызывает и службу поставщика интерфейса (SPI), который представляет собой набор функций в драйвере реализованы. Это разделение необходимо учитывать, что в ODBC 3. *x*, которая использует **SQLFetchScroll**, чтобы соответствовать стандартам, а также быть совместим с ODBC 2. *x*, которая использует **SQLExtendedFetch**.  
  
 ODBC 3 *.x* API, который является набор функции приложение вызывает функцию, включает в себя **SQLFetchScroll** и связанные атрибуты инструкции. ODBC 3 *.x* SPI, которая представляет собой набор функций, драйвер реализует, включает в себя **SQLFetchScroll**, **SQLExtendedFetch**и связанные атрибуты инструкции. Поскольку ODBC не поддерживает это разделение между API и SPI формально, возможна ODBC 3 *.x* приложениям вызывать **SQLExtendedFetch** и связанные атрибуты инструкции. Тем не менее, нет причин для ODBC 3 *.x* приложений, чтобы сделать это. Дополнительные сведения об интерфейсах API и SPI см. во введении к [архитектура ODBC](../../../odbc/reference/odbc-architecture.md).  
  
 Сведения о том, как ODBC 3. *x* диспетчера драйверов сопоставляет вызовы ODBC 2. *x* и ODBC 3. *x* драйверов и какие функции и инструкции атрибуты ODBC 3. *x* драйвер должен реализовать для блока и Прокручиваемые курсоры, см. в разделе [драйвер назначение](../../../odbc/reference/appendixes/what-the-driver-does.md) в приложении G: драйвер рекомендации для обеспечения обратной совместимости.  
  
 В следующей таблице перечислены какие функции и инструкции атрибутов ODBC 3. *x* приложение должно использовать блок и Прокручиваемые курсоры. В ней также перечислены различия между ODBC 2. *x* и ODBC 3. *x* в этой области, ODBC 3. *x* приложения следует обратить внимание на совместимость с ODBC 2. *x* драйверы.  
  
|Функция или<br /><br /> атрибут инструкции|Комментарии|  
|-----------------------------------------|--------------|  
|SQL_ATTR_FETCH_BOOKMARK_PTR|Указывает на закладку для использования с **SQLFetchScroll**.<br /><br /> Когда приложение устанавливает это в ODBC 2. *x* драйвера, это должно указывать закладки фиксированной длины.|  
|ЗНАЧЕНИЯ SQL_ATTR_ROW_STATUS_PTR|Указывает на массив статусов строк заполняются **SQLFetch**, **SQLFetchScroll**, **SQLBulkOperations**, и **SQLSetPos**.<br /><br /> Если приложение задает это в ODBC 2. *x* драйвер и вызовы **SQLBulkOperation** с *операции* из SQL_ADD перед вызовом **SQLFetchScroll**,  **SQLFetch**, или **SQLExtendedFetch**, SQLSTATE HY011 (атрибут нельзя установить сейчас) возвращается.<br /><br /> Если приложение вызывает **SQLFetch** в ODBC 2. *x* драйвера, **SQLFetch** сопоставляется **SQLExtendedFetch** и поэтому возвращает значения в этом массиве.|  
|SQL_ATTR_ROWS_FETCHED_PTR|Указывает на буфер, в который **SQLFetch** и **SQLFetchScroll** возвращают число возвращаемых строк.<br /><br /> Если приложение вызывает **SQLFetch** в ODBC 2. *x* драйвера, **SQLFetch** сопоставляется **SQLExtendedFetch** и поэтому возвращает значение в этом буфере.|  
|SQL_ATTR_ROW_ARRAY_SIZE|Задает размер набора строк.<br /><br /> Если приложение вызывает **SQLBulkOperations** с *операции* из SQL_ADD в ODBC 2. *x* драйвер, SQL_ROWSET_SIZE будет использоваться для вызова, не SQL_ATTR_ROW_ARRAY_SIZE, так как вызов сопоставлен с **SQLSetPos** с *операции* из SQL_ADD, который использует SQL_ROWSET_SIZE.<br /><br /> Вызов **SQLSetPos** с *операции* из SQL_ADD или **SQLExtendedFetch** в ODBC 2. *x* драйвер использует SQL_ROWSET_SIZE.<br /><br /> Вызов **SQLFetch** или **SQLFetchScroll** в ODBC 2. *x* драйвер использует атрибут SQL_ATTR_ROW_ARRAY_SIZE.|  
|**SQLBulkOperations**|Выполняет операции вставки и закладки. Когда **SQLBulkOperations** с *операции* SQL_ADD вызывается в ODBC 2. *x* драйвера, он сопоставляется **SQLSetPos** с *операции* из SQL_ADD. Ниже приведены сведения о реализации.<br /><br /> — При работе с ODBC 2. *x* драйвера, в приложении необходимо использовать только неявно выделенные Отменить, связанные с *StatementHandle*; его не удалось выделить другой Отменить для добавления строк, из-за неявного дескриптора операций не поддерживается в ODBC 2. *x* драйвера. Приложение должно использовать **SQLBindCol** для привязки к Отменить, не **SQLSetDescField** или **SQLSetDescRec**.<br />-При вызове ODBC 3. *x* драйвера, приложение может вызвать **SQLBulkOperations** с *операции* из SQL_ADD перед вызовом **SQLFetch** или **SQLFetchScroll**. При вызове ODBC 2. *x* драйвера, приложение должно вызвать **SQLFetchScroll** перед вызовом **SQLBulkOperations** с операции SQL_ADD.|  
|**SQLFetch**|Возвращает следующий набор строк. Ниже приведены сведения о реализации.<br /><br /> — Если приложение вызывает **SQLFetch** в ODBC 2. *x* драйвера, он сопоставляется **SQLExtendedFetch**.<br />— Если приложение вызывает **SQLFetch** в ODBC 3. *x* драйвер, он возвращает число строк, заданное с помощью атрибута SQL_ATTR_ROW_ARRAY_SIZE инструкции.|  
|**SQLFetchScroll**|Возвращает указанный набор строк. Ниже приведены сведения о реализации.<br /><br /> — Если приложение вызывает **SQLFetchScroll** в ODBC 2. *x* драйвера, он возвращает SQLSTATE 01S01 (ошибка в строке) перед каждой ошибки, которая применяется к одной строки. Это делается только в том случае, поскольку ODBC 3 *.x* сопоставляет диспетчера драйверов для **SQLExtendedFetch** и **SQLExtendedFetch** возвращает этот SQLSTATE. Если приложение вызывает **SQLFetchScroll** в ODBC 3. *x* драйвера, он никогда не возвращает SQLSTATE 01S01 (ошибка в строке).<br />— Если приложение вызывает **SQLFetchScroll** в ODBC 2. *x* драйвера с *FetchOrientation* присвоено sql_fetch_bookmark аргумента, *FetchOffset* аргумент должен быть задан равным 0. SQLSTATE HYC00 (дополнительная возможность не реализована) возвращается в том случае, если выборка закладку на основе смещение предпринимается попытка с ODBC 2. *x* драйвера.|  
  
> [!NOTE]  
>  ODBC 3. *x* приложения не должны использовать **SQLExtendedFetch** или атрибут SQL_ROWSET_SIZE инструкции. Вместо этого они должны использовать **SQLFetchScroll** и инструкции атрибута SQL_ATTR_ROW_ARRAY_SIZE. ODBC 3. *x* приложения не должны использовать **SQLSetPos** с *операции* из SQL_ADD для этого следует использовать **SQLBulkOperations** с *Операции* из SQL_ADD.
