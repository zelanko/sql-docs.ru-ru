---
title: "Блок и совместимости Прокручиваемые курсоры ODBC 3.x | Документы Microsoft"
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
- compatibility [ODBC], cursors
- backward compatibility [ODBC], cursors
- SQLExtendedFetch function [ODBC], block cursors
- cursors [ODBC], compatibility issues
- SQLFetchScroll function [ODBC], block cursors
ms.assetid: 82f6cf68-cfde-4417-9788-d6382ca14bf8
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 56543f0de0d95bad6fa85fc415dddd7da58f3667
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="block-cursors-scrollable-cursors-and-backward-compatibility-for-odbc-3x-applications"></a>Блочные курсоры, обратная совместимость для приложений ODBC 3.x и Прокручиваемые курсоры
На наличие **SQLFetchScroll** и **SQLExtendedFetch** представляет первый clear разбиения в ODBC между приложения программный интерфейс (API), которая представляет собой набор функций приложение вызывает и служба поставщика интерфейса (SPI), которая представляет собой набор функций в драйвере реализованы. Это разделение необходимо учитывать, что в ODBC 3. *x*, которая использует **SQLFetchScroll**, чтобы выровнять стандартам и совместимость с ODBC 2. *x*, которая использует **SQLExtendedFetch**.  
  
 ODBC 3*.x* API, который является набор функций приложение вызывает функцию, включает **SQLFetchScroll** и связанных с ними атрибуты инструкции. ODBC 3*.x* SPI, которая представляет собой набор функций, драйвер реализует, включает в себя **SQLFetchScroll**, **SQLExtendedFetch**и связанных с ними атрибуты инструкции. Поскольку ODBC не поддерживает это разделение между API и SPI формально, то возможна ODBC 3*.x* приложения, вызывающие **SQLExtendedFetch** и связанных с ними атрибуты инструкции. Тем не менее, нет причин для ODBC 3*.x* приложения для этого. Дополнительные сведения об API-интерфейсы и SPI см. во введении к [архитектура ODBC](../../../odbc/reference/odbc-architecture.md).  
  
 Сведения о том, как ODBC 3. *x* диспетчера драйверов сопоставляет вызовы ODBC 2. *x* и ODBC 3. *x* драйверов, а также какие функции и инструкции атрибуты ODBC 3. *x* драйвер должен реализовать для блока и Прокручиваемые курсоры см. в разделе [драйвер назначение](../../../odbc/reference/appendixes/what-the-driver-does.md) в приложении G: драйвер рекомендации для обеспечения обратной совместимости.  
  
 В следующей таблице перечислены какие функции и инструкции атрибутов ODBC 3. *x* приложение должно использовать блок и Прокручиваемые курсоры. На ней также указаны различия между ODBC 2. *x* и ODBC 3. *x* в этой области, ODBC 3. *x* приложений следует иметь в виду для обеспечения совместимости с ODBC 2. *x* драйверы.  
  
|Функция или<br /><br /> атрибут инструкции|Комментарии|  
|-----------------------------------------|--------------|  
|SQL_ATTR_FETCH_BOOKMARK_PTR|Указывает на закладку для использования с **SQLFetchScroll**.<br /><br /> Когда приложение устанавливает это в ODBC 2. *x* драйвера, это должен указывать на закладку фиксированной длины.|  
|ЗНАЧЕНИЯ SQL_ATTR_ROW_STATUS_PTR|Указывает на массив состояния строк заполненной **SQLFetch**, **SQLFetchScroll**, **SQLBulkOperations**, и **SQLSetPos**.<br /><br /> Если приложение устанавливает это в ODBC 2. *x* драйвер и вызовы **SQLBulkOperation** с *операции* из SQL_ADD перед вызовом **SQLFetchScroll**,  **SQLFetch**, или **SQLExtendedFetch**, SQLSTATE HY011 (атрибут нельзя установить сейчас) возвращается.<br /><br /> Если приложение вызывает **SQLFetch** в ODBC 2. *x* драйвера, **SQLFetch** сопоставляется **SQLExtendedFetch** и поэтому возвращает значения в этом массиве.|  
|SQL_ATTR_ROWS_FETCHED_PTR|Указывает на буфер, в котором **SQLFetch** и **SQLFetchScroll** возвращают число возвращаемых строк.<br /><br /> Если приложение вызывает **SQLFetch** в ODBC 2. *x* драйвера, **SQLFetch** сопоставляется **SQLExtendedFetch** и поэтому возвращает значение в этом буфере.|  
|SQL_ATTR_ROW_ARRAY_SIZE|Задает размер набора строк.<br /><br /> Если приложение вызывает **SQLBulkOperations** с *операции* из SQL_ADD в ODBC 2. *x* драйвер SQL_ROWSET_SIZE будет использоваться для вызова SQL_ATTR_ROW_ARRAY_SIZE, так как вызов сопоставляется **SQLSetPos** с *операции* из SQL_ADD, который использует SQL_ROWSET_SIZE.<br /><br /> Вызов **SQLSetPos** с *операции* из SQL_ADD или **SQLExtendedFetch** в ODBC 2. *x* драйвер использует SQL_ROWSET_SIZE.<br /><br /> Вызов **SQLFetch** или **SQLFetchScroll** в ODBC 2. *x* драйвер использует SQL_ATTR_ROW_ARRAY_SIZE.|  
|**SQLBulkOperations**|Выполняет операции insert и закладки. Когда **SQLBulkOperations** с *операции* SQL_ADD вызывается в ODBC 2. *x* драйвера, он сопоставляется **SQLSetPos** с *операции* из SQL_ADD. Ниже приведены сведения о реализации.<br /><br /> — При работе с ODBC 2. *x* драйвера, приложение должно использовать неявно выделенном Отменить, связанные с *StatementHandle*; его не удается выделить другой Отменить для добавления строк, из-за явной дескриптора операций не поддерживается в ODBC 2. *x* драйвера. Приложение должно использовать **SQLBindCol** для привязки к Отменить, не **SQLSetDescField** или **SQLSetDescRec**.<br />-При вызове ODBC 3. *x* драйвера, приложение может вызвать **SQLBulkOperations** с *операции* из SQL_ADD перед вызовом **SQLFetch** или **SQLFetchScroll**. При вызове ODBC 2. *x* драйвера, приложение должно вызвать **SQLFetchScroll** перед вызовом **SQLBulkOperations** с операцией SQL_ADD.|  
|**SQLFetch**|Возвращает следующий набор строк. Ниже приведены сведения о реализации.<br /><br /> -Если приложение вызывает **SQLFetch** в ODBC 2. *x* драйвера, он сопоставляется **SQLExtendedFetch**.<br />-Если приложение вызывает **SQLFetch** в ODBC 3. *x* драйвера, возвращает число строк, заданное с помощью атрибута SQL_ATTR_ROW_ARRAY_SIZE инструкции.|  
|**SQLFetchScroll**|Возвращает указанный набор строк. Ниже приведены сведения о реализации.<br /><br /> -Если приложение вызывает **SQLFetchScroll** в ODBC 2. *x* драйвера, она возвращает SQLSTATE 01S01 (ошибка в строке) перед каждой ошибки, который относится к одной строки. Это делается только потому, что ODBC 3*.x* диспетчера драйверов сопоставляет этот параметр, чтобы **SQLExtendedFetch** и **SQLExtendedFetch** возвращает этот SQLSTATE. Если приложение вызывает **SQLFetchScroll** в ODBC 3. *x* драйвера, никогда не возвращает SQLSTATE 01S01 (ошибка в строке).<br />-Если приложение вызывает **SQLFetchScroll** в ODBC 2. *x* драйвера с *FetchOrientation* значение SQL_FETCH_BOOKMARK, *FetchOffset* аргумента должно быть равно 0. SQLSTATE HYC00 (дополнительная возможность не реализована) возвращается при попытке выборки на основе смещение закладки с ODBC 2. *x* драйвера.|  
  
> [!NOTE]  
>  ODBC 3. *x* приложения не должны использовать **SQLExtendedFetch** или атрибут SQL_ROWSET_SIZE инструкции. Вместо этого используйте **SQLFetchScroll** и атрибут SQL_ATTR_ROW_ARRAY_SIZE инструкции. ODBC 3. *x* приложения не должны использовать **SQLSetPos** с *операции* из SQL_ADD, но следует использовать **SQLBulkOperations** с *Операции* из SQL_ADD.

