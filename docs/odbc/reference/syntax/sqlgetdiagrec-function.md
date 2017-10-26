---
title: "Функции SQLGetDiagRec | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLGetDiagRec
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetDiagRec
helpviewer_keywords:
- SQLGetDiagRec function [ODBC]
ms.assetid: ebdbac93-3d68-438f-8416-ef1f08e04269
caps.latest.revision: 26
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 591664f329f4c7feeb24fff52b809dba567d0b80
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="sqlgetdiagrec-function"></a>Функция Sqlgetdescrec
**Соответствия**  
 Появился в версии: ODBC 3.0 нормативных требований: ISO-92  
  
 **Сводка**  
 **SQLGetDiagRec** возвращает текущие значения нескольких полей диагностики запись, которая содержит сведения об ошибках, предупреждения и состояние. В отличие от **SQLGetDiagField**, которая возвращает одно поле диагностики для каждого вызова, **SQLGetDiagRec** возвращает некоторые часто используемые поля диагностические записи, включая значение SQLSTATE, машинный код ошибки, и текст диагностическое сообщение.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SQLRETURN SQLGetDiagRec(  
     SQLSMALLINT     HandleType,  
     SQLHANDLE       Handle,  
     SQLSMALLINT     RecNumber,  
     SQLCHAR *       SQLState,  
     SQLINTEGER *    NativeErrorPtr,  
     SQLCHAR *       MessageText,  
     SQLSMALLINT     BufferLength,  
     SQLSMALLINT *   TextLengthPtr);  
```  
  
## <a name="arguments"></a>Аргументы  
 *HandleType*  
 [Вход] Идентификатор типа дескриптора, описывающий тип дескриптора, для которого требуются диагностики. Должна быть одной из следующих:  
  
-   SQL_HANDLE_DBC  
  
-   SQL_HANDLE_DBC_INFO_TOKEN  
  
-   SQL_HANDLE_DESC  
  
-   SQL_HANDLE_ENV  
  
-   ЗНАЧЕНИЕ SQL_HANDLE_STMT  
  
 Дескриптор SQL_HANDLE_DBC_INFO_TOKEN используется только для диспетчера драйверов и драйверов. Приложения не должны использовать этот тип дескриптора. Дополнительные сведения о SQL_HANDLE_DBC_INFO_TOKEN см. в разделе [разработке пула соединений, поддерживающие драйвер ODBC](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md).  
  
 *Дескриптор*  
 [Вход] Дескриптор для структуры диагностических данных, тип, указанный *HandleType*. Если *HandleType* — SQL_HANDLE_ENV, *обработки* может быть общим или дескриптор среды с монопольным доступом.  
  
 *RecNumber*  
 [Вход] Указывает состояние записи, из которой приложение ищет сведения. Состояние записи нумеруются от 1.  
  
 *SQLState*  
 [Выход] Указатель на буфер, в которую будет возвращен код Пятисимвольный SQLSTATE (и конечное значение NULL) для записи диагностики *RecNumber*. Первые два символа указывают класса; Далее три указывают подкласса. Эти сведения содержатся в поле SQL_DIAG_SQLSTATE диагностики. Дополнительные сведения см. в разделе [SQLSTATE](../../../odbc/reference/develop-app/sqlstates.md).  
  
 *NativeErrorPtr*  
 [Выход] Указатель на буфер, в которую будет возвращен машинный код ошибки, относящиеся к источнику данных. Эти сведения содержатся в поле SQL_DIAG_NATIVE диагностики.  
  
 *MessageText*  
 [Выход] Указатель на буфер, в которую будет возвращен диагностическое сообщение текстовую строку. Эти сведения содержатся в поле SQL_DIAG_MESSAGE_TEXT диагностики. Формат строки, в разделе [диагностические сообщения](../../../odbc/reference/develop-app/diagnostic-messages.md).  
  
 Если *MessageText* имеет значение NULL, *TextLengthPtr* по-прежнему возвращает общее число символов (за исключением символа конечное значение null, символьные данные) для возврата в буфере, на который указывает *MessageText*.  
  
 *BufferLength*  
 [Вход] Длина **MessageText* буфера в символах. Нет без ограничения длины текста диагностическое сообщение.  
  
 *TextLengthPtr*  
 [Выход] Указатель на буфер, в который возвращается общее число символов (за исключением количество символов, необходимых для знака завершения null) для возврата в * \*MessageText*. Если количество символов вернуть больше, чем *BufferLength*, текст сообщения о диагностике в * \*MessageText* усекается до *BufferLength* за вычетом длины символ конечное значение null.  
  
## <a name="returns"></a>Возвращает  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, значение SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 **SQLGetDiagRec** не публикует диагностические записи для себя. Он использует следующие возвращаемые значения для оповещения результат собственный выполнения:  
  
-   SQL_SUCCESS: Функция успешно возвращен диагностические сведения.  
  
-   SQL_SUCCESS_WITH_INFO: \* *MessageText* буфер слишком мал для хранения запрошенного диагностическое сообщение. Диагностические записи не были созданы. Чтобы определить, что возникло усечение, приложение необходимо сравнить *BufferLength* фактическое число доступных байтов, записываемые в **StringLengthPtr*.  
  
-   SQL_INVALID_HANDLE: Дескриптор обозначается *HandleType* и *обработки* не является допустимым дескриптором.  
  
-   Значение SQL_ERROR: Произошло одно из следующих:  
  
    -   *RecNumber* была меньше или равно 0.  
  
    -   *BufferLength* меньше нуля.  
  
    -   При использовании асинхронного уведомления, асинхронные операции для дескриптора не завершена.  
  
-   Значение SQL_NO_DATA: *RecNumber* превышает количество диагностических записей, которые существовали для дескриптор, указанный в *обработки.* Функция также возвращает значение SQL_NO_DATA любой положительные *RecNumber* Если нет диагностических записей для *обработки*.  
  
## <a name="comments"></a>Комментарии  
 Приложение обычно вызывает **SQLGetDiagRec** после предыдущего вызова функции ODBC вернул значение SQL_ERROR или SQL_SUCCESS_WITH_INFO. Тем не менее, так как любая функция ODBC можно разместить ноль или более записей диагностики при каждом вызове, приложение может вызвать **SQLGetDiagRec** после любого вызова функции ODBC. Приложение может вызвать **SQLGetDiagRec** несколько раз, чтобы вернуть некоторые или все записи в структуре диагностических данных. ODBC не предусмотрено ограничение на количество диагностических записей, которые могут храниться в любой момент времени.  
  
 **SQLGetDiagRec** не может использоваться для возврата полей из заголовка структуры диагностических данных. ( *RecNumber* аргумент должен быть больше 0.) Приложение должно вызывать **SQLGetDiagField** для этой цели.  
  
 **SQLGetDiagRec** получает диагностические сведения, недавно связанной с дескриптором, указанный в *обработки* аргумент. Если приложение вызывает другую функцию ODBC, за исключением **SQLGetDiagRec**, **SQLGetDiagField**, или **SQLError**, все диагностические сведения из предыдущих вызовов на же дескриптор теряются.  
  
 Приложение может сканировать все диагностические записи по коллекциям, увеличивая *RecNumber*, при условии, что **SQLGetDiagRec** возвращает SQL_SUCCESS. Вызовы **SQLGetDiagRec** являются обратимыми полей заголовка и записи. Приложение может вызвать **SQLGetDiagRec** еще раз позже для извлечения полей из записи, пока в другие функции, за исключением **SQLGetDiagRec**, **SQLGetDiagField**, или **SQLError**, был вызван за этот промежуток времени. Приложение также можно получить, вызвав количество общее число доступных диагностических записей **SQLGetDiagField** для получения значения поля SQL_DIAG_NUMBER, а затем вызов метода **SQLGetDiagRec**количество раз.  
  
 Описание полей структуры диагностических данных см. в разделе [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md). Дополнительные сведения см. в разделе [с помощью SQLGetDiagRec и SQLGetDiagField](../../../odbc/reference/develop-app/using-sqlgetdiagrec-and-sqlgetdiagfield.md) и [реализации SQLGetDiagRec и SQLGetDiagField](../../../odbc/reference/develop-app/implementing-sqlgetdiagrec-and-sqlgetdiagfield.md).  
  
 Вызов API-Интерфейс, отличном от того, которое выполняется асинхронно создаст HY010 «Функция ошибка последовательности». Однако не удалось получить запись об ошибке, до завершения асинхронной операции.  
  
## <a name="handletype-argument"></a>Аргумент HandleType  
 Каждый тип дескриптора может иметь диагностические сведения, связанные с ним. *HandleType* аргумент обозначает тип дескриптора *обработки* аргумент.  
  
 Некоторые поля заголовка и записи не может быть предоставлен среды, подключения, инструкции и дескриптора дескрипторов. Эти дескрипторы, для которых поле не применимо, отображаются в разделах «Заголовок полей» и «записи» в [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md).  
  
 Вызов **SQLGetDiagRec** возвращает SQL_INVALID_HANDLE, если *HandleType* — SQL_HANDLE_SENV, который используется для обозначения дескриптор общей среде. Однако если *HandleType* — SQL_HANDLE_ENV, *обработки* может быть общим или дескриптор среды с монопольным доступом.  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Получение поля диагностики записи или поля диагностики заголовка|[Функция SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)|  
  
## <a name="see-also"></a>См. также:  
 [Справочник по API-интерфейса ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовка ODBC](../../../odbc/reference/install/odbc-header-files.md)   
 [Образец программы на ODBC](../../../odbc/reference/sample-odbc-program.md)

