---
title: "Диспетчер драйверов не | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- driver manager [ODBC], backward compatibility
- compatibility [ODBC], driver manager
- ODBC driver manager [ODBC]
- backward compatibility [ODBC], driver manager
ms.assetid: 57f65c38-d9ee-46c8-9051-128224a582c6
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 64c6fb04fe5c5c693da4982e1c12194bc7e42f98
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="what-the-driver-manager-does"></a>Назначение диспетчера драйверов
В следующей таблице представлены как ODBC 3*.x* диспетчера драйверов сопоставляет вызовы ODBC 2.* x* а ODBC 3*.x* драйверы.  
  
|Функция или<br /><br /> атрибут инструкции|Комментарии|  
|-----------------------------------------|--------------|  
|SQL_ATTR_FETCH_BOOKMARK_PTR|Указывает на закладку для использования с **SQLFetchScroll**. Ниже приведены сведения о реализации.<br /><br /> -Если приложение устанавливает это в ODBC 2. *x* драйвера ODBC 3*.x* диспетчера драйверов выполнит его кэширование. Он разыменовывает указатель и передает значение в ODBC 2. *x* драйвера в *FetchOffset* аргумент **SQLExtendedFetch** при **SQLFetchScroll** позже вызывается приложением.<br />-Когда приложение устанавливает это в ODBC 3*.x* драйвера ODBC 3*.x* диспетчера драйверов передает этот вызов к драйверу.|  
|ЗНАЧЕНИЯ SQL_ATTR_ROW_STATUS_PTR|Указывает на массив состояния строк заполненной **SQLFetch**, **SQLFetchScroll**, **SQLBulkOperations**, и **SQLSetPos**. Ниже приведены сведения о реализации.<br /><br /> -Если приложение устанавливает это в ODBC 2. *x* драйвера ODBC 3*.x* диспетчера драйверов кэширует его значение. Это значение передается в ODBC 2. *x* драйвера в *RowStatusArray* аргумент **SQLExtendedFetch** при **SQLFetchScroll** или **SQLFetch** вызывается.<br />-Когда приложение устанавливает это в ODBC 3*.x* драйвера ODBC 3*.x* диспетчера драйверов передает этот вызов к драйверу.<br />-В состоянии S6, если приложение устанавливает значения SQL_ATTR_ROW_STATUS_PTR и затем вызывает **SQLBulkOperations** (с *операции* из SQL_ADD) или **SQLSetPos** без предварительного вызова функции **SQLFetch** или **SQLFetchScroll**, SQLSTATE HY011 (атрибут нельзя установить сейчас) возвращается.|  
|SQL_ATTR_ROWS_FETCHED_PTR|Указывает на буфер, в котором **SQLFetch** и **SQLFetchScroll** возвращают число возвращаемых строк. Ниже приведены сведения о реализации.<br /><br /> -Если приложение устанавливает это в ODBC 2. *x* драйвера ODBC 3*.x* диспетчера драйверов кэширует его значение. Это значение передается в ODBC 2. *x* драйвера в *RowCountPtr* аргумент **SQLExtendedFetch** при **SQLFetch** или **SQLFetchScroll** вызывается приложением.<br />-Когда приложение устанавливает это в ODBC 3*.x* драйвера ODBC 3*.x* диспетчера драйверов передает этот вызов к драйверу.|  
|SQL_ATTR_ROW_ARRAY_SIZE|Задает размер набора строк. Ниже приведены сведения о реализации.<br /><br /> -Если приложение устанавливает это в ODBC 2. *x* драйвера ODBC 3*.x* диспетчера драйверов сопоставляет его с атрибутом SQL_ROWSET_SIZE инструкции.<br />-Когда приложение устанавливает это в ODBC 3*.x* драйвера ODBC 3*.x* диспетчера драйверов передает этот вызов к драйверу.<br />— Если приложение, работа с ODBC 3*.x* драйвер вызывает **SQLSetScrollOptions**, SQL_ROWSET_SIZE присвоено значение в *RowsetSize* аргумент Если базовый драйвер не поддерживает **SQLSetScrollOptions**.|  
|SQL_ROWSET_SIZE|Задает размер набора строк, используемых **SQLExtendedFetch** при **SQLExtendedFetch** вызывается ODBC 2*.x* приложения. Ниже приведены сведения о реализации.<br /><br /> -Если приложение задает, ODBC 3*.x* диспетчера драйверов передает этот вызов к драйверу, независимо от версии драйвера.<br />— Если приложение, работа с ODBC 2. *x* драйвер вызывает **SQLSetScrollOptions**, SQL_ROWSET_SIZE присвоено значение в **RowsetSize** аргумент.|  
|**SQLBulkOperations**|Выполняет вставки операции или update, delete или fetch операциями закладки. Ниже приведены сведения о реализации.<br /><br /> -Если приложение вызывает **SQLBulkOperations** с *операции* из SQL_ADD в ODBC 2.* x* драйвера ODBC 3*.x* диспетчера драйверов сопоставляет его **SQLSetPos** с *операции* из SQL_ADD.<br />— При работе с ODBC 2. *x* драйвер, который не поддерживает **SQLSetPos** с *операции* из SQL_ADD ODBC 3*.x* диспетчер драйверов не соответствует **SQLSetPos** с *операции* из SQL_ADD для **SQLBulkOperations** с *операции* из SQL_ADD. Это вызвано **SQLBulkOperations** не может вызываться в состоянии S7, какие в ODBC 2.* x* только состояние, в котором был **SQLSetPos** может быть вызвана.<br />-Если приложение вызывает **SQLBulkOperations** с *операции* из SQL_ADD в ODBC 2.* x* драйвера перед вызовом **SQLFetchScroll**, ODBC 3*.x* диспетчера драйверов возвращает сообщение об ошибке.|  
|**SQLExtendedFetch**|Возвращает указанный набор строк. За исключением случая, упомянутых, ODBC 3*.x* диспетчера драйверов передает вызовы **SQLExtendedFetch** к драйверу, независимо от версии драйвера.|  
|**SQLFetch**|Возвращает следующий набор строк. Ниже приведены сведения о реализации.<br /><br /> -Если приложение вызывает **SQLFetch** в ODBC 2.* x* драйвера ODBC 3*.x* диспетчера драйверов сопоставляет его **SQLExtendedFetch**. *FetchOrientation* аргумент **SQLExtendedFetch** равно SQL_FETCH_NEXT. Диспетчер драйверов использует кэшированное значение sql_attr_row_status_ptr, которое указывает атрибут инструкции для *RowStatusArray* аргумент и кэшированное значение атрибута SQL_ATTR_ROWS_FETCHED_PTR инструкции для * RowCountPtr* аргумент.<br />-3 ODBC*.x* приложения могут быть использованы смешанные вызовы **SQLFetch** и **SQLFetchScroll** в ODBC 2.* x* драйвер поскольку ODBC 3*.x* сопоставляет диспетчера драйверов **SQLFetch** для **SQLExtendedFetch** когда приложение вызывает его в ODBC 2.* x* драйвера.<br />-Если ODBC 2. *x* драйвер не поддерживает **SQLExtendedFetch**, ODBC 3*.x* диспетчер драйверов не соответствует **SQLFetch** или ** SQLFetchScroll** для **SQLExtendedFetch** когда приложение вызывает его в нем. Если приложение пытается установить SQL_ATTR_ROW_ARRAY_SIZE значение больше 1, SQLSTATE HYC00 возвращается (дополнительная возможность не реализована).<br />— Кроме для только что было отмечено, ограничения ODBC 3*.x* диспетчера драйверов передает вызовы **SQLFetch** к драйверу, независимо от версии драйвера.|  
|**SQLFetchScroll**|Возвращает указанный набор строк. Ниже приведены сведения о реализации.<br /><br /> -Если приложение вызывает **SQLFetchScroll** в ODBC 2.* x* драйвера ODBC 3*.x* диспетчера драйверов сопоставляет его **SQLExtendedFetch**. Она использует кэшированное значение sql_attr_row_status_ptr, которое указывает атрибут инструкции для *RowStatusArray* аргумент и кэшированное значение атрибута SQL_ATTR_ROWS_FETCHED_PTR инструкции для *RowCountPtr* аргумент. Если *FetchOrientation* аргумент в **SQLFetchScroll** — SQL_FETCH_BOOKMARK, он использует кэшированное значение атрибута инструкции SQL_ATTR_FETCH_BOOKMARK_PTR для *FetchOffset * аргумент и возвращает ошибку, если *FetchOffset* аргумент **SQLFetchScroll** — не равно 0.<br />-Если приложение вызывает это в ODBC 3*.x* драйвера ODBC 3*.x* диспетчера драйверов передает этот вызов к драйверу.|  
|**SQLSetPos**|Выполняет различные позиционированных операций. ODBC 3*.x* диспетчера драйверов передает вызовы **SQLSetPos** драйверу, независимо от версии драйвера.|  
|**SQLSetScrollOptions**|Когда диспетчер драйверов сопоставляет **SQLSetScrollOptions** для приложения, работа с ODBC 3*.x* драйвер, который не поддерживает **SQLSetScrollOptions**, драйвер Диспетчер задает параметр инструкции SQL_ROWSET_SIZE атрибут не SQL_ATTR_ROW_ARRAY_SIZE инструкции к *RowsetSize* аргумент в **SQLSetScrollOption**. В результате **SQLSetScrollOptions** не может использоваться приложением при их получении нескольких строк путем вызова **SQLFetch** или **SQLFetchScroll**. Он может использоваться только в том случае, если извлечение нескольких строк путем вызова **SQLExtendedFetch**.|

