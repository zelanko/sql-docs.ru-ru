---
title: Функция S'LColAttribute (англ.) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLColAttribute
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLColAttribute
helpviewer_keywords:
- SQLColAttribute function [ODBC]
ms.assetid: 8c45c598-cb01-4789-a571-e93619a18ed9
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c94de3dfc7036277f8be56c401326cdab07a9606
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301294"
---
# <a name="sqlcolattribute-function"></a>Функция SQLColAttribute
**Соответствия**  
 Представлена версия: Соответствие стандартам ODBC 3.0: ISO 92  
  
 **Сводка**  
 В наборе результатов **sLColAttribute** возвращает информацию о дескрипторе для столбца. Информация о дескрипторе возвращается в виде строки символов, значения, зависящей от дескриптора, или целых значений.  
  
> [!NOTE]  
>  Для получения дополнительной информации о том, что менеджер драйверов карты эту функцию, когда ODBC 3. *приложение x* работает с ODBC 2. *х* драйвер, см [Отображение функции замены для обратной совместимости приложений.](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
  
SQLRETURN SQLColAttribute (  
      SQLHSTMT        StatementHandle,  
      SQLUSMALLINT    ColumnNumber,  
      SQLUSMALLINT    FieldIdentifier,  
      SQLPOINTER      CharacterAttributePtr,  
      SQLSMALLINT     BufferLength,  
      SQLSMALLINT *   StringLengthPtr,  
      SQLLEN *        NumericAttributePtr);  
```  
  
## <a name="arguments"></a>Аргументы  
 *Обработка заявления*  
 (Вход) Ручка оператора.  
  
 *ColumnNumber*  
 (Вход) Число записей в IRD, из которого должно быть извлечено значение поля. Этот аргумент соответствует количеству столбцов данных результата, заказанных последовательно в увеличении порядка столбца, начиная с 1. Столбцы можно описать в любом порядке.  
  
 В этом аргументе может быть указан апогнивей 0, но все значения, за исключением SQL_DESC_TYPE и SQL_DESC_OCTET_LENGTH, вернут неопределенные значения.  
  
 *FieldIdentifier*  
 (Вход) Ручка дескриптора. Эта ручка определяет, какое поле в IRD следует запрашивать (например, SQL_COLUMN_TABLE_NAME).  
  
 *CharacterAttributePtr*  
 (Выход) Указатель на буфер, в котором можно вернуть значение в поле *FieldIdentifier* строки *ColumnNumber* IRD, если поле является строкой символов. В противном случае поле не используется.  
  
 Если *CharacterAttributePtr* является NULL, *StringLengthPtr* по-прежнему возвращает общее количество байтов (за исключением символа нулевого прекращения для данных символов), доступного для возврата в буфере, на который указывает *CharacterAttributePtr.*  
  
 *BufferLength*  
 (Вход) Если *FieldIdentifier* является полем, определяемым ODBC, а *CharacterAttributePtr* указывает \*на строку символов или бинарный буфер, этот аргумент должен быть длиной *CharacterAttributePtr.* Если *FieldIdentifier* является полем, \*определяемым ODBC, а *CharacterAttribute*Ptr — бесседом, это поле игнорируется. Если * \*CharacterAttributePtr* является строкой Unicode (при вызове **S'LColAttributeW),** аргумент *BufferLength* должен быть четным числом. Если *FieldIdentifier* является полем, определяемым драйвером, приложение указывает на характер поля менеджеру драйвера, установив аргумент *BufferLength.* *BufferLength* может иметь следующие значения:  
  
-   Если *CharacterAttributePtr* является указателем на указатель, *BufferLength* должен иметь значение SQL_IS_POINTER.  
  
-   Если *CharacterAttributePtr* является указателем на строку символов, *BufferLength* — это длина буфера.  
  
-   Если *CharacterAttributePtr* является указателем на двоичный буфер, приложение помещает результат SQL_LEN_BINARY_ATTR *(длина)* макроса в *BufferLength*. Это ставит отрицательное значение в *BufferLength*.  
  
-   Если *CharacterAttributePtr* является указателем на тип данных с фиксированной длиной, *BufferLength* должен быть одним из следующих: SQL_IS_INTEGER, SQL_IS_UNINTEGER, SQL_SMALLINT или S'LUSMALLINT.  
  
 *СтрунныйДлинПтр*  
 (Выход) Указатель на буфер, в котором можно вернуть общее количество байтов (за исключением байт-ра-на-арудля для данных о персонажах), доступного для возврата в*характереАтрибут.*  
  
 Для данных о персонажах, если количество байтов, доступных для возврата, \*больше или равно *Буферной Длине,* информация о дескрипторе в *CharacterAttributePtr* усечена до *BufferLength* минус длина символа с нулевым прекращением и сведена к нулю водителю.  
  
 Для всех других типов данных значение *BufferLength* игнорируется, и драйвер предполагает, что размер*characterAttributePtr* составляет 32 бита.  
  
 *Числоатрибутов*  
 (Выход) Указатель на целый буфер, в котором можно вернуть значение в поле *FieldIdentifier* строки *ColumnNumber* IRD, если поле является типом числическом дескриптора, например SQL_DESC_COLUMN_LENGTH. В противном случае поле не используется. Обратите внимание, что некоторые драйверы могут писать только нижний 32-битный или 16-битный буфер и оставлять бит более высокого порядка без изменений. Таким образом, приложения должны инициализировать значение до 0, прежде чем вызывать эту функцию.  
  
## <a name="returns"></a>Результаты  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 При возврате **SQL_ERROR** или SQL_SUCCESS_WITH_INFO, связанные с s'LSTATE, связанные с s'LSTATE, могут быть получены по телефону **s'LGetDiagRec** с *помощью HandleType* of SQL_HANDLE_STMT и *ручки* *statementHandle.* В следующей таблице перечислены значения S'LSTATE, обычно возвращаемые **S'LColAttribute,** и разъясняются каждое из них в контексте этой функции; нотация "(DM)" предшествует описаниям S'LSTATEs, возвращенным менеджером драйвера. Код возврата, связанный с каждым значением S'LSTATE, является SQL_ERROR, если не указано иное.  
  
|SQLSTATE|Error|Описание|  
|--------------|-----------|-----------------|  
|01000|Общее предупреждение|Информационное сообщение, конкретное для водителя. (Функция возвращает SQL_SUCCESS_WITH_INFO.)|  
|01004|Строковые данные, правые усеченные|Буфер \* *CharacterAttributePtr* не был достаточно большим, чтобы вернуть все значение строки, поэтому значение строки было усечено. Длина непросеченного значения строки возвращается в*строке ДлинаPtr*. (Функция возвращает SQL_SUCCESS_WITH_INFO.)|  
|07005|Подготовленное заявление не является *спецификацией курсора*|Заявление, связанное с *statementHandle,* не вернуло набор результатов, и *FieldIdentifier* не был SQL_DESC_COUNT. Не было никаких столбцов для описания.|  
|07009|Недействительный индекс дескриптора|(DM) Значение, указанное для *ColumnNumber,* было равен 0, а атрибут SQL_ATTR_USE_BOOKMARKS оператора был SQL_UB_OFF.<br /><br /> Значение, указанное для аргумента *ColumnNumber,* превышало количество столбцов в наборе результатов.|  
|HY000|Общая ошибка|Произошла ошибка, в соответствии с которой не было конкретного S'LSTATE и для которой не было определено конкретное осуществление СЗЛСТАТ. Сообщение об ошибке, возвращенное **S'LGetDiagField** из структуры диагностических данных, описывает ошибку и ее причину.|  
|HY001|Ошибка распределения памяти|Водитель не смог выделить память, необходимую для поддержки выполнения или завершения функции.|  
|HY008|Operation canceled|Асинхронная обработка была включена для *StatementHandle*. Функция была вызвана, и перед завершением выполнения, **S'LCancel** или **S'LКансортхлик** был вызван на *StatementHandle*. Затем функция была вызвана снова на *StatementHandle*.<br /><br /> Функция была вызвана, и перед завершением выполнения, **S'LCancel** или **S'LКансортхливнейра** был вызван на *StatementHandle* из другого потока в многопоточном приложении.|  
|HY010|Ошибка последовательности функций|(DM) Асинхронно функция выполнения была вызвана для ручки соединения, которая связана с *StatementHandle.* Эта аинхронная функция по-прежнему исполнялась, когда был вызван S'LColAttribute.<br /><br /> (DM) **S'LExecute**, **S'LExecDirect**, или **S'LMoreResults** был вызван для *statementHandle* и вернулся SQL_PARAM_DATA_AVAILABLE. Эта функция была вызвана до того, как данные были извлечены для всех потоковых параметров.<br /><br /> (DM) Функция была вызвана до вызова **S'LPrepare**, **S'LExecDirect**, или функции каталога для *StatementHandle*.<br /><br /> (DM) Асинхронно выполнение функции (не этот) был вызван для *StatementHandle* и по-прежнему выполнения, когда эта функция была вызвана.<br /><br /> (DM) **S'LExecute**, **S'LExecDirect**, **S'LBulkOperations**, или **S'LSetPos** был вызван для *statementHandle* и вернулся SQL_NEED_DATA. Эта функция была вызвана до отправки данных для всех параметров или столбцов данных.|  
|HY013|Ошибка управления памятью|Вызов функции не может быть обработан, поскольку основные объекты памяти не могут быть доступны, возможно, из-за низких условий памяти.|  
|HY090|Недействительная длина строки или буфера|(DM) * \*CharacterAttributePtr* — это строка для персонажей, а *BufferLength* был менее 0, но не равен SQL_NTS.|  
|HY091|Идентификатор полей недействительных дескрипторов|Значение, указанное для аргумента *FieldIdentifier,* не является одним из определенных значений и не является значением, определяемым реализацией.|  
|HY117|Подключение приостанавливается из-за неизвестного состояния транзакции. Разрешены только отключить и прочитать только функции.|(DM) Для получения дополнительной информации о приостановленном состоянии, [см.](../../../odbc/reference/syntax/sqlendtran-function.md)|  
|HYC00|Водитель не способен|Значение, указанное для аргумента *FieldIdentifier,* не было поддержано водителем.|  
|HYT01|Срок истечения времени подключения|Период тайм-аута соединения истек до того, как источник данных ответил на запрос. Период тайм-аута соединения устанавливается через **S'LSetConnectAttr,** SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Драйвер не поддерживает эту функцию|(DM) Драйвер, связанный с *StatementHandle,* не поддерживает функцию.|  
|IM017|Опрос отключен в асинхронном режиме уведомления|Всякий раз, когда используется модель уведомления, опрос отключается.|  
|IM018|Для завершения предыдущей асинхронной операции на этой ручке не был вызван **S'LCompleteAsync.**|Если предыдущий вызов функции на ручке возвращается SQL_STILL_EXECUTING и если режим уведомления включен, **s'LCompleteAsync** должен быть вызван на ручку, чтобы сделать пост-обработку и завершить операцию.|  
  
 При вызове после **s'LPrepare** и перед **s'LExecute,** **S'LColAttribute** может вернуть любой S'LSTATE, которые могут быть возвращены **S'LPrepare** или **S'LExecute**, в зависимости от того, когда источник данных оценивает заявление S'L, связанное с *StatementHandle.*  
  
 По причинам производительности приложение не должно вызывать **S'LColAttribute** перед выполнением оператора.  
  
## <a name="comments"></a>Комментарии  
 Для получения информации о том, как приложения [Result Set Metadata](../../../odbc/reference/develop-app/result-set-metadata.md)используют информацию, возвращенную **S'LColAttribute,** см.  
  
 **S'LColAttribute** возвращает \*информацию либо в \* *NumericAttributePtr,* либо в *CharacterAttributePtr*. Информация integer \*возвращается в *NumericAttributePtr* в качестве значения S'LLEN; все остальные форматы информации \*возвращаются в *CharacterAttributePtr*. Когда информация \*возвращается в *NumericAttributePtr*, драйвер игнорирует *CharacterAttributePtr*, *BufferLength*и *StringLengthPtr*. При возврате \*информации в *CharacterAttributePtr*драйвер игнорирует *NumericAttributePtr.*  
  
 **SLColAttribute** возвращает значения из полей дескриптора IRD. Функция вызывается с помощью ручки оператора, а не дескриптора. Значения, возвращенные **S'LColAttribute** для значений *FieldIdentifier,* перечисленных позднее в этом разделе, также могут быть получены, позвонив по **s'LGetDesccField** с соответствующей рукояткой IRD.  
  
 В настоящее время определенные полей дескриптора, версия ODBC, в которой они были введены, и аргументы, в которых информация возвращается для них показаны позже в этом разделе; драйверы могут определять больше типов дескрипторов, чтобы воспользоваться преимуществами различных источников данных.  
  
 ODBC 3. *x* драйвер должен вернуть значение для каждого из полей дескриптора. Если поле дескриптора не применяется к драйверу или источнику данных, и если не указано иное, драйвер возвращает 0 в \* *StringLengthPtr* или пустую строку в*характереАтрибут.*  
  
## <a name="backward-compatibility"></a>Backward Compatibility  
 ODBC 3. *х* функция **S'LColAttribute** заменяет устаревшую ODBC 2. *х* функция **S'LColАтрибуты**. При отображении **S'LColAttributes** на **S'LColAttribute** (когда ODBC 2.* приложение x* работает с ODBC 3. *x* драйвера) или отображение **S'LColAttributes** на **S'LColAttributes** (когда ODBC 3.* приложение x* работает с ODBC 2. *x* driver), менеджер драйвера либо передает значение *FieldIdentifier,* отображает его на новое значение, либо возвращает ошибку, следующим образом:  
  
> [!NOTE]  
>  Префикс, используемый в значениях *FieldIdentifier* в ODBC 3. *x* был изменен с того, что используется в ODBC 2. *x*. Новая приставка "SQL_DESC"; старая приставка была "SQL_COLUMN".  
  
-   Если **#define** значение ODBC 2. *x* *FieldIdentifier* такой же, как **и #define** значение ODBC 3. *x* *FieldIdentifier*, значение в вызове функции только что пройдено.  
  
-   **Значения #define** ODBC 2. *x* *FieldIdentifiers* SQL_COLUMN_LENGTH, SQL_COLUMN_PRECISION и SQL_COLUMN_SCALE отличаются от **значений #define** ODBC 3. *x* *ПолевыеиSQL_DESC_PRECISION,* SQL_DESC_SCALE и SQL_DESC_LENGTH. ODBC 2. *x* водителю нужна только поддержка ODBC 2. *значения x.* ODBC 3. *драйвер x* должен поддерживать значения "SQL_COLUMN" и "SQL_DESC" для этих трех *полевых идентификаторов.* Эти значения различны, потому что точность, масштаб и длина определяются по-разному в ODBC 3. *x,* чем они были в ODBC 2. *x*. Для получения дополнительной информации [см. Размер столбца, десятичные цифры, длина передачи Octet и размер дисплея](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md).  
  
-   Если **#define** значение ODBC 2. *x* *FieldIdentifier* отличается от **#define** стоимости ODBC 3. *x* *FieldIdentifier*, как это происходит со значениями COUNT, NAME и NULLABLE, значение в вызове функции отображается к соответствующему значению. Например, SQL_COLUMN_COUNT отображается до SQL_DESC_COUNT, а SQL_DESC_COUNT отображается до SQL_COLUMN_COUNT, в зависимости от направления отображения.  
  
-   Если *FieldIdentifier* является новым значением в ODBC 3. *x,* для которого не было соответствующего значения в ODBC 2. *x,* он не будет отображен, когда ODBC 3. *приложение x* использует его в вызове на **s'LColAttribute** в ODBC 2. *x* драйвер, и вызов вернет S'LSTATE HY091 (идентификатор полей недействительных дескрипторов).  
  
 В следующей таблице перечислены типы дескрипторов, возвращенные **S'LColAttribute.** Тип для значений *NumericAttributePtr* — **это S'LLEN. \* **  
  
|*FieldIdentifier*|Сведения<br /><br /> вернулся в|Описание|  
|-----------------------|---------------------------------|-----------------|  
|SQL_DESC_AUTO_UNIQUE_VALUE (ODBC 1.0)|*Числоатрибутов*|SQL_TRUE, если столбец является столбцом аутоинкредментации.<br /><br /> SQL_FALSE, если столбец не является столбцом аутоинкредментации или не является числовым.<br /><br /> Это поле допустимо только для столбцов типа численных данных. Приложение может вставлять значения в строку, содержащую столбец аутоинкреации, но обычно не может обновлять значения в столбце.<br /><br /> Когда вставка сделана в колонку аутоинкремации, уникальное значение вставляется в столбец во время вставки. Приращение не определено, но является источником данных. Приложение не должно предполагать, что столбец аутоинкреации начинается в какой-либо конкретной точке или приращения какой-либо конкретной стоимости.|  
|SQL_DESC_BASE_COLUMN_NAME (ODBC 3.0)|*CharacterAttributePtr*|Название базовой колонки для столбца набора результата. Если имя базового столбца не существует (как в случае столбцов, которые являются выражениями), то эта переменная содержит пустую строку.<br /><br /> Эта информация возвращается из SQL_DESC_BASE_COLUMN_NAME области записи IRD, которая является полем только для чтения.|  
|SQL_DESC_BASE_TABLE_NAME (ODBC 3.0)|*CharacterAttributePtr*|Название базовой таблицы, содержащей столбец. Если имя базовой таблицы не может быть определено или не применимо, то эта переменная содержит пустую строку.<br /><br /> Эта информация возвращается из SQL_DESC_BASE_TABLE_NAME области записи IRD, которая является полем только для чтения.|  
|SQL_DESC_CASE_SENSITIVE (ODBC 1.0)|*Числоатрибутов*|SQL_TRUE если столбец рассматривается как чувствительный к случаям для сопоставления и сравнения.<br /><br /> SQL_FALSE если столбец не рассматривается как чувствительный к случаям для сопоставления и сравнения или не характерен.|  
|SQL_DESC_CATALOG_NAME (ODBC 2.0)|*CharacterAttributePtr*|Каталог таблицы, содержащий столбец. Возвратное значение определяется реализацией, если столбец является выражением или если столбец является частью представления. Если источник данных не поддерживает каталоги или имя каталога не может быть определено, возвращается пустая строка. Это поле записи VARCHAR не ограничено 128 символами.|  
|SQL_DESC_CONCISE_TYPE (ODBC 1.0)|*Числоатрибутов*|Краткий тип данных.<br /><br /> Для типов дат времени и интервальных данных это поле возвращает краткий тип данных; например, SQL_TYPE_TIME или SQL_INTERVAL_YEAR. (Для получения дополнительной информации смотрите [идентификаторы и дескрипторы типов данных](../../../odbc/reference/appendixes/data-type-identifiers-and-descriptors.md) в приложении D: Типы данных.)<br /><br /> Эта информация возвращается из SQL_DESC_CONCISE_TYPE области записи IRD.|  
|SQL_DESC_COUNT (ODBC 1.0)|*Числоатрибутов*|Количество столбцов, доступных в наборе результатов. Это возвращает 0, если в наборе результатов нет столбцов. Значение в аргументе *ColumnNumber* игнорируется.<br /><br /> Эта информация возвращается из SQL_DESC_COUNT заголовка IRD.|  
|SQL_DESC_DISPLAY_SIZE (ODBC 1.0)|*Числоатрибутов*|Максимальное количество символов, необходимых для отображения данных из столбца. Для получения дополнительной информации о размере дисплея [в](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) приложении D: Типы данных см.|  
|SQL_DESC_FIXED_PREC_SCALE (ODBC 1.0)|*Числоатрибутов*|SQL_TRUE если столбец имеет фиксированную точность и ненулевой масштаб, специфичный для исходных данных.<br /><br /> SQL_FALSE, если столбец не имеет фиксированной точности и ненулевой шкалы, специфичный для исходных данных.|  
|SQL_DESC_LABEL (ODBC 2.0)|*CharacterAttributePtr*|Метка столбца или название. Например, столбец под названием EmpName может быть помечен как имя сотрудника или может быть помечен псевдонимом.<br /><br /> Если столбец не имеет метки, имя столбца возвращается. Если столбец не помечен и неназван, возвращается пустая строка.|  
|SQL_DESC_LENGTH (ODBC 3.0)|*Числоатрибутов*|Числовое значение, которое является либо максимальной, либо фактической длиной символов строки символов, либо типом двоичных данных. Это максимальная длина символов для типа данных с фиксированной длиной или фактическая длина символов для типа данных с переменной длиной. Его значение всегда исключает байт с нулевым прекращением, который завершает строку символа.<br /><br /> Эта информация возвращается из SQL_DESC_LENGTH области записи IRD.<br /><br /> Для получения дополнительной информации о длине см. [Размер столбца, десятичные цифры, длина переноса Octet и размер дисплея](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) в приложении D: Типы данных.|  
|SQL_DESC_LITERAL_PREFIX (ODBC 3.0)|*CharacterAttributePtr*|Это поле записи VARCHAR (128) содержит символ или символы, которые драйвер распознает в качестве приставки для буквального этого типа данных. Это поле содержит пустую строку для типа данных, для которой буквальная приставка не применима. Для получения дополнительной информации, см [Литературные префиксы и суффиксы](../../../odbc/reference/develop-app/literal-prefixes-and-suffixes.md).|  
|SQL_DESC_LITERAL_SUFFIX (ODBC 3.0)|*CharacterAttributePtr*|Это поле записи VARCHAR (128) содержит символ или символы, которые водитель распознает в качестве суффикса для буквального этого типа данных. Это поле содержит пустую строку для типа данных, для которой буквальный суффикс не применим. Для получения дополнительной информации, см [Литературные префиксы и суффиксы](../../../odbc/reference/develop-app/literal-prefixes-and-suffixes.md).|  
|SQL_DESC_LOCAL_TYPE_NAME (ODBC 3.0)|*CharacterAttributePtr*|Это поле записи VARCHAR(128) содержит любое локализованное (родной язык) имя типа данных, которое может отличаться от обычного имени типа данных. Если локализованного имени нет, возвращается пустая строка. Это поле предназначено только для отображения. Набор символов строки зависит от локально-зависимого и, как правило, является набором символов сервера по умолчанию.|  
|SQL_DESC_NAME (ODBC 3.0)|*CharacterAttributePtr*|Столбец псевдоним, если он применяется. Если псевдоним столбец не применяется, имя столбца возвращается. В любом случае, SQL_DESC_UNNAMED настроен на SQL_NAMED. Если нет имени столбца или псевдонима столбца, возвращается пустая строка и SQL_DESC_UNNAMED SQL_UNNAMED.<br /><br /> Эта информация возвращается из SQL_DESC_NAME области записи IRD.|  
|SQL_DESC_NULLABLE (ODBC 3.0)|*Числоатрибутов*|SQL_ NULLABLE, если столбец может иметь значения NULL; SQL_NO_NULLS, если столбец не имеет значения NULL; или SQL_NULLABLE_UNKNOWN, если не известно, принимает ли столбец значения NULL.<br /><br /> Эта информация возвращается из SQL_DESC_NULLABLE области записи IRD.|  
|SQL_DESC_NUM_PREC_RADIX (ODBC 3.0)|*Числоатрибутов*|Если тип данных в поле SQL_DESC_TYPE является приблизительной типом численных данных, то это поле S'LINTEGER содержит значение 2, поскольку SQL_DESC_PRECISION поле содержит количество битов. Если тип данных в поле SQL_DESC_TYPE является точным типом числа данных, это поле содержит значение 10, поскольку поле SQL_DESC_PRECISION содержит количество десятичных цифр. Это поле установлено на 0 для всех типов нечислоных данных.|  
|SQL_DESC_OCTET_LENGTH (ODBC 3.0)|*Числоатрибутов*|Длина, в байтах, строки символов или типа двоичных данных. Для символов с фиксированной длиной или бинарных типов это фактическая длина байтов. Для символов с переменной длиной или бинарных типов это максимальная длина байтов. Это значение не включает нулевой терминатор.<br /><br /> Эта информация возвращается из SQL_DESC_OCTET_LENGTH области записи IRD.<br /><br /> Для получения дополнительной информации о длине см. [Размер столбца, десятичные цифры, длина переноса Octet и размер дисплея](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) в приложении D: Типы данных.|  
|SQL_DESC_PRECISION (ODBC 3.0)|*Числоатрибутов*|Числовое значение, которое для типа числового данных обозначает применимую точность. Для типов данных SQL_TYPE_TIME, SQL_TYPE_TIMESTAMP и всех типов интервальных данных, представляющих интервал времени, их значение является применимой точностью компонента дробных секунд.<br /><br /> Эта информация возвращается из SQL_DESC_PRECISION области записи IRD.|  
|SQL_DESC_SCALE (ODBC 3.0)|*Числоатрибутов*|Числовое значение, которое является применимой шкалой для типа числового данных. Для типов данных DECIMAL и NUMERIC это определенная шкала. Он не определен для всех других типов данных.<br /><br /> Эта информация возвращается из поля записи SCALE IRD.|  
|SQL_DESC_SCHEMA_NAME (ODBC 2.0)|*CharacterAttributePtr*|Схема таблицы, содержащая столбец. Возвратное значение определяется реализацией, если столбец является выражением или если столбец является частью представления. Если источник данных не поддерживает схемы или имя схемы не может быть определено, возвращается пустая строка. Это поле записи VARCHAR не ограничено 128 символами.|  
|SQL_DESC_SEARCHABLE (ODBC 1.0)|*Числоатрибутов*|SQL_PRED_NONE, если столбец не может быть использован в пункте WHERE. (Это то же самое, что и SQL_UNSEARCHABLE значение в ODBC 2. *x*.)<br /><br /> SQL_PRED_CHAR, если столбец может быть использован в пункте WHERE, но только с предикатом LIKE. (Это то же самое, что и SQL_LIKE_ONLY значение в ODBC 2. *x*.)<br /><br /> SQL_PRED_BASIC, если столбец может быть использован в пункте WHERE со всеми операторами сравнения, за исключением LIKE. (Это то же самое, что и SQL_EXCEPT_LIKE значение в ODBC 2. *x*.)<br /><br /> SQL_PRED_SEARCHABLE, если столбец может быть использован в пункте WHERE с любым оператором сравнения.<br /><br /> Колонны SQL_LONGVARCHAR типа и SQL_LONGVARBINARY обычно возвращаются SQL_PRED_CHAR.|  
|SQL_DESC_TABLE_NAME (ODBC 2.0)|*CharacterAttributePtr*|Имя таблицы, содержащей столбец. Возвратное значение определяется реализацией, если столбец является выражением или если столбец является частью представления.<br /><br /> Если имя таблицы не может быть определено, возвращается пустая строка.|  
|SQL_DESC_TYPE (ODBC 3.0)|*Числоатрибутов*|Численное значение, описавававававаемый тип данных S'L.<br /><br /> Когда *ColumnNumber* равен 0, SQL_BINARY возвращается для закладок с переменной длиной и SQL_INTEGER возвращается для закладок с фиксированной длиной.<br /><br /> Для типов данных о дате и интервалах это поле возвращает многословный тип данных: SQL_DATETIME или SQL_INTERVAL. (Для получения дополнительной информации смотрите [идентификаторы и дескрипторы типов данных](../../../odbc/reference/appendixes/data-type-identifiers-and-descriptors.md) в приложении D: Типы данных.<br /><br /> Эта информация возвращается из SQL_DESC_TYPE области записи IRD. **Примечание:**  Работать против ODBC 2. *х* драйверы, вместо этого используйте SQL_DESC_CONCISE_TYPE.|  
|SQL_DESC_TYPE_NAME (ODBC 1.0)|*CharacterAttributePtr*|Имя типа типа данных, зависящих от источников данных; например, "CHAR", "VARCHAR", "MONEY", "LONG VARBINARY", или "CHAR ( ) ДЛЯ BIT DATA".<br /><br /> Если тип неизвестен, возвращается пустая строка.|  
|SQL_DESC_UNNAMED (ODBC 3.0)|*Числоатрибутов*|SQL_NAMED или SQL_UNNAMED. Если SQL_DESC_NAME поле IRD содержит псевдоним столбца или имя столбца, SQL_NAMED возвращается. Если нет имени столбца или псевдонима столбец, SQL_UNNAMED возвращается.<br /><br /> Эта информация возвращается из SQL_DESC_UNNAMED области записи IRD.|  
|SQL_DESC_UNSIGNED (ODBC 1.0)|*Числоатрибутов*|SQL_TRUE, если столбец не подписан (или не числовой).<br /><br /> SQL_FALSE если столбец подписан.|  
|SQL_DESC_UPDATABLE (ODBC 1.0)|*Числоатрибутов*|Столбец описывается значениями для определенных констант:<br /><br /> SQL_ATTR_READONLY SQL_ATTR_WRITE SQL_ATTR_READWRITE_UNKNOWN<br /><br /> SQL_DESC_UPDATABLE описывает updatability столбца в наборе результатов, а не столбец в базовой таблице. Updatability базовой колонки, на которой основан столбец набора результатов, может отличаться от значения в этом поле. Вопрос о том, является ли столбец updatable, может основываться на типе данных, привилегиях пользователя и определении набора результата. Если неясно, является ли столбец updatable, SQL_ATTR_READWRITE_UNKNOWN должны быть возвращены.|  
  
 **СЗЛКолАтрибут** является расширительной альтернативой **S'LDescribeCol**. **Компания «СЗЛОописывакол»** возвращает фиксированный набор информации о дескрипторах, основанную на ANSI-89 S'L. **S'LColAttribute** позволяет получить доступ к более обширному набору информации о дескрипторах, доступной в расширениях поставщиков ANSI S'L-92 и DBMS.  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Привязка буфера к столбцовику в наборе результатов|[SQLBindCol, функция](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Отмена обработки оператора|[Функция SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Возвращение информации о столбце в наборе результатов|[Функция SQLDescribeCol](../../../odbc/reference/syntax/sqldescribecol-function.md)|  
|Получение блока данных или прокрутка набора результатов|[Функция SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Получение нескольких строк данных|[Функция S'LFetch](../../../odbc/reference/syntax/sqlfetch-function.md)|  
  
## <a name="example"></a>Пример  
 Следующий пример кода не освобождает ручки и соединения. Для [SQLFreeHandle Function](../../../odbc/reference/syntax/sqlfreehandle-function.md)образцов кода для бесплатных ручек [SQLFreeStmt Function](../../../odbc/reference/syntax/sqlfreestmt-function.md) и инструкций [с](../../../odbc/reference/sample-odbc-program.md)функциями спроданным, см.  
  
```cpp  
// SQLColAttibute.cpp  
// compile with: user32.lib odbc32.lib  
  
#define UNICODE  
  
#include <windows.h>  
#include <sqlext.h>  
#include <strsafe.h>  
  
struct DataBinding {  
   SQLSMALLINT TargetType;  
   SQLPOINTER TargetValuePtr;  
   SQLINTEGER BufferLength;  
   SQLLEN StrLen_or_Ind;  
};  
  
void printStatementResult(SQLHSTMT hstmt) {  
   int bufferSize = 1024, i;  
   SQLRETURN retCode;  
   SQLSMALLINT numColumn = 0, bufferLenUsed;
   
   retCode = SQLNumResultCols(hstmt, &numColumn);  
   
   SQLPOINTER* columnLabels = (SQLPOINTER *)malloc( numColumn * sizeof(SQLPOINTER*) );  
   struct DataBinding* columnData = (struct DataBinding*)malloc( numColumn * sizeof(struct DataBinding) );  
  
   printf( "Columns from that table:\n" );  
   for ( i = 0 ; i < numColumn ; i++ ) {  
      columnLabels[i] = (SQLPOINTER)malloc( bufferSize*sizeof(char) );  
  
      retCode = SQLColAttribute(hstmt, (SQLUSMALLINT)i + 1, SQL_DESC_LABEL, columnLabels[i], (SQLSMALLINT)bufferSize, &bufferLenUsed, NULL);  
      wprintf( L"Column %d: %s\n", i, (wchar_t*)columnLabels[i] );  
   }  
  
   // allocate memory for the binding  
   for ( i = 0 ; i < numColumn ; i++ ) {  
      columnData[i].TargetType = SQL_C_CHAR;  
      columnData[i].BufferLength = (bufferSize+1);  
      columnData[i].TargetValuePtr = malloc( sizeof(unsigned char)*columnData[i].BufferLength );  
   }  
  
   // setup the binding   
   for ( i = 0 ; i < numColumn ; i++ ) {  
      retCode = SQLBindCol(hstmt, (SQLUSMALLINT)i + 1, columnData[i].TargetType,   
         columnData[i].TargetValuePtr, columnData[i].BufferLength, &(columnData[i].StrLen_or_Ind));  
   }  
  
   printf( "Data from that table:\n" );  
   // fetch the data and print out the data  
   for ( retCode = SQLFetch(hstmt) ; retCode == SQL_SUCCESS || retCode == SQL_SUCCESS_WITH_INFO ; retCode = SQLFetch(hstmt) ) {  
      int j;  
      for ( j = 0 ; j < numColumn ; j++ )  
         wprintf( L"%s: %hs\n", columnLabels[j], columnData[j].TargetValuePtr );  
      printf( "\n" );  
   }  
   printf( "\n" );   
}  
  
int main() {  
   int bufferSize = 1024, i, count = 1, numCols = 5;  
   wchar_t firstTableName[1024], * dbName = (wchar_t *)malloc( sizeof(wchar_t)*bufferSize ), * userName = (wchar_t *)malloc( sizeof(wchar_t)*bufferSize );  
   HWND desktopHandle = GetDesktopWindow();   // desktop's window handle  
   SQLWCHAR connStrbuffer[1024];  
   SQLSMALLINT connStrBufferLen, bufferLen;  
   SQLRETURN retCode;  
  
   SQLHENV henv = NULL;   // Environment     
   SQLHDBC hdbc = NULL;   // Connection handle  
   SQLHSTMT hstmt = NULL;   // Statement handle  
  
   struct DataBinding* catalogResult = (struct DataBinding*) malloc( numCols * sizeof(struct DataBinding) );  
   SQLWCHAR* selectAllQuery = (SQLWCHAR *)malloc( sizeof(SQLWCHAR) * bufferSize );  
  
   // connect to database  
   retCode = SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &henv);  
   retCode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLCHAR *)(void*)SQL_OV_ODBC3, -1);  
   retCode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc);  
   retCode = SQLSetConnectAttr(hdbc, SQL_LOGIN_TIMEOUT, (SQLPOINTER)10, 0);  
   retCode = SQLDriverConnect(hdbc, desktopHandle, L"Driver={SQL Server}", SQL_NTS, connStrbuffer, 1025, &connStrBufferLen, SQL_DRIVER_PROMPT);  
   retCode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmt);  
  
   // display the database information  
   retCode = SQLGetInfo(hdbc, SQL_DATABASE_NAME, dbName, (SQLSMALLINT)bufferSize, (SQLSMALLINT *)&bufferLen);  
   retCode = SQLGetInfo(hdbc, SQL_USER_NAME, userName, (SQLSMALLINT)bufferSize, &bufferLen);  
  
   for ( i = 0 ; i < numCols ; i++ ) {  
      catalogResult[i].TargetType = SQL_C_CHAR;  
      catalogResult[i].BufferLength = (bufferSize + 1);  
      catalogResult[i].TargetValuePtr = malloc( sizeof(unsigned char)*catalogResult[i].BufferLength );  
   }  
  
   // Set up the binding. This can be used even if the statement is closed by closeStatementHandle  
   for ( i = 0 ; i < numCols ; i++ )  
      retCode = SQLBindCol(hstmt, (SQLUSMALLINT)i + 1, catalogResult[i].TargetType, catalogResult[i].TargetValuePtr, catalogResult[i].BufferLength, &(catalogResult[i].StrLen_or_Ind));  
  
   retCode = SQLTables( hstmt, (SQLWCHAR*)SQL_ALL_CATALOGS, SQL_NTS, L"", SQL_NTS, L"", SQL_NTS, L"", SQL_NTS );  
   retCode = SQLFreeStmt(hstmt, SQL_CLOSE);  
  
   retCode = SQLTables( hstmt, dbName, SQL_NTS, userName, SQL_NTS, L"%", SQL_NTS, L"TABLE", SQL_NTS );  
  
   for ( retCode = SQLFetch(hstmt) ; retCode == SQL_SUCCESS || retCode == SQL_SUCCESS_WITH_INFO ; retCode = SQLFetch(hstmt), ++count )  
      if ( count == 1 )  
         StringCchPrintfW( firstTableName, 1024, L"%hs", catalogResult[2].TargetValuePtr );  
   retCode = SQLFreeStmt(hstmt, SQL_CLOSE);  
  
   wprintf( L"Select all data from the first table (%s)\n", firstTableName );  
   StringCchPrintfW( selectAllQuery, bufferSize, L"SELECT * FROM %s", firstTableName );  
  
   retCode = SQLExecDirect(hstmt, selectAllQuery, SQL_NTS);  
   printStatementResult(hstmt);  
}  
```  
  
## <a name="see-also"></a>См. также:  
 [Справка aPI ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовка ODBC](../../../odbc/reference/install/odbc-header-files.md)   
 [Образец программы ODBC](../../../odbc/reference/sample-odbc-program.md)
