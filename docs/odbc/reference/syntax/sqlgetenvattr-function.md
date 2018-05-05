---
title: Функция SQLGetEnvAttr | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
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
caps.latest.revision: 22
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 010a47003b044a400abaaaef5cd7ffd3c80d94d3
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sqlgetenvattr-function"></a>Функция SQLGetEnvAttr
**Соответствия**  
 Появился в версии: ODBC 3.0 нормативных требований: ISO-92  
  
 **Сводка**  
 **SQLGetEnvAttr** возвращает текущее значение атрибута среды.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
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
  
 *Атрибут*  
 [Вход] Атрибут.  
  
 *ValuePtr*  
 [Выход] Указатель на буфер, в который возвращается текущее значение атрибута, заданного с *атрибут*.  
  
 Если *ValuePtr* имеет значение NULL, *StringLengthPtr* по-прежнему возвращает общее количество байтов (за исключением знака конечное значение null для символьных данных) для возврата в буфере, на который указывает  *ValuePtr*.  
  
 *BufferLength*  
 [Вход] Если *ValuePtr* указывает на строку символов, данный аргумент должен иметь длину \* *ValuePtr*. Если \* *ValuePtr* является целым числом, *BufferLength* учитывается. Если  *\*ValuePtr* строка в Юникоде (при вызове **SQLGetEnvAttrW**), *BufferLength* аргумент должен быть четным числом. Если значение атрибута не является строкой символов *BufferLength* не используется.  
  
 *StringLengthPtr*  
 [Выход] Указатель на буфер, в который возвращается общее количество байтов (за исключением знака завершения null) для возврата в  *\*ValuePtr*. Если *ValuePtr* является указателем null, длина не возвращается. Если значение атрибута представляет собой строку символов и число байтов, доступных для возврата больше или равно *BufferLength*, данные в \* *ValuePtr* усекается до  *BufferLength* за вычетом длины знак завершения null и нули драйвером.  
  
## <a name="returns"></a>Возвращает  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA, значение SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLGetEnvAttr** возвращает значение SQL_ERROR или SQL_SUCCESS_WITH_INFO, соответствующее значение SQLSTATE можно получить, вызвав **SQLGetDiagRec** с *HandleType* из SQL_ HANDLE_ENV и *обработки* из *EnvironmentHandle*. В следующей таблице перечислены значения SQLSTATE, обычно возвращаемые **SQLGetEnvAttr** и описание каждого из них в контексте этой функции; нотации «(DM)» предшествует описания SQLSTATE, возвращаемых диспетчером драйверов. Код возврата, связанные с каждым из значений SQLSTATE — это SQL_ERROR, если не указано иное.  
  
|SQLSTATE|Ошибка|Описание|  
|--------------|-----------|-----------------|  
|01000|Общее предупреждение|Информационное сообщение, относящиеся к драйверу. (Функция возвращает значение SQL_SUCCESS_WITH_INFO).|  
|01004|Строка справа усечение данных|Данные, возвращаемые в \* *ValuePtr* усечена, чтобы быть *BufferLength* конечное значение null знак «минус». Длина неусеченный строковое значение возвращается в **StringLengthPtr*. (Функция возвращает значение SQL_SUCCESS_WITH_INFO).|  
|HY000|Общая ошибка|Произошла ошибка, для которой было нет определенных SQLSTATE и для которого был определен SQLSTATE не зависит от реализации. Сообщение об ошибке, возвращенные **SQLGetDiagRec** в  *\*MessageText* буфера описывает ошибку и его причины.|  
|HY001|Ошибка выделения памяти|Драйверу не удалось выделить память, необходимую для поддержки выполнения или завершения функции.|  
|HY010|Ошибка последовательности функций|(DM) **SQL_ATTR_ODBC_VERSION** еще не было задано через **SQLSetEnvAttr**. Не нужно задавать **SQL_ATTR_ODBC_VERSION** явным образом в том случае, если вы используете **SQLAllocHandleStd**.|  
|HY013|Ошибка управления памятью|Не удалось обработать вызов функции, поскольку базовые объекты памяти будет недоступен, возможно из-за нехватки памяти.|  
|HY092|Недопустимый атрибут идентификатор или параметра|Значение, указанное для аргумента *атрибут* не подходит для версии поддерживаются драйвером ODBC.|  
|HY117|Соединение будет приостановлена из-за неизвестной транзакции состояния. Только отключиться и разрешены функции, доступные только для чтения.|(DM) Дополнительные сведения о состоянии приостановки см. в разделе [функция SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Дополнительная возможность не реализована|Значение, указанное для аргумента *атрибут* был допустимым атрибутом среды ODBC для используемая версия ODBC, поддерживаемых драйвером, но не поддерживается драйвером.|  
|IM001|Драйвер не поддерживает эту функцию|(DM) драйвер, соответствующий *EnvironmentHandle* не поддерживает функцию.|  
  
## <a name="comments"></a>Комментарии  
 Список атрибутов см. в разделе [SQLSetEnvAttr](../../../odbc/reference/syntax/sqlsetenvattr-function.md). Нет никаких атрибутов драйвера среды. Если *атрибута* определяет атрибут, который возвращает строку, *ValuePtr* должен быть указателем на буфер, в который возвращается строка. Максимальная длина строки, включая байт конечное значение null, будет *BufferLength* байт.  
  
 **SQLGetEnvAttr** можно вызвать в любое время между выделении и освобождении дескриптора среды. Все атрибуты среды успешно установлены приложением для среды сохраняется до **SQLFreeHandle** будет вызван на *EnvironmentHandle* с *HandleType*установленным в значение sql_handle_env. Более одного дескриптора среды может находиться одновременно в ODBC 3 *.x*. Атрибут среды в одной среде не влияет на выделил другую среду.  
  
> [!NOTE]  
>  Атрибут среды SQL_ATTR_OUTPUT_NTS поддерживается стандартам приложениями. Когда **SQLGetEnvAttr** вызывается ODBC 3 *.x* диспетчера драйверов всегда возвращает SQL_TRUE для этого атрибута. SQL_ATTR_OUTPUT_NTS можно присвоить значение SQL_TRUE только путем вызова **SQLSetEnvAttr**.  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Возврат значения атрибута соединения|[Функция SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
|Возврат значения атрибута инструкции|[Функция SQLGetStmtAttr](../../../odbc/reference/syntax/sqlgetstmtattr-function.md)|  
|Присвоение атрибуту соединения|[Функция SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|  
|Установка атрибута среды|[Функция SQLSetEnvAttr](../../../odbc/reference/syntax/sqlsetenvattr-function.md)|  
|С помощью атрибута инструкции|[Функция SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|  
  
## <a name="see-also"></a>См. также  
 [Справочник по API-интерфейса ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)
