---
title: "SQLDrivers, функция | Документы Microsoft"
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
apiname:
- SQLDrivers
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLDrivers
helpviewer_keywords:
- SQLDrivers function [ODBC]
ms.assetid: 6b5b7514-e9cb-4cfd-8b7a-ab51dfab9efa
caps.latest.revision: 23
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 39d6aee9cf7260d4bc21cc66d39f8845c3d7df97
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="sqldrivers-function"></a>SQLDrivers, функция
**Соответствия**  
 Появился в версии: ODBC 2.0 нормативных требований: ODBC  
  
 **Сводка**  
 **SQLDrivers** перечислены описания драйверов и ключевые слова атрибута драйвера. Эта функция реализуется только диспетчером драйверов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SQLRETURN SQLDrivers(  
     SQLHENV         EnvironmentHandle,  
     SQLUSMALLINT    Direction,  
     SQLCHAR *       DriverDescription,  
     SQLSMALLINT     BufferLength1,  
     SQLSMALLINT *   DescriptionLengthPtr,  
     SQLCHAR *       DriverAttributes,  
     SQLSMALLINT     BufferLength2,  
     SQLSMALLINT *   AttributesLengthPtr);  
```  
  
## <a name="arguments"></a>Аргументы  
 *EnvironmentHandle*  
 [Вход] Дескриптор среды.  
  
 *Направление*  
 [Вход] Определяет, получает ли диспетчер драйверов Далее описания драйвера в списке (SQL_FETCH_NEXT) или ли поиск начинается с начала списка (SQL_FETCH_FIRST).  
  
 *DriverDescription*  
 [Выход] Указатель на буфер, в который возвращается Описание драйвера.  
  
 Если *DriverDescription* имеет значение NULL, *DescriptionLengthPtr* по-прежнему возвращает общее число символов (за исключением символа конечное значение null, символьные данные) для возврата в буфер, на который указывает *DriverDescription*.  
  
 *BufferLength1*  
 [Вход] Длина **DriverDescription* буфера в символах.  
  
 *DescriptionLengthPtr*  
 [Выход] Указатель на буфер, в который возвращается общее число символов (за исключением знака завершения null) для возврата в \* *DriverDescription*. Если количество символов вернуть больше или равно *BufferLength1*, описание драйвера в \* *DriverDescription* усекается до  *BufferLength1* за вычетом длины символ конечное значение null.  
  
 *DriverAttributes*  
 [Выход] Указатель на буфер, в которую будет возвращен список пар значение атрибута "драйвер" (в разделе «Комментарии»).  
  
 Если *DriverAttributes* имеет значение NULL, *AttributesLengthPtr* по-прежнему возвращает общее количество байтов (за исключением знака конечное значение null для символьных данных) для возврата в буфер Указывает *DriverAttributes*.  
  
 *BufferLength2*  
 [Вход] Длина \* *DriverAttributes* буфера в символах. Если  *\*DriverDescription* значение является строкой Юникода (при вызове **SQLDriversW**), *BufferLength* аргумент должен быть четным числом.  
  
 *AttributesLengthPtr*  
 [Выход] Указатель на буфер, в который возвращается общее количество байтов (за исключением байтов конечное значение null) для возврата в \* *DriverAttributes*. Если количество байтов, доступных для возврата больше или равно *BufferLength2*, список пары значений атрибутов в \* *DriverAttributes* усекается до  *BufferLength2* за вычетом длины символ конечное значение null.  
  
## <a name="returns"></a>Возвращает  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA, значение SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLDrivers** возвращает значение SQL_ERROR или SQL_SUCCESS_WITH_INFO, соответствующее значение SQLSTATE можно получить, вызвав **SQLGetDiagRec** с *HandleType* из SQL_HANDLE_ENV и *обработки* из *EnvironmentHandle*. В следующей таблице перечислены значения SQLSTATE, обычно возвращаемые **SQLDrivers** и описание каждого из них в контексте этой функции; нотации «(DM)» предшествует описания SQLSTATE, возвращаемых диспетчером драйверов. Код возврата, связанные с каждым из значений SQLSTATE — это SQL_ERROR, если не указано иное.  
  
|SQLSTATE|Ошибка|Description|  
|--------------|-----------|-----------------|  
|01000|Общее предупреждение|(DM) диспетчера драйверов, определяемые информационное сообщение. (Функция возвращает значение SQL_SUCCESS_WITH_INFO).|  
|01004|Строка справа усечение данных|(DM) буфер \* *DriverDescription* не был достаточно велик, возвращается описание завершения драйвера. Таким образом описание был усечен. Длина описания полный драйвер возвращается в \* *DescriptionLengthPtr*. (Функция возвращает значение SQL_SUCCESS_WITH_INFO).<br /><br /> (DM) буфер \* *DriverAttributes* не был достаточно велик, чтобы получить полный список пар «атрибут-значение». Таким образом список был усечен. Длина неусеченный списка пар «атрибут-значение», возвращается в **AttributesLengthPtr*. (Функция возвращает значение SQL_SUCCESS_WITH_INFO).|  
|HY000|Общая ошибка|Произошла ошибка, для которой было нет определенных SQLSTATE и для которого был определен SQLSTATE не зависит от реализации. Сообщение об ошибке, возвращенные **SQLGetDiagRec** в  *\*MessageText* буфера описывает ошибку и его причины.|  
|HY001|Ошибка выделения памяти|Диспетчер драйверов (DM) не удалось выделить память, который необходим для поддержки выполнения или завершения функции.|  
|HY010|Ошибка последовательности функций|(DM) **SQLExecute**, **SQLExecDirect**, или **SQLMoreResults** был вызван для *StatementHandle* и возвращается SQL_PARAM_DATA_ ЭТОТ ПАРАМЕТР ДОСТУПЕН. До получения данных для всех параметров потоковой вызове этой функции.|  
|HY013|Ошибка управления памятью|Не удалось обработать вызов функции, поскольку базовые объекты памяти будет недоступен, возможно из-за нехватки памяти.|  
|HY090|Недопустимая длина строки или буфера|(DM) значение, указанное в аргументе *BufferLength1* был меньше 0.<br /><br /> (DM) значение, указанное в аргументе *BufferLength2* был меньше 0 или равно 1.|  
|HY103|Недопустимое получение кода|(DM) значение, указанное для аргумента *направление* не равнялось SQL_FETCH_FIRST или SQL_FETCH_NEXT.|  
|HY117|Соединение будет приостановлена из-за неизвестной транзакции состояния. Только отключиться и разрешены функции, доступные только для чтения.|(DM) Дополнительные сведения о состоянии приостановки см. в разделе [функция SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
  
## <a name="comments"></a>Комментарии  
 **SQLDrivers** возвращает описание драйвер в \* *DriverDescription* буфера. Возвращает дополнительные сведения о драйвере в \* *DriverAttributes* буфера в виде списка пар «ключевое слово значение». Все ключевые слова, указанные сведения о системе для драйверов будут возвращены для всех драйверов, за исключением **CreateDSN**, который используется для запроса создания источников данных и поэтому является необязательным. Каждая пара заканчивается нулевым байтом, и завершается нулевым байтом полный список (то есть две пустые байты отмечающий конец списка). Например на основе файла драйвера, с использованием синтаксиса C может возвратить следующий список атрибутов («\0» представляет символ null):  
  
```  
FileUsage=1\0FileExtns=*.dbf\0\0  
```  
  
 Если \* *DriverAttributes* — не недостаточно велик для хранения списка в целом, список будет усечен, **SQLDrivers** возвращает SQLSTATE 01004 (данных) и размер списка (за исключением последний байт конечное значение null), возвращается в **AttributesLengthPtr*.  
  
 Ключевые слова атрибутов драйвера добавляются из сведений о системе, при установке драйвера. Дополнительные сведения см. в разделе [Установка компонентов ODBC](../../../odbc/reference/install/installing-odbc-components.md).  
  
 Приложение может вызвать **SQLDrivers** несколько раз, чтобы получить все описания драйвера. Диспетчер драйверов извлекает эту информацию из сведений о системе. При наличии не Дополнительные описания драйверов **SQLDrivers** не вернет значение SQL_NO_DATA. Если **SQLDrivers** вызывается с SQL_FETCH_NEXT сразу же после вернулось значение SQL_NO_DATA, он возвращает описание первого драйвера. Сведения о том, как приложение использует сведения, возвращаемые функцией **SQLDrivers**, в разделе [Выбор источника данных или драйвер](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md).  
  
 Если передается SQL_FETCH_NEXT **SQLDrivers** в первый раз, он вызывается **SQLDrivers** возвращает имя первого источника данных.  
  
 Поскольку **SQLDrivers** реализуется диспетчера драйверов, он поддерживается для все драйверы независимо от того, соответствие стандартам конкретного драйвера.  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Обнаружение и вывод значения, необходимые для подключения к источнику данных|[Функция SQLBrowseConnect](../../../odbc/reference/syntax/sqlbrowseconnect-function.md)|  
|Подключение к источнику данных|[Функция SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)|  
|Возврат имен источников данных|[Функция SQLDataSources](../../../odbc/reference/syntax/sqldatasources-function.md)|  
|Соединение с источником данных, используется поле строки или диалоговое окно соединения|[Функция SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)|  
  
## <a name="see-also"></a>См. также:  
 [Справочник по API-интерфейса ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)

