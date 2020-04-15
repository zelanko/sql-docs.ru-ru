---
title: Функция S'LGetEnvAttr Документы Майкрософт
ms.custom: ''
ms.date: 07/18/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLGetEnvAttr
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLGetEnvAttr
helpviewer_keywords:
- SQLGetEnvAttr function [ODBC]
ms.assetid: 01f4590f-427a-4280-a1c3-18de9f7d86c1
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 77cd24386a8eea6769aee59f3674b681c516d9ed
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81285314"
---
# <a name="sqlgetenvattr-function"></a>Функция SQLGetEnvAttr
**Соответствия**  
 Представлена версия: Соответствие стандартам ODBC 3.0: ISO 92  
  
 **Сводка**  
 **S'LGetEnvAttr** возвращает текущую настройку атрибута среды.  
  
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
 *Окружающая средаРучка*  
 (Вход) Ручка окружающей среды.  
  
 *Атрибут*  
 (Вход) Атрибут для извлечения.  
  
 *ValuePtr*  
 (Выход) Указатель на буфер, в котором можно вернуть текущее значение атрибута, указанное *Attribute.*  
  
 Если *ValuePtr* является NULL, *StringLengthPtr* по-прежнему возвращает общее количество байтов (за исключением символа нулевого прекращения для данных символов), доступного для возврата в буфере, на который указывает *ValuePtr.*  
  
 *BufferLength*  
 (Вход) Если *ValuePtr* указывает на строку символов, \*этот аргумент должен быть длиной *ValuePtr.* Если \* *ValuePtr* является рядом, *BufferLength* игнорируется. Если * \*ValuePtr* является строкой Unicode (при вызове **S'LGetEnvAttrW),** аргумент *BufferLength* должен быть четным числом. Если значение атрибута не является строкой символов, *BufferLength* не используется.  
  
 *СтрунныйДлинПтр*  
 (Выход) Указатель на буфер, в котором для возврата общего числа байтов (за исключением символа нулевого прекращения), доступного для возврата в * \*ValuePtr.* Если *ValuePtr* является нулевой указатель, длина не возвращается. Если значение атрибута является строкой символов, а количество байтов, доступных для \*возврата, больше или равно *BufferLength,* данные в *ValuePtr* усечены до *BufferLength* минус длина символа с нулевым прекращением и сведены на нет пилотом.  
  
## <a name="returns"></a>Результаты  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA, SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **S'LGetEnvAttr** возвращается SQL_ERROR или SQL_SUCCESS_WITH_INFO, связанная с этим стоимость S'LSTATE может быть получена, позвонив по **телефону S'LGetDiagRec** с *помощью HandleType* of SQL_HANDLE_ENV и *ручкой* *environmentHandle.* В следующей таблице перечислены значения S'LSTATE, обычно возвращаемые **S'LGetEnvAttr,** и разъясняются каждое из них в контексте этой функции; нотация "(DM)" предшествует описаниям S'LSTATEs, возвращенным менеджером драйвера. Код возврата, связанный с каждым значением S'LSTATE, является SQL_ERROR, если не указано иное.  
  
|SQLSTATE|Error|Описание|  
|--------------|-----------|-----------------|  
|01000|Общее предупреждение|Информационное сообщение, конкретное для водителя. (Функция возвращает SQL_SUCCESS_WITH_INFO.)|  
|01004|Строковые данные, правые усеченные|Данные, \*возвращенные в *ValuePtr,* были усечены как *BufferLength* минус символ нулевого прекращения. Длина непросеченного значения строки возвращается в*строке ДлинаPtr*. (Функция возвращает SQL_SUCCESS_WITH_INFO.)|  
|HY000|Общая ошибка|Произошла ошибка, в соответствии с которой не было конкретного S'LSTATE и для которой не было определено конкретное осуществление СЗЛСТАТ. Сообщение об ошибке, возвращенное **S'LGetDiagRec** в * \*буфере MessageText,* описывает ошибку и ее причину.|  
|HY001|Ошибка распределения памяти|Водитель не смог выделить память, необходимую для поддержки выполнения или завершения функции.|  
|HY010|Ошибка последовательности функций|(DM) **SQL_ATTR_ODBC_VERSION** еще не установлен ы через **S'LSetEnvAttr**. Вам не нужно устанавливать **SQL_ATTR_ODBC_VERSION** явно, если вы используете **S'LAllocHandleStd.**|  
|HY013|Ошибка управления памятью|Вызов функции не может быть обработан, поскольку основные объекты памяти не могут быть доступны, возможно, из-за низких условий памяти.|  
|HY092|Недействительный идентификатор атрибута/опциона|Значение, указанное для аргумента *Attribute,* не было действительным для версии ODBC, поддерживаемой водителем.|  
|HY117|Подключение приостанавливается из-за неизвестного состояния транзакции. Разрешены только отключить и прочитать только функции.|(DM) Для получения дополнительной информации о приостановленном состоянии, [см.](../../../odbc/reference/syntax/sqlendtran-function.md)|  
|HYC00|Дополнительная функция не реализована|Значение, указанное для аргумента *Attribute,* является допустимой атрибутом среды ODBC для версии ODBC, поддерживаемой водителем, но не поддерживается водителем.|  
|IM001|Драйвер не поддерживает эту функцию|(DM) Драйвер, соответствующий *EnvironmentHandle,* не поддерживает функцию.|  
  
## <a name="comments"></a>Комментарии  
 Список атрибутов можно [оперет.С.](../../../odbc/reference/syntax/sqlsetenvattr-function.md) Нет атрибутов среды, специфичной для драйвера. Если *атрибут* определяет атрибут, возвращающие строку, *ValuePtr* должен быть указателем буфера, в котором можно вернуть строку. Максимальная длина строки, включая байт с нулевым прекращением, будет *буферным* байтам.  
  
 **СЗЛГетЕнвТтр** может быть вызван в любое время между выделением и освобождением ручки среды. Все атрибуты среды, успешно установленные приложением для среды, сохраняются до тех пор, пока **s'LFreeHandle** не будет вызван в *EnvironmentHandle* с *помощью HandleType* of SQL_HANDLE_ENV. Несколько рукояток среды могут быть выделены одновременно в ODBC 3 *.x*. Атрибут среды на одной среде не влияет при выделении другой среды.  
  
> [!NOTE]
>  Атрибут среды SQL_ATTR_OUTPUT_NTS поддерживается приложениями, совместимыми со стандартами. При вызове **S'LGetEnvAttr** менеджер драйвера ODBC 3 *.x* всегда возвращает SQL_TRUE для этого атрибута. SQL_ATTR_OUTPUT_NTS может быть установлен на SQL_TRUE только по вызову в **S'LSetEnvAttr**.  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Возвращение параметра атрибута соединения|[Функция SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
|Возвращение атрибута оператора|[Функция SQLGetStmtAttr](../../../odbc/reference/syntax/sqlgetstmtattr-function.md)|  
|Установка атрибута соединения|[Функция SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|  
|Установка атрибута среды|[Функция SQLSetEnvAttr](../../../odbc/reference/syntax/sqlsetenvattr-function.md)|  
|Установка атрибута оператора|[Функция SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|  
  
## <a name="see-also"></a>См. также:  
 [Справка aPI ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)
