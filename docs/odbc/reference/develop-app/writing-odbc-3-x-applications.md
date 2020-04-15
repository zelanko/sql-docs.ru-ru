---
title: Написание приложений ODBC 3.x Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- application upgrades [ODBC], about upgrading
- ODBC drivers [ODBC], backward compatibility
- upgrading applications [ODBC]
- compatibility [ODBC], upgrading applications
- application upgrades [ODBC]
- upgrading applications [ODBC], about upgrading
- backward compatibility [ODBC], upgrading applications
ms.assetid: 19c54fc5-9dd6-49b6-8c9f-a38961b40a65
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3ba48d76babcaa5fcc49a541088f7c4cc349b569
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81288992"
---
# <a name="writing-odbc-3x-applications"></a>Написание приложений ODBC 3.x
Когда приложение ODBC *2.x* обновлено до ODBC *3.x,* оно должно быть написано так, что оно работает как с odBC *2.x,* так и *с драйверами 3.x.* Приложение должно включать условный код, чтобы в полной мере воспользоваться функциями ODBC *3.x.*  
  
 Атрибут среды SQL_ATTR_ODBC_VERSION должен быть установлен на SQL_OV_ODBC2. Это гарантирует, что водитель ведет себя как водитель ODBC *2.x* в отношении изменений, описанных в разделе [Поведенческие изменения.](../../../odbc/reference/develop-app/behavioral-changes.md)  
  
 Если приложение будет использовать какие-либо функции, описанные в разделе [Новые функции,](../../../odbc/reference/develop-app/new-features.md)условный код должен быть использован, чтобы определить, является ли драйвер драйверOD ABC *3.x* или ODBC *2.x.* Приложение использует **S'LGetDiagField** и **S'LGetDiagRec** для получения ODBC *3.x* S'LSTATEs при обработке ошибок на этих условных фрагментах кода. Следует рассмотреть следующие моменты о новой функциональности:  
  
-   Приложение, пострадавшее от изменения поведения размера строки, должно быть осторожным, чтобы не вызывать **S'LFetch,** когда размер массива превышает 1. Эти приложения должны заменить вызовы на **S'LExtendedFetch** звонками в **S'LSetStmtAttr,** чтобы установить атрибут SQL_ATTR_ARRAY_STATUS_PTR оператора и на **S'LFetchScroll,** чтобы у них был общий код, который работает как с драйверами ODBC *3.x,* так и с драйверами ODBC *2.x.* Поскольку **sLSetStmtAttr** с SQL_ATTR_ROW_ARRAY_SIZE будет отображены на **s'LSetStmtAttr** с SQL_ROWSET_SIZE для драйверов ODBC *2.x,* приложения могут просто установить SQL_ATTR_ROW_ARRAY_SIZE для их многофункциональных операций по извлечению.  
  
-   Большинство приложений, которые обновляются, на самом деле не подвержены изменениям в кодах S'Lstate. Для затронутых приложений они могут выполнять механический поиск и заменять их в большинстве случаев с помощью таблицы преобразования ошибок в разделе "S'LSTATE Mapping" для преобразования кодов ошибок ODBC *3.x* в коды ODBC *2.x.* Так как менеджер драйверов ODBC *3.x* будет выполнять отображение от ODBC *2.x* S'LSTATEs до ODBC *3.x* S'LSTATEs, эти писатели приложений должны только проверить ODBC *3.x* S'LSTATEs и не беспокоиться о включении ODBC *2.x* S'LSTATEs в условный код.  
  
-   Если приложение использует типы данных даты, времени и меток времени, приложение может объявить себя приложением ODBC *2.x* и использовать существующий код вместо использования кода кондиционирования.  
  
 Обновление должно также включать следующие шаги:  
  
-   Позвоните **в S'LSetEnvAttr,** прежде чем выделить соединение для установки атрибута SQL_ATTR_ODBC_VERSION среды SQL_OV_ODBC2.  
  
-   Замените все вызовы на **S'LAllocEnv,** **S'LAllocConnect**, или **S'LAllocStmt** с вызовами на **S'LAllocHandle** с соответствующим аргументом *HandleType* SQL_HANDLE_ENV, SQL_HANDLE_DBC или SQL_HANDLE_STMT.  
  
-   Замените все вызовы на **S'LFreeEnv** или **S'LFreeConnect** звонками в **S'LFreeHandle** соответствующим аргументом *HandleType* SQL_HANDLE_DBC или SQL_HANDLE_STMT.  
  
-   Замените все вызовы на **S'LSetConnectOption** вызовами на **S'LSetConnectAttr.** Если параметр, значение которого является строкой, установить аргумент *StringLength* соответствующим образом. Изменение аргумента *Attribute* с SQL_XXXX на SQL_ATTR_XXXX.  
  
-   Замените все вызовы на **S'LGetConnectOption** вызовами на **S'LGetConnectAttr.** При получении строки или двоичного атрибута установите *BufferLength* на соответствующее значение и перейдите в аргумент *струнного длины.* Изменение аргумента *Attribute* с SQL_XXXX на SQL_ATTR_XXXX.  
  
-   Замените все вызовы на **S'LSetStmtOption** звонками на **S'LSetStmtAttr.** Если параметр, значение которого является строкой, установить аргумент *StringLength* соответствующим образом. Изменение аргумента *Attribute* с SQL_XXXX на SQL_ATTR_XXXX.  
  
-   Замените все вызовы на **S'LGetStmtOption** звонками на **S'LGetStmtAttr.** При получении строки или двоичного атрибута установите *BufferLength* на соответствующее значение и перейдите в аргумент *струнного длины.* Изменение аргумента *Attribute* с SQL_XXXX на SQL_ATTR_XXXX.  
  
-   Замените все вызовы на **S'LTransact** вызовами на **S'LEndTran.** Если наиболее допустимой ручкой в вызове **S'LTransact** является ручка среды, аргумент *handleType* SQL_HANDLE_ENV должен использоваться в вызове **S'LEndTran** с соответствующим аргументом *«Ручка».* Если наиболее правильной действительной ручкой в вашем вызове **S'LTransact** является ручка соединения, *аргументType* SQL_HANDLE_DBC должен быть использован в вызове **S'LEndTran** с соответствующим аргументом *Ручка.*  
  
-   Замените все вызовы на **S'LColAttributes вызовами** на **S'LColAttributes.** Если аргумент *FieldIdentifier* является SQL_COLUMN_PRECISION, SQL_COLUMN_SCALE или SQL_COLUMN_LENGTH, не изменяйте ничего, кроме названия функции. Если нет, измените *FieldIdentifier* с SQL_COLUMN_XXXX на SQL_DESC_XXXX. Если *FieldIdentifier* является SQL_DESC_CONCISE_TYPE а тип данных — типом данных по дате, измените на соответствующий тип данных ODBC *3.x.*  
  
-   При использовании курсоров блоков, прокрутки курсоров или и того, и другого, приложение делает следующее:  
  
    -   Устанавливает размер рядового набора, тип курсора и курсор, параллелировая с помощью **S'LSetStmtAttr.**  
  
    -   Вызывает **sLSetStmtAttr,** чтобы установить SQL_ATTR_ROW_STATUS_PTR, чтобы указать на массив записей о состоянии.  
  
    -   Вызывает **S'LSetStmtAttr,** чтобы установить SQL_ATTR_ROWS_FETCHED_PTR, чтобы указать на S'LINTEGER.  
  
    -   Выполняет требуемые привязки и выполняет выписку s'L.  
  
    -   Вызывает **S'LFetchScroll** в цикле, чтобы получить строки и перемещаться в наборе результатов.  
  
    -   Если оно хочет получить закладку, приложение вызывает **S'LSetStmtAttr,** чтобы установить SQL_ATTR_FETCH_BOOKMARK_PTR переменной, которая будет содержать закладку для строки, которую он хочет получить, и вызывает **S'LFetchScroll** с аргументом *FetchOrientation* SQL_FETCH_BOOKMARK.  
  
-   При использовании массивов параметров приложение делает следующее:  
  
    -   Вызывает **sLSetStmtAttr,** чтобы установить SQL_ATTR_PARAMSET_SIZE атрибутом размер массива параметров.  
  
    -   Вызывает **sLSetStmtAttr,** чтобы установить SQL_ATTR_ROWS_PROCESSED_PTR, чтобы указать на внутреннюю переменную UDWORD.  
  
    -   Выполняет подготовку, связывание и выполнение операций по мере необходимости.  
  
    -   Если выполнение по какой-либо причине останавливается (например, SQL_NEED_DATA), он может найти "текущий" ряд параметров, проинспектируя место, на что указывает SQL_ATTR_ROWS_PROCESSED_PTR.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Сопоставление замещающих функций для обеспечения обратной совместимости приложений](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md)  
  
-   [Вызов SQLCloseCursor](../../../odbc/reference/develop-app/calling-sqlclosecursor.md)  
  
-   [Вызов SQLGetDiagField](../../../odbc/reference/develop-app/calling-sqlgetdiagfield.md)  
  
-   [Вызов SQLSetPos](../../../odbc/reference/develop-app/calling-sqlsetpos.md)  
  
-   [Операции с библиотекой курсоров](../../../odbc/reference/develop-app/cursor-library-operations.md)  
  
-   [Сопоставление типов сведений атрибутов1 курсора](../../../odbc/reference/develop-app/mapping-the-cursor-attributes1-information-types.md)  
  
-   [SQL_NO_DATA](../../../odbc/reference/develop-app/sql-no-data.md)
