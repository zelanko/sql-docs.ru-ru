---
title: Функция S'LRowCount (англ.) Документы Майкрософт
ms.custom: ''
ms.date: 07/18/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLRowCount
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLRowCount
helpviewer_keywords:
- SQLRowCount function [ODBC]
ms.assetid: 61e00a8a-9b3b-45b9-b397-7fe818822416
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2cbca03e7c3e381b803196a1bf7bb227ebeea03b
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81293374"
---
# <a name="sqlrowcount-function"></a>Функция SQLRowCount
**Соответствия**  
 Представлена версия: Соответствие стандартам ODBC 1.0: ISO 92  
  
 **Сводка**  
 **S'LRowCount** возвращает количество строк, затронутых **обновлением,** **INSERT**, или **заявление DELETE;** SQL_ADD, SQL_UPDATE_BY_BOOKMARK или SQL_DELETE_BY_BOOKMARK операции в **S'LBulkOperations;** или SQL_UPDATE или SQL_DELETE операции в **S'LSetPos**.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
  
SQLRETURN SQLRowCount(  
      SQLHSTMT   StatementHandle,  
      SQLLEN *   RowCountPtr);  
```  
  
## <a name="arguments"></a>Аргументы  
 *Обработка заявления*  
 (Вход) Ручка оператора.  
  
 *RowCountPtr*  
 (Выход) Указывает на буфер, в котором можно вернуть количество строк. Для **обновлений,** **вставканых**и DELETE-отчетов, для SQL_ADD, SQL_UPDATE_BY_BOOKMARK и SQL_DELETE_BY_BOOKMARK операций в **S'LBulkOperations,** а также для операций SQL_UPDATE или SQL_DELETE в **S'LSetPos,** значение, возвращенное в*строках RowCountPtr,* — это либо количество строк, затронутых запросом, либо -1, если количество затронутых строк недоступно. **DELETE**  
  
 При вызове **SQL_DIAG_ROW_COUNT**поле структуры **SQLBulkOperations**диагностических данных **SQLSetPos, or SQLMoreResults** в строке устанавливается SQL_DIAG_ROW_COUNT поле структуры диагностических данных, **SQLExecDirect**а количество строк кэшируется зависящим от реализации. **Значение** количества кэшированных строк возвращается. Значение количества кэшированных строк является действительным до тех пор, пока ручка оператора не будет восстановлена в подготовленном или выделенном состоянии, заявление будет перевыполнено или вызвано **s'LCloseCursor.** Обратите внимание, что если функция была вызвана с момента установки SQL_DIAG_ROW_COUNT поля, то значение, возвращенное **S'LRowCount,** может отличаться от значения в поле SQL_DIAG_ROW_COUNT, поскольку поле SQL_DIAG_ROW_COUNT сбросить на 0 любым вызовом функции.  
  
 Для других инструкций и функций драйвер \*может определить значение, возвращенное в *RowCountPtr.* Например, некоторые источники данных могут вернуть количество строк, возвращенных выпиской **SELECT** или функцией каталога, перед извлечением строк.  
  
> [!NOTE]  
>  Многие источники данных не могут вернуть количество строк в наборе результатов, прежде чем получить их; для максимальной совместимости приложения не должны полагаться на такое поведение.  
  
## <a name="returns"></a>Результаты  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **S'LRowCount** возвращается SQL_ERROR или SQL_SUCCESS_WITH_INFO, связанное с этим значение S'LSTATE можно получить, позвонив по **телефону S'LGetDiagRec** с *помощью HandleType* of SQL_HANDLE_STMT и *ручкой* *statementHandle.* В следующей таблице перечислены значения S'LSTATE, обычно возвращаемые **S'LRowCount,** и приведены в контексте этой функции. нотация "(DM)" предшествует описаниям S'LSTATEs, возвращенным менеджером драйвера. Код возврата, связанный с каждым значением S'LSTATE, является SQL_ERROR, если не указано иное.  
  
|SQLSTATE|Error|Описание|  
|--------------|-----------|-----------------|  
|01000|Общее предупреждение|Информационное сообщение, конкретное для водителя. (Функция возвращает SQL_SUCCESS_WITH_INFO.)|  
|HY000|Общая ошибка|Произошла ошибка, в соответствии с которой не было конкретного S'LSTATE и для которой не было определено конкретное осуществление СЗЛСТАТ. Сообщение об ошибке, возвращенное **S'LGetDiagRec** в * \*буфере MessageText,* описывает ошибку и ее причину.|  
|HY001|Ошибка распределения памяти|Водитель не смог выделить память, необходимую для поддержки выполнения или завершения функции.|  
|HY010|Ошибка последовательности функций|(DM) Асинхронно функция выполнения была вызвана для ручки соединения, которая связана с *StatementHandle.* Эта асинхронная функция по-прежнему исполнялась, когда была вызвана функция **S'LRowCount.**<br /><br /> (DM) **S'LExecute**, **S'LExecDirect**, или **S'LMoreResults** был вызван для *statementHandle* и вернулся SQL_PARAM_DATA_AVAILABLE. Эта функция была вызвана до того, как данные были извлечены для всех потоковых параметров.<br /><br /> (DM) Функция была вызвана до вызова **S'LExecute**, **S'LExecDirect**, **S'LBulkOperations**, или **S'LSetPos** для *statementHandle*.<br /><br /> (DM) Асинхронно выполнение функции был вызван для *StatementHandle* и по-прежнему выполнения, когда эта функция была вызвана.<br /><br /> (DM) **S'LExecute**, **S'LExecDirect**, **S'LBulkOperations**, или **S'LSetPos** был вызван для *statementHandle* и вернулся SQL_NEED_DATA. Эта функция была вызвана до отправки данных для всех параметров или столбцов данных.|  
|HY013|Ошибка управления памятью|Вызов функции не может быть обработан, поскольку основные объекты памяти не могут быть доступны, возможно, из-за низких условий памяти.|  
|HY117|Подключение приостанавливается из-за неизвестного состояния транзакции. Разрешены только отключить и прочитать только функции.|(DM) Для получения дополнительной информации о приостановленном состоянии, [см.](../../../odbc/reference/syntax/sqlendtran-function.md)|  
|HYT01|Срок истечения времени подключения|Период тайм-аута соединения истек до того, как источник данных ответил на запрос. Период тайм-аута соединения устанавливается через **S'LSetConnectAttr,** SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Драйвер не поддерживает эту функцию|(DM) Драйвер, связанный с *StatementHandle,* не поддерживает функцию.|  
  
## <a name="comments"></a>Комментарии  
 Если последняя выписка, выполненная на ручке оператора, не была **ОБНОВЛЕНИЕ,** **INSERT**, или **DELETE** заявление или если *аргумент операции* в предыдущем вызове к **S'LBulkOperations** не был SQL_ADD, SQL_UPDATE_BY_BOOKMARK или SQL_DELETE_BY_BOOKMARK, или если *аргумент операции* в предыдущем вызове на **S'LSetPos** не был SQL_UPDATE или SQL_DELETE, значение*строки RowCountPtr* определяется драйвером. Для получения дополнительной [информации см.](../../../odbc/reference/develop-app/determining-the-number-of-affected-rows.md)  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Выполнение оператора S'L|[Функция SQLExecDirect](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|Выполнение подготовленного заявления по S'L|[Функция «СЗЛВы»](../../../odbc/reference/syntax/sqlexecute-function.md)|  
  
## <a name="see-also"></a>См. также:  
 [Справка aPI ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)
