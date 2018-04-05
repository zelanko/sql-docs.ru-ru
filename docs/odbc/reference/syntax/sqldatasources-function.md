---
title: Функция SQLDataSources | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
apiname:
- SQLDataSources
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLDataSources
helpviewer_keywords:
- SQLDataSources function [ODBC]
ms.assetid: 3f63b1b4-e70e-44cd-96c6-6878d50d0117
caps.latest.revision: 22
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8aee3d9e1caa424f4792fb1fae0551adcacfcdc3
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="sqldatasources-function"></a>Функция SQLDataSources
**Соответствия**  
 Появился в версии: Полное соответствие стандартам 1.0 ODBC: ISO-92  
  
 **Сводка**  
 **SQLDataSources** возвращает сведения об источнике данных. Эта функция реализуется только диспетчером драйверов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SQLRETURN SQLDataSources(  
     SQLHENV          EnvironmentHandle,  
     SQLUSMALLINT     Direction,  
     SQLCHAR *        ServerName,  
     SQLSMALLINT      BufferLength1,  
     SQLSMALLINT *    NameLength1Ptr,  
     SQLCHAR *        Description,  
     SQLSMALLINT      BufferLength2,  
     SQLSMALLINT *    NameLength2Ptr);  
```  
  
## <a name="arguments"></a>Аргументы  
 *EnvironmentHandle*  
 [Вход] Дескриптор среды.  
  
 *Направление*  
 [Вход] Определяет, какой источник данных диспетчера драйверов возвращает сведения о. Возможны следующие варианты:  
  
 SQL_FETCH_NEXT (для выборки далее имя источника данных в списке), SQL_FETCH_FIRST (извлекаемых из начала списка), SQL_FETCH_FIRST_USER (для выборки первый пользователь DSN) или SQL_FETCH_FIRST_SYSTEM (для получения первого системный DSN).  
  
 При *направление* равно SQL_FETCH_FIRST, последующие вызовы **SQLDataSources** с *направление* набор для SQL_FETCH_NEXT возвращают пользовательских и системных источников данных. При *направление* равно SQL_FETCH_FIRST_USER, все последующие вызовы **SQLDataSources** с *направление* набор для SQL_FETCH_NEXT возвращают только пользовательских источников данных. При *направление* равно SQL_FETCH_FIRST_SYSTEM, все последующие вызовы **SQLDataSources** с *направление* набор для SQL_FETCH_NEXT возвращают только системных источников данных.  
  
 *ServerName*  
 [Выход] Указатель на буфер, в который возвращается имя источника данных.  
  
 Если *ServerName* имеет значение NULL, *NameLength1Ptr* по-прежнему возвращает общее число символов (за исключением символа конечное значение null, символьные данные) для возврата в буфере, на который указывает *Имя_сервера*.  
  
 *BufferLength1*  
 [Вход] Длина **ServerName* буфера в символах; это не обязательно быть длиннее, чем SQL_MAX_DSN_LENGTH в сочетании с символом конечное значение null.  
  
 *NameLength1Ptr*  
 [Выход] Указатель на буфер, в который возвращается общее число символов (за исключением знака завершения null) для возврата в \* *имя_сервера*. Если количество символов вернуть больше или равно *BufferLength1*, имя источника данных в \* *ServerName* усекается до *BufferLength1* за вычетом длины символ конечное значение null.  
  
 *Description*  
 [Выход] Указатель на буфер, в который возвращается Описание драйвера, связанного с источником данных. Например dBASE или SQL Server.  
  
 Если *описание* имеет значение NULL, *NameLength2Ptr* по-прежнему возвращает общее число символов (за исключением символа конечное значение null, символьные данные) для возврата в буфере, на который указывает *Описание*.  
  
 *BufferLength2*  
 [Вход] Длина в символах **описание* буфера.  
  
 *NameLength2Ptr*  
 [Выход] Указатель на буфер, в который возвращается общее число символов (за исключением знака завершения null) для возврата в \* *описание*. Если количество символов вернуть больше или равно *BufferLength2*, описание драйвера в \* *описание* усекается до *BufferLength2*  за вычетом длины символ конечное значение null.  
  
## <a name="returns"></a>Возвращает  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA, значение SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLDataSources** возвращает значение SQL_ERROR или SQL_SUCCESS_WITH_INFO, соответствующее значение SQLSTATE можно получить, вызвав **SQLGetDiagRec** с *HandleType*установленным в значение sql_handle_env и *обработки* из *EnvironmentHandle*. В следующей таблице перечислены значения SQLSTATE, обычно возвращаемые **SQLDataSources** и описание каждого из них в контексте этой функции; нотации «(DM)» предшествует описания SQLSTATE, возвращаемых диспетчером драйверов. Код возврата, связанные с каждым из значений SQLSTATE — это SQL_ERROR, если не указано иное.  
  
|SQLSTATE|Ошибка|Description|  
|--------------|-----------|-----------------|  
|01000|Общее предупреждение|(DM) диспетчера драйверов, определяемые информационное сообщение. (Функция возвращает значение SQL_SUCCESS_WITH_INFO).|  
|01004|Строка справа усечение данных|(DM) буфер \* *ServerName* не был достаточно велик, чтобы вернуть имя источника данных завершено. Таким образом имя усечено. Длина имени источника данных возвращается в \* *NameLength1Ptr*. (Функция возвращает значение SQL_SUCCESS_WITH_INFO).<br /><br /> (DM) буфер \* *описание* не был достаточно велик, возвращается описание завершения драйвера. Таким образом описание был усечен. Длина описания источника данных неусеченный возвращается в **NameLength2Ptr*. (Функция возвращает значение SQL_SUCCESS_WITH_INFO).|  
|HY000|Общая ошибка|(DM) произошла ошибка, для которой было нет определенных SQLSTATE и для которого был определен SQLSTATE не зависит от реализации. Сообщение об ошибке, возвращенные **SQLGetDiagRec** в  *\*MessageText* буфера описывает ошибку и его причины.|  
|HY001|Ошибка выделения памяти|Диспетчер драйверов (DM) не удалось выделить память, который необходим для поддержки выполнения или завершения функции.|  
|HY010|Ошибка последовательности функций|(DM) **SQLExecute**, **SQLExecDirect**, или **SQLMoreResults** был вызван для *StatementHandle* и возвращается SQL_PARAM_DATA_ ЭТОТ ПАРАМЕТР ДОСТУПЕН. До получения данных для всех параметров потоковой вызове этой функции.|  
|HY013|Ошибка управления памятью|Не удалось обработать вызов функции, поскольку базовые объекты памяти будет недоступен, возможно из-за нехватки памяти.|  
|HY090|Недопустимая длина строки или буфера|(DM) значение, указанное в аргументе *BufferLength1* был меньше 0.<br /><br /> (DM) значение, указанное в аргументе *BufferLength2* был меньше 0.|  
|HY103|Недопустимое получение кода|(DM) значение, указанное для аргумента *направление* не равнялось SQL_FETCH_FIRST, SQL_FETCH_FIRST_USER, SQL_FETCH_FIRST_SYSTEM или SQL_FETCH_NEXT.|  
|HY117|Соединение будет приостановлена из-за неизвестной транзакции состояния. Только отключиться и разрешены функции, доступные только для чтения.|(DM) Дополнительные сведения о состоянии приостановки см. в разделе [функция SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
  
## <a name="comments"></a>Комментарии  
 Поскольку **SQLDataSources** реализуется диспетчера драйверов, он поддерживается для все драйверы независимо от того, соответствие стандартам конкретного драйвера.  
  
 Приложение может вызвать **SQLDataSources** несколько раз, чтобы получить все имена источников данных. Диспетчер драйверов извлекает эту информацию из сведений о системе. Если отсутствуют дополнительные имена источника данных, диспетчер драйверов не вернет значение SQL_NO_DATA. Если **SQLDataSources** вызывается с SQL_FETCH_NEXT сразу же после вернулось значение SQL_NO_DATA, возвращается первый источник данных. Сведения о том, как приложение использует сведения, возвращаемые функцией **SQLDataSources**, в разделе [Выбор источника данных или драйвер](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md).  
  
 Если передается SQL_FETCH_NEXT **SQLDataSources** первый раз, он вызывается, он возвращает имя первого источника данных.  
  
 Драйвер определяет сопоставление имен источников данных к источникам данных.  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Обнаружение и вывод значения, необходимые для подключения к источнику данных|[Функция SQLBrowseConnect](../../../odbc/reference/syntax/sqlbrowseconnect-function.md)|  
|Подключение к источнику данных|[Функция SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)|  
|Соединение с источником данных, используется поле строки или диалоговое окно соединения|[Функция SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)|  
|Возврат описания драйверов и атрибуты|[Функция SQLDrivers](../../../odbc/reference/syntax/sqldrivers-function.md)|  
  
## <a name="see-also"></a>См. также:  
 [Справочник по API-интерфейса ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)
