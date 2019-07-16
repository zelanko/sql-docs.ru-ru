---
title: Функция SQLGetEnvAttr | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLGetEnvAttr
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetEnvAttr
helpviewer_keywords:
- SQLGetEnvAttr function [ODBC]
ms.assetid: 01f4590f-427a-4280-a1c3-18de9f7d86c1
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4e3bfc22e4205657107f11b4eec145028aee6397
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67911281"
---
# <a name="sqlgetenvattr-function"></a>Функция SQLGetEnvAttr
**Соответствие стандартам**  
 Представленные версии: ODBC 3.0 стандартов соответствия: ISO-92  
  
 **Сводка**  
 **SQLGetEnvAttr** возвращает текущее значение атрибута среды.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
  
SQLRETURN SQLGetEnvAttr(  
     SQLHENV        EnvironmentHandle,  
     SQLINTEGER     Attribute,  
     SQLPOINTER     ValuePtr,  
     SQLINTEGER     BufferLength,  
     SQLINTEGER *   StringLengthPtr);  
```  
  
## <a name="arguments"></a>Аргументы  
 *EnvironmentHandle*  
 [Вход] Дескриптор среды.  
  
 *Attribute*  
 [Вход] Атрибут.  
  
 *ValuePtr*  
 [Выход] Указатель на буфер, в который возвращается текущее значение атрибута, заданного с *атрибут*.  
  
 Если *ValuePtr* имеет значение NULL, *StringLengthPtr* по-прежнему возвращает общее число байтов (за исключением символа конечное значение null для символьных данных) для возврата в буфере, на которые указывают  *ValuePtr*.  
  
 *BufferLength*  
 [Вход] Если *ValuePtr* указывает строку символов, данный аргумент должен иметь длину \* *ValuePtr*. Если \* *ValuePtr* должно быть целым числом, *BufferLength* учитывается. Если  *\*ValuePtr* строка в Юникоде (при вызове **SQLGetEnvAttrW**), *BufferLength* аргумент должен быть четным числом. Если значение атрибута не содержит строку знаков, *BufferLength* не используется.  
  
 *StringLengthPtr*  
 [Выход] Указатель на буфер, в которую будет возвращено общее число байтов (за исключением знака завершения null) для возврата в  *\*ValuePtr*. Если *ValuePtr* является указателем null, длина не возвращается. Если значение атрибута — строка символов, а также количество байтов, доступных для возврата больше или равно *BufferLength*, данные в \* *ValuePtr* усекается до  *BufferLength* минус длина знак завершения null и заканчивается нулевым байтом драйвером.  
  
## <a name="returns"></a>Возвращает  
 Значение SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA, значение SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLGetEnvAttr** возвращает значение SQL_ERROR или SQL_SUCCESS_WITH_INFO, а связанное значение SQLSTATE можно получить, вызвав **SQLGetDiagRec** с *HandleType* из SQL_ HANDLE_ENV и *обрабатывать* из *EnvironmentHandle*. В следующей таблице перечислены значения SQLSTATE, обычно возвращаемые **SQLGetEnvAttr** и объясняется каждый из них в контексте этой функции; описания SQLSTATE, возвращаемых диспетчером драйверов предшествует обозначение «(DM)». Возвращается связанный с каждого значения SQLSTATE значение SQL_ERROR, если не указано иное.  
  
|SQLSTATE|Ошибка|Описание|  
|--------------|-----------|-----------------|  
|01000|Общее предупреждение|Специфические для драйвера информационное сообщение. (Функция возвращает значение SQL_SUCCESS_WITH_INFO).|  
|01004|Усечение данных строки справа|Данные, возвращаемые в \* *ValuePtr* было усечено до быть *BufferLength* минус знак завершения null. Длина неусеченный строковое значение возвращается в **StringLengthPtr*. (Функция возвращает значение SQL_SUCCESS_WITH_INFO).|  
|HY000|Общая ошибка|Произошла ошибка, для которой было нет конкретных SQLSTATE и SQLSTATE не зависящие от реализации, который был определен. Сообщение об ошибке, возвращенные **SQLGetDiagRec** в  *\*MessageText* буфера описывает ошибку и его причины.|  
|HY001|Ошибка выделения памяти|Драйвер не удалось выделить память, необходимую для поддержки выполнения или завершения функции.|  
|HY010|Ошибка последовательности функций|(DM) **SQL_ATTR_ODBC_VERSION** еще не было задано с помощью **SQLSetEnvAttr**. Необходимо задать **SQL_ATTR_ODBC_VERSION** явным образом в том случае, если вы используете **SQLAllocHandleStd**.|  
|HY013|Ошибка управления памятью|Не удалось обработать вызов функции, так как базовые объекты памяти оказываются недоступны, возможно из-за нехватки памяти.|  
|HY092|Недопустимый атрибут/идентификатор параметра|Значение, указанное для аргумента *атрибут* недопустимо для версии ODBC, поддерживаемых драйвером.|  
|HY117|Подключение будет приостановлена из-за состояние транзакции неизвестно. Только отключиться и разрешены функции, доступные только для чтения.|(DM) Дополнительные сведения о состоянии приостановки, см. в разделе [функция SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Дополнительная возможность не реализована|Значение, указанное для аргумента *атрибут* был допустимым атрибутом среды ODBC, драйвер поддерживает используемая версия ODBC, но не поддерживается драйвером.|  
|IM001|Драйвер не поддерживает эту функцию|(DM) драйвер, соответствующий *EnvironmentHandle* не поддерживает функцию.|  
  
## <a name="comments"></a>Комментарии  
 Список атрибутов, см. в разделе [SQLSetEnvAttr](../../../odbc/reference/syntax/sqlsetenvattr-function.md). Отсутствуют атрибуты среды, относящиеся к драйверу. Если *атрибут* определяет атрибут, который возвращает строку, *ValuePtr* должен быть указателем на буфер, в котором для возврата строки. Максимальная длина строки, включая байт конечное значение null, будет *BufferLength* байт.  
  
 **SQLGetEnvAttr** можно вызвать в любое время между выделении и освобождении дескриптора среды. Все атрибуты среды, успешно установлены приложением для среды сохраняется до **SQLFreeHandle** вызывается для *EnvironmentHandle* с *HandleType*из SQL_HANDLE_ENV. Более одного дескриптора среды может находиться одновременно в ODBC 3 *.x*. Атрибут среды в одной среде не влияет на другую среду было выделено.  
  
> [!NOTE]
>  Атрибут среды SQL_ATTR_OUTPUT_NTS поддерживается соответствующих стандартам приложений. Когда **SQLGetEnvAttr** вызывается ODBC 3 *.x* диспетчера драйверов всегда возвращает SQL_TRUE для этого атрибута. SQL_ATTR_OUTPUT_NTS можно задать значение sql_true только путем вызова **SQLSetEnvAttr**.  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Возвращает значение атрибута соединения|[Функция SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
|Возвращает значение атрибута инструкции|[Функция SQLGetStmtAttr](../../../odbc/reference/syntax/sqlgetstmtattr-function.md)|  
|Присвоение атрибуту соединения|[Функция SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|  
|Задания атрибута среды|[Функция SQLSetEnvAttr](../../../odbc/reference/syntax/sqlsetenvattr-function.md)|  
|Присвоение атрибуту инструкции|[Функция SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|  
  
## <a name="see-also"></a>См. также  
 [Справочник по API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)
