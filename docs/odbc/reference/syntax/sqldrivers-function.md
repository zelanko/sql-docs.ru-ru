---
title: Функция SQLDrivers | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bac7f88dcbd9895cfd0d07a5993ab9e38a4608d0
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63061902"
---
# <a name="sqldrivers-function"></a>Функция SQLDrivers
**Соответствие стандартам**  
 Представленные версии: ODBC 2.0 стандартов соответствия: интерфейс ODBC  
  
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
 [Вход] Определяет, получает ли диспетчер драйверов Далее Описание драйвера в списке (SQL_FETCH_NEXT) или от того, начинается ли поиск с начала списка (SQL_FETCH_FIRST).  
  
 *DriverDescription*  
 [Выход] Указатель на буфер, в которую будет возвращен Описание драйвера.  
  
 Если *DriverDescription* имеет значение NULL, *DescriptionLengthPtr* по-прежнему возвращает общее число символов (включая знак завершения null для символьных данных) для возврата в буфер, на которые указывают *DriverDescription*.  
  
 *BufferLength1*  
 [Вход] Длина **DriverDescription* буфера в символах.  
  
 *DescriptionLengthPtr*  
 [Выход] Указатель на буфер, в которую будет возвращено общее число символов (за исключением знака завершения null) для возврата в \* *DriverDescription*. Если количество символов, доступных для возврата больше или равно *BufferLength1*, описание драйвера в \* *DriverDescription* усекается до  *BufferLength1* минус длина знак завершения null.  
  
 *DriverAttributes*  
 [Выход] Указатель на буфер, в которую будет возвращен список пар значение атрибута "драйвер" (см. в разделе «Комментарии»).  
  
 Если *DriverAttributes* имеет значение NULL, *AttributesLengthPtr* по-прежнему возвращает общее число байтов (за исключением символа конечное значение null для символьных данных) для возврата в буфере Указывает *DriverAttributes*.  
  
 *BufferLength2*  
 [Вход] Длина \* *DriverAttributes* буфера в символах. Если  *\*DriverDescription* значение является строкой Юникода (при вызове **SQLDriversW**), *BufferLength* аргумент должен быть четным числом.  
  
 *AttributesLengthPtr*  
 [Выход] Указатель на буфер, в которую будет возвращено общее число байтов (за исключением байтов конечное значение null) для возврата в \* *DriverAttributes*. Если количество байтов, доступных для возврата больше или равно *BufferLength2*, список пар атрибутов значение в \* *DriverAttributes* усекается до  *BufferLength2* минус длина знак завершения null.  
  
## <a name="returns"></a>Возвращает  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA, SQL_ERROR, or SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLDrivers** возвращает значение SQL_ERROR или SQL_SUCCESS_WITH_INFO, можно получить путем вызова связанного значения SQLSTATE **SQLGetDiagRec** с *HandleType* из SQL_HANDLE_ENV и *обрабатывать* из *EnvironmentHandle*. В следующей таблице перечислены значения SQLSTATE, обычно возвращаемые при помощи **SQLDrivers** и объясняется каждый из них в контексте этой функции; описания SQLSTATE, возвращаемых диспетчером драйверов предшествует обозначение «(DM)». Возвращается связанный с каждого значения SQLSTATE значение SQL_ERROR, если не указано иное.  
  
|SQLSTATE|Ошибка|Описание|  
|--------------|-----------|-----------------|  
|01000|Общее предупреждение|(DM) конкретного диспетчера драйверов информационное сообщение. (Функция возвращает значение SQL_SUCCESS_WITH_INFO).|  
|01004|Усечение данных строки справа|(DM) буфера \* *DriverDescription* не было достаточно крупным для возврата описания завершения драйвера. Таким образом описание были усечены. Длина описания полный драйвер возвращается в \* *DescriptionLengthPtr*. (Функция возвращает значение SQL_SUCCESS_WITH_INFO).<br /><br /> (DM) буфера \* *DriverAttributes* не был достаточно велик для того, чтобы получить полный список пар "атрибут-значение". Таким образом список был усечен. Длина неусеченный список пар "атрибут-значение" возвращается в **AttributesLengthPtr*. (Функция возвращает значение SQL_SUCCESS_WITH_INFO).|  
|HY000|Общая ошибка|Произошла ошибка, для которой было нет конкретных SQLSTATE и SQLSTATE не зависящие от реализации, который был определен. Сообщение об ошибке, возвращенные **SQLGetDiagRec** в  *\*MessageText* буфера описывает ошибку и его причины.|  
|HY001|Ошибка выделения памяти|Диспетчер драйверов (DM) не удалось выделить память, необходимая для поддержки выполнения или завершения функции.|  
|HY010|Ошибка последовательности функций|(DM) **SQLExecute**, **SQLExecDirect**, или **SQLMoreResults** был вызван для *StatementHandle* и возвращается SQL_PARAM_DATA_ ДОСТУПНО. Прежде чем данные были получены для всех параметров потоковой вызове этой функции.|  
|HY013|Ошибка управления памятью|Не удалось обработать вызов функции, так как базовые объекты памяти оказываются недоступны, возможно из-за нехватки памяти.|  
|HY090|Недопустимая длина строки или буфера|(DM) значение, указанное для аргумента *BufferLength1* меньше 0.<br /><br /> (DM) значение, указанное для аргумента *BufferLength2* был меньше 0 или равно 1.|  
|HY103|Недопустимый код получения|(DM) значение, указанное для аргумента *направление* не равно SQL_FETCH_FIRST или SQL_FETCH_NEXT.|  
|HY117|Подключение будет приостановлена из-за состояние транзакции неизвестно. Только отключиться и разрешены функции, доступные только для чтения.|(DM) Дополнительные сведения о состоянии приостановки, см. в разделе [функция SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
  
## <a name="comments"></a>Комментарии  
 **SQLDrivers** возвращает описание драйвера в \* *DriverDescription* буфера. Он возвращает Дополнительные сведения о драйвере в \* *DriverAttributes* буфер в виде списка пар "ключевое слово значение". Все ключевые слова, указанные в сведениях о системе для драйверов будет возвращаться для всех драйверов, за исключением **CreateDSN**, который используется для запроса создания источников данных и поэтому является необязательным. Каждая пара заканчивается нулевым байтом, а полный список заканчивается нулевым байтом (то есть две пустые байты обозначения конца списка). Например с помощью синтаксиса C драйверов на основе файла может вернуть перечисленные ниже атрибуты («\0» представляет символ null).  
  
```  
FileUsage=1\0FileExtns=*.dbf\0\0  
```  
  
 Если \* *DriverAttributes* является не недостаточно велик для хранения по всему списку, список усекается, **SQLDrivers** возвращает SQLSTATE 01004 (данных) и длину списка (за исключением последний байт конечное значение null) возвращается в **AttributesLengthPtr*.  
  
 Ключевые слова атрибута драйвера добавляются из информации о системе, при установке драйвера. Дополнительные сведения см. в разделе [Установка компонентов ODBC](../../../odbc/reference/install/installing-odbc-components.md).  
  
 Приложение может вызвать **SQLDrivers** несколько раз, чтобы получить все описания драйвера. Диспетчер драйверов получает эти сведения из сведений о системе. При наличии нет дополнительного описания драйвер **SQLDrivers** не вернет значение SQL_NO_DATA. Если **SQLDrivers** вызывается с SQL_FETCH_NEXT сразу же после его вернет значение SQL_NO_DATA, он возвращает первое описание драйвера. Сведения о том, как приложение использует сведения, возвращаемые функцией **SQLDrivers**, см. в разделе [Выбор источника данных или драйвера](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md).  
  
 Если передается SQL_FETCH_NEXT **SQLDrivers** в первый раз, он называется **SQLDrivers** возвращает имя первого источника данных.  
  
 Так как **SQLDrivers** реализуется в диспетчер драйверов, она будет поддерживать все драйверы независимо от того, соответствие стандартам конкретного драйвера.  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Обнаружение и список значений, необходимых для подключения к источнику данных|[Функция SQLBrowseConnect](../../../odbc/reference/syntax/sqlbrowseconnect-function.md)|  
|Подключение к источнику данных|[Функция SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)|  
|Возвращает имена источников данных|[Функция SQLDataSources](../../../odbc/reference/syntax/sqldatasources-function.md)|  
|Подключение к источнику данных с помощью соединения строки или в диалоговом окне|[Функция SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)|  
  
## <a name="see-also"></a>См. также  
 [Справочник по API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)
