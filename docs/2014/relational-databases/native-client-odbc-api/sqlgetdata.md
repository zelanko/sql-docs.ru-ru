---
title: SQLGetData | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLGetData function
ms.assetid: 204848be-8787-45b4-816f-a60ac9d56fcf
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 048ee2d27445bf64839c5331627a12e012cd4123
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/13/2018
ms.locfileid: "53376516"
---
# <a name="sqlgetdata"></a>SQLGetData
  **SQLGetData** используется для получения данных результирующего набора без привязки значений столбцов. **SQLGetData** вызывается последовательно для одного столбца для извлечения больших объемов данных из столбца с **текст**, **ntext**, или **изображение** тип данных.  
  
 В приложении не обязательно выполнять привязку данных для получения данных результирующего набора. Данные любого столбца могут быть получены из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента с помощью **SQLGetData**.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Драйвер ODBC собственного клиента не поддерживает использование **SQLGetData** для получения данных в порядке произвольного столбца. Все непривязанные столбцы, обрабатываемые с **SQLGetData** должен иметь высокий порядковые номера столбцов, чем привязанные столбцы в результирующем наборе. Приложение обрабатывает данные непривязанных столбцов (начиная со столбца с наименьшим порядковым номером и заканчивая столбцом с наибольшим порядковым номером). Попытка получить данные из столбца с более низким порядковым номером приведет к ошибке. Если в приложении используются серверные курсоры для формирования сообщений о строках результирующего набора, то приложение может повторно получить текущую строку, а затем получить значение столбца. Если инструкция выполняется только для чтения, однопроходный курсор по умолчанию, необходимо повторно выполнить инструкцию для резервного копирования **SQLGetData**.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Драйвер ODBC собственного клиента точно сообщает длину **текст**, **ntext**, и **изображение** данные, полученные с помощью **SQLGetData** . Приложение может работать при *StrLen_or_IndPtr* параметр возврата быстро получении данных большой длины.  
  
> [!NOTE]  
>  Для типов больших значений *StrLen_or_IndPtr* возвращает значение SQL_NO_TOTAL в случае усечения данных.  
  
## <a name="sqlgetdata-support-for-enhanced-date-and-time-features"></a>Поддержка методом SQLGetData улучшенных функций даты и времени  
 Значения результирующих столбцов типов даты времени преобразуются, как описано в разделе [преобразования из SQL в C](../native-client-odbc-date-time/datetime-data-type-conversions-from-sql-to-c.md).  
  
 Дополнительные сведения см. в разделе [время улучшения функций даты и &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlgetdata-support-for-large-clr-udts"></a>Поддержка методом SQLGetData больших определяемых пользователем типов (UDT) в среде CLR  
 **SQLGetData** поддерживает большие определяемые пользователем типы CLR (UDT). Дополнительные сведения см. в разделе [Large CLR User-Defined типы &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="example"></a>Пример  
  
```  
SQLHDBC     hDbc = NULL;  
SQLHSTMT    hStmt = NULL;  
long        lEmpID;  
PBYTE       pPicture;  
SQLINTEGER  pIndicators[2];  
  
// Get an environment, connection, and so on.  
...  
  
// Get a statement handle and execute a command.  
SQLAllocHandle(SQL_HANDLE_STMT, hDbc, &hStmt);  
  
if (SQLExecDirect(hStmt,  
    (SQLCHAR*) "SELECT EmployeeID, Photo FROM Employees",  
    SQL_NTS) == SQL_ERROR)  
    {  
    // Handle error and return.  
    }  
  
// Retrieve data from row set.  
SQLBindCol(hStmt, 1, SQL_C_LONG, (SQLPOINTER) &lEmpID, sizeof(long),  
    &pIndicators[0]);  
  
while (SQLFetch(hStmt) == SQL_SUCCESS)  
    {  
    cout << "EmployeeID: " << lEmpID << "\n";  
  
    // Call SQLGetData to determine the amount of data that's waiting.  
    if (SQLGetData(hStmt, 2, SQL_C_BINARY, pPicture, 0, &pIndicators[1])  
        == SQL_SUCCESS_WITH_INFO)  
        {  
        cout << "Photo size: " pIndicators[1] << "\n\n";  
  
        // Get all the data at once.  
        pPicture = new BYTE[pIndicators[1]];  
        if (SQLGetData(hStmt, 2, SQL_C_DEFAULT, pPicture,  
            pIndicators[1], &pIndicators[1]) != SQL_SUCCESS)  
            {  
            // Handle error and continue.  
            }  
  
        delete [] pPicture;  
        }  
    else  
        {  
        // Handle error on attempt to get data length.  
        }  
    }  
```  
  
## <a name="see-also"></a>См. также  
 [Функция SQLGetData](https://go.microsoft.com/fwlink/?LinkId=59350)   
 [Подробные сведения о реализации API-интерфейсов ODBC](odbc-api-implementation-details.md)  
  
  
