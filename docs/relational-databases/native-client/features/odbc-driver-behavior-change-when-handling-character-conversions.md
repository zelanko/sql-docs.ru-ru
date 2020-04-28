---
title: Преобразование символов обработки изменений ODBC
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 682a232a-bf89-4849-88a1-95b2fbac1467
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 82e9e3b1ed8487e864e91edfd3067f9fb97bbb71
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81303839"
---
# <a name="odbc-driver-behavior-change-when-handling-character-conversions"></a>Изменение поведения драйвера ODBC при обработке преобразования символов
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Драйвер [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] ODBC для собственного клиента (sqlncli11. dll) изменил то, как он выполняет преобразования SQL_WCHAR * (nchar/NVARCHAR/nvarchar (max))\* и SQL_CHAR (char/varchar/нарчар (max)). При использовании драйвера Native Client ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 2012 функции ODBC, например SQLGetData, SQLBindCol и SQLBindParameter, возвращают (-4) SQL_NO_TOTAL в качестве параметра длины или индикатора. Предыдущие версии драйвера Native Client ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] возвращали значение длины, которое могло быть неверным.  
  
## <a name="sqlgetdata-behavior"></a>Поведение SQLGetData  
 Многие функции Windows позволяют указывать нулевой размер буфера, при этом возвращаемая длина является размером возвращаемых данных. Следующий вариант является стандартным для программистов Windows:  
  
```  
int iSize = 0;  
BYTE * pBuffer = NULL;  
GetMyFavoriteAPI(pBuffer, &iSize);   // Returns needed size in iSize  
pBuffer = new BYTE[iSize];   // Allocate buffer   
GetMyFavoriteAPI(pBuffer, &iSize);   // Retrieve actual data  
```  
  
 Однако **SQLGetData** не следует использовать в этом сценарии. Не следует использовать следующий вариант.  
  
```  
// bad  
int iSize = 0;  
WCHAR * pBuffer = NULL;  
SQLGetData(hstmt, SQL_W_CHAR, ...., (SQLPOINTER*)0x1, 0, &iSize);   // Get storage size needed  
pBuffer = new WCHAR[(iSize/sizeof(WCHAR)) + 1];   // Allocate buffer  
SQLGetData(hstmt, SQL_W_CHAR, ...., (SQLPOINTER*)pBuffer, iSize, &iSize);   // Retrieve data  
```  
  
 **SQLGetData** можно вызывать только для получения фрагментов фактических данных. Использование **SQLGetData** для получения размера данных не поддерживается.  
  
 Далее показано влияние изменения драйвера, которое проявляется при использовании неверного варианта. Это приложение запрашивает столбец **varchar** и привязку в юникоде (SQL_UNICODE/SQL_WCHAR):  
  
 Выбор`select convert(varchar(36), '123')`  
  
```  
SQLGetData(hstmt, SQL_WCHAR, ....., (SQLPOINTER*) 0x1, 0 , &iSize);   // Attempting to determine storage size needed  
```  
  
|Версия драйвера Native Client ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]|Итоговая длина или индикатор|Описание|  
|-----------------------------------------------------------------|---------------------------------|-----------------|  
|Native Client [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] или более ранняя версия|6|Драйвер ошибочно предположил, что преобразование CHAR в WCHAR можно было выполнить как умножение длины на 2.|  
|Native Client [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] (версия 11.0.2100.60) или более поздняя версия|-4 (SQL_NO_TOTAL)|Драйвер больше не предполагает, что преобразование типа CHAR в тип WCHAR или WCHAR в CHAR является действием ( \*умножение) 2 или (деление)/2.<br /><br /> Вызов **SQLGetData** больше не возвращает длину ожидаемого преобразования. Драйвер обнаруживает преобразование из CHAR в WCHAR или обратное преобразование и возвращает (-4) SQL_NO_TOTAL вместо *2 или /2, что могло быть неверным.|  
  
 Используйте **SQLGetData** для извлечения фрагментов данных. (Показан псевдокод).  
  
```  
while( (SQL_SUCCESS or SQL_SUCCESS_WITH_INFO) == SQLFetch(...) ) {  
   SQLNumCols(...iTotalCols...)  
   for(int iCol = 1; iCol < iTotalCols; iCol++) {  
      WCHAR* pBufOrig, pBuffer = new WCHAR[100];  
      SQLGetData(.... iCol ... pBuffer, 100, &iSize);   // Get original chunk  
      while(NOT ALL DATA RETREIVED (SQL_NO_TOTAL, ...) ) {  
         pBuffer += 50;   // Advance buffer for data retrieved  
         // May need to realloc the buffer when you reach current size  
         SQLGetData(.... iCol ... pBuffer, 100, &iSize);   // Get next chunk  
      }  
   }  
}  
```  
  
## <a name="sqlbindcol-behavior"></a>Поведение функции SQLBindCol  
 Выбор`select convert(varchar(36), '1234567890')`  
  
```  
SQLBindCol(... SQL_W_CHAR, ...)   // Only bound a buffer of WCHAR[4] - Expecting String Data Right Truncation behavior  
```  
  
|Версия драйвера Native Client ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]|Итоговая длина или индикатор|Описание|  
|-----------------------------------------------------------------|---------------------------------|-----------------|  
|Native Client [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] или более ранняя версия|20|**SQLFetch** сообщает, что в правой части данных имеется усечение.<br /><br /> Длина является длиной возращенных данных, а не того, что было сохранено (предполагается преобразование CHAR в WCHAR при помощи операции *2, что может быть неверным для глифов).<br /><br /> В буфере хранятся следующие данные: 123\0. Буфер гарантированно заканчивается на NULL.|  
|Native Client [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] (версия 11.0.2100.60) или более поздняя версия|-4 (SQL_NO_TOTAL)|**SQLFetch** сообщает, что в правой части данных имеется усечение.<br /><br /> Длина указывает -4 (SQL_NO_TOTAL), поскольку остальные данные не были преобразованы.<br /><br /> В буфере хранятся следующие данные: 123\0. - Буфер гарантированно заканчивается на NULL.|  
  
## <a name="sqlbindparameter-output-parameter-behavior"></a>SQLBindParameter (поведение параметра OUTPUT)  
 Выбор`create procedure spTest @p1 varchar(max) OUTPUT`  
  
 `select @p1 = replicate('B', 1234)`  
  
```  
SQLBindParameter(... SQL_W_CHAR, ...)   // Only bind up to first 64 characters  
```  
  
|Версия драйвера Native Client ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]|Итоговая длина или индикатор|Описание|  
|-----------------------------------------------------------------|---------------------------------|-----------------|  
|Native Client [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] или более ранняя версия|2468|**SQLFetch** больше не возвращает данные.<br /><br /> **SQLMoreResults** больше не возвращает данные.<br /><br /> Длина указывает размер данных, возвращенных с сервера, а нет тех, которые хранятся в буфере.<br /><br /> Первоначальный буфер содержит 63 байта и признак конца NULL. Буфер гарантированно заканчивается на NULL.|  
|Native Client [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] (версия 11.0.2100.60) или более поздняя версия|-4 (SQL_NO_TOTAL)|**SQLFetch** больше не возвращает данные.<br /><br /> **SQLMoreResults** больше не возвращает данные.<br /><br /> Длина указывает (-4) SQL_NO_TOTAL, поскольку остальные данные не были преобразованы.<br /><br /> Первоначальный буфер содержит 63 байта и признак конца NULL. Буфер гарантированно заканчивается на NULL.|  
  
## <a name="performing-char-and-wchar-conversions"></a>Выполнение преобразований CHAR и WCHAR  
 Драйвер Native Client ODBC [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] предлагает несколько вариантов выполнения преобразования CHAR и WCHAR. Логика аналогична манипуляции с большими двоичными объектами (varchar (max), nvarchar (max),...):  
  
-   Данные сохраняются или усекаются в указанном буфере при привязке с помощью **SQLBindCol** или **SQLBindParameter**.  
  
-   Если не выполнить привязку, можно получить данные в блоках с помощью **SQLGetData** и **метод SQLParamData**.  
  
## <a name="see-also"></a>См. также:  
 [Компоненты собственного клиента SQL Server](../../../relational-databases/native-client/features/sql-server-native-client-features.md)  
  
  
