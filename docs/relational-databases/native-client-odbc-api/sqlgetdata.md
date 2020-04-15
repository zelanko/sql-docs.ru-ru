---
title: СЗЛГетДата (англ.) Документы Майкрософт
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLGetData function
ms.assetid: 204848be-8787-45b4-816f-a60ac9d56fcf
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 5ebda3de96cbd9a4a1ceadd62093420cc372a169
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302165"
---
# <a name="sqlgetdata"></a>SQLGetData
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Для извлечения данных набора результатов без обязательных значений столбца используется **s'LGetData.** **СЗЛГетДата** может быть последовательно вызвана на одну и ту же колонку для извлечения больших объемов данных из столбца с **текстом,** **ntext**или типом данных **изображения.**  
  
 В приложении не обязательно выполнять привязку данных для получения данных результирующего набора. Данные любого столбца можно [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] получить из драйвера NATIVE Client ODBC с помощью **s'LGetData.**  
  
 Драйвер [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC не поддерживает использование **S'LGetData** для получения данных в порядке случайного столбца. Все несвязанные столбцы, обработанные **с помощью S'LGetData,** должны иметь более высокие ординаты столбца, чем связанные столбцы в наборе результатов. Приложение обрабатывает данные непривязанных столбцов (начиная со столбца с наименьшим порядковым номером и заканчивая столбцом с наибольшим порядковым номером). Попытка получить данные из столбца с более низким порядковым номером приведет к ошибке. Если в приложении используются серверные курсоры для формирования сообщений о строках результирующего набора, то приложение может повторно получить текущую строку, а затем получить значение столбца. Если выписка выполняется только по умолчанию, только для чтения, только вперед, необходимо повторно выполнить выписку для резервного копирования **s'LGetData.**  
  
 Драйвер [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC точно сообщает длину **текста,** **ntext**и данные **изображений,** полученные с помощью **S'LGetData.** Приложение может эффективно использовать *StrLen_or_IndPtr* возврата параметров для быстрого получения длинных данных.  
  
> [!NOTE]  
>  Для больших типов значений *StrLen_or_IndPtr* будет возвращать SQL_NO_TOTAL в случае усечения данных.  
  
## <a name="sqlgetdata-support-for-enhanced-date-and-time-features"></a>Поддержка методом SQLGetData улучшенных функций даты и времени  
 Значения столбца результатов типов даты/времени преобразуются, как описано в [преобразованиях от S'L к C.](../../relational-databases/native-client-odbc-date-time/datetime-data-type-conversions-from-sql-to-c.md)  
  
 Для получения дополнительной информации см [&#41;&#40;. ](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md)  
  
## <a name="sqlgetdata-support-for-large-clr-udts"></a>Поддержка методом SQLGetData больших определяемых пользователем типов (UDT) в среде CLR  
 **S'LGetData** поддерживает большие типы, определяемые пользователями CLR (UDT). Для получения дополнительной информации смотрите [большие типы, определяемые пользователями CLR, &#40;&#41;ODBC. ](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md)  
  
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
  
## <a name="see-also"></a>См. также:  
 [Функция S'LGetData](https://go.microsoft.com/fwlink/?LinkId=59350)   
 [ODBC API Implementation Details](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
