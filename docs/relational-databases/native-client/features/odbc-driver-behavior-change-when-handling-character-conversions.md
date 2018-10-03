---
title: Изменение поведения драйвера ODBC при обработке преобразования символов | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 682a232a-bf89-4849-88a1-95b2fbac1467
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: b48a22e440889012dd16c8e60142f5b984cb4e7e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47828582"
---
# <a name="odbc-driver-behavior-change-when-handling-character-conversions"></a>Изменение поведения драйвера ODBC при обработке преобразования символов
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] Драйвер ODBC Native Client (SQLNCLI11.dll) изменен, как он выполняет SQL_WCHAR * (NCHAR/NVARCHAR/NVARCHAR(MAX)) и SQL_CHAR\* (CHAR/VARCHAR/NARCHAR(MAX)) преобразования. При использовании драйвера Native Client ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 2012 функции ODBC, например SQLGetData, SQLBindCol и SQLBindParameter, возвращают (-4) SQL_NO_TOTAL в качестве параметра длины или индикатора. Предыдущие версии драйвера Native Client ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] возвращали значение длины, которое могло быть неверным.  
  
## <a name="sqlgetdata-behavior"></a>Поведение SQLGetData  
 Многие функции Windows позволяют указывать нулевой размер буфера, при этом возвращаемая длина является размером возвращаемых данных. Следующий вариант является стандартным для программистов Windows:  
  
```  
int iSize = 0;  
BYTE * pBuffer = NULL;  
GetMyFavoriteAPI(pBuffer, &iSize);   // Returns needed size in iSize  
pBuffer = new BYTE[iSize];   // Allocate buffer   
GetMyFavoriteAPI(pBuffer, &iSize);   // Retrieve actual data  
```  
  
 Тем не менее **SQLGetData** не следует использовать в этом сценарии. Не следует использовать следующий вариант.  
  
```  
// bad  
int iSize = 0;  
WCHAR * pBuffer = NULL;  
SQLGetData(hstmt, SQL_W_CHAR, ...., (SQLPOINTER*)0x1, 0, &iSize);   // Get storage size needed  
pBuffer = new WCHAR[(iSize/sizeof(WCHAR)) + 1];   // Allocate buffer  
SQLGetData(hstmt, SQL_W_CHAR, ...., (SQLPOINTER*)pBuffer, iSize, &iSize);   // Retrieve data  
```  
  
 **SQLGetData** может вызываться только для получения фрагментов фактических данных. С помощью **SQLGetData** для получения размера данных не поддерживается.  
  
 Далее показано влияние изменения драйвера, которое проявляется при использовании неверного варианта. Это приложение запрашивает **varchar** столбец и привязку в кодировке Юникод (SQL_UNICODE/SQL_WCHAR):  
  
 Запрос:  `select convert(varchar(36), '123')`  
  
```  
SQLGetData(hstmt, SQL_WCHAR, ….., (SQLPOINTER*) 0x1, 0 , &iSize);   // Attempting to determine storage size needed  
```  
  
|Версия драйвера Native Client ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]|Итоговая длина или индикатор|Описание|  
|-----------------------------------------------------------------|---------------------------------|-----------------|  
|Native Client [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] или более ранняя версия|6|Драйвер ошибочно предположил, что преобразование CHAR в WCHAR можно было выполнить как умножение длины на 2.|  
|Native Client [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] (версия 11.0.2100.60) или более поздняя версия|-4 (SQL_NO_TOTAL)|Драйвер больше не предполагается, что преобразование из CHAR в WCHAR или из WCHAR в CHAR (умножение) \*2 или (деления) / 2 действия.<br /><br /> Вызов **SQLGetData** больше не возвращает длину ожидаемого преобразования. Драйвер обнаруживает преобразование из CHAR в WCHAR или обратное преобразование и возвращает (-4) SQL_NO_TOTAL вместо *2 или /2, что могло быть неверным.|  
  
 Используйте **SQLGetData** для получения фрагментов данных. (Показан псевдокод).  
  
```  
while( (SQL_SUCCESS or SQL_SUCCESS_WITH_INFO) == SQLFetch(...) ) {  
   SQLNumCols(...iTotalCols...)  
   for(int iCol = 1; iCol < iTotalCols; iCol++) {  
      WCHAR* pBufOrig, pBuffer = new WCHAR[100];  
      SQLGetData(.... iCol … pBuffer, 100, &iSize);   // Get original chunk  
      while(NOT ALL DATA RETREIVED (SQL_NO_TOTAL, ...) ) {  
         pBuffer += 50;   // Advance buffer for data retrieved  
         // May need to realloc the buffer when you reach current size  
         SQLGetData(.... iCol … pBuffer, 100, &iSize);   // Get next chunk  
      }  
   }  
}  
```  
  
## <a name="sqlbindcol-behavior"></a>Поведение функции SQLBindCol  
 Запрос:  `select convert(varchar(36), '1234567890')`  
  
```  
SQLBindCol(… SQL_W_CHAR, …)   // Only bound a buffer of WCHAR[4] – Expecting String Data Right Truncation behavior  
```  
  
|Версия драйвера Native Client ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]|Итоговая длина или индикатор|Описание|  
|-----------------------------------------------------------------|---------------------------------|-----------------|  
|Native Client [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] или более ранняя версия|20|**SQLFetch** сообщает о наличии усечения с правой стороны данных.<br /><br /> Длина является длиной возращенных данных, а не того, что было сохранено (предполагается преобразование CHAR в WCHAR при помощи операции *2, что может быть неверным для глифов).<br /><br /> В буфере хранятся следующие данные: 123\0. Буфер гарантированно заканчивается на NULL.|  
|Native Client [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] (версия 11.0.2100.60) или более поздняя версия|-4 (SQL_NO_TOTAL)|**SQLFetch** сообщает о наличии усечения с правой стороны данных.<br /><br /> Длина указывает -4 (SQL_NO_TOTAL), поскольку остальные данные не были преобразованы.<br /><br /> В буфере хранятся следующие данные: 123\0. - Буфер гарантированно заканчивается на NULL.|  
  
## <a name="sqlbindparameter-output-parameter-behavior"></a>SQLBindParameter (поведение параметра OUTPUT)  
 Запрос:  `create procedure spTest @p1 varchar(max) OUTPUT`  
  
 `select @p1 = replicate('B', 1234)`  
  
```  
SQLBindParameter(… SQL_W_CHAR, …)   // Only bind up to first 64 characters  
```  
  
|Версия драйвера Native Client ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]|Итоговая длина или индикатор|Описание|  
|-----------------------------------------------------------------|---------------------------------|-----------------|  
|Native Client [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] или более ранняя версия|2468|**SQLFetch** возвращает нет доступных данных.<br /><br /> **SQLMoreResults** возвращает нет доступных данных.<br /><br /> Длина указывает размер данных, возвращенных с сервера, а нет тех, которые хранятся в буфере.<br /><br /> Первоначальный буфер содержит 63 байта и признак конца NULL. Буфер гарантированно заканчивается на NULL.|  
|Native Client [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] (версия 11.0.2100.60) или более поздняя версия|-4 (SQL_NO_TOTAL)|**SQLFetch** возвращает нет доступных данных.<br /><br /> **SQLMoreResults** возвращает нет доступных данных.<br /><br /> Длина указывает (-4) SQL_NO_TOTAL, поскольку остальные данные не были преобразованы.<br /><br /> Первоначальный буфер содержит 63 байта и признак конца NULL. Буфер гарантированно заканчивается на NULL.|  
  
## <a name="performing-char-and-wchar-conversions"></a>Выполнение преобразований CHAR и WCHAR  
 Драйвер Native Client ODBC [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] предлагает несколько вариантов выполнения преобразования CHAR и WCHAR. Логика этих преобразований похожа на обработку больших двоичных объектов (varchar(max), nvarchar(max), …):  
  
-   Данные сохранены или усекаются в указанный буфер при привязке с помощью **SQLBindCol** или **SQLBindParameter**.  
  
-   Если привязка не выполняется, фрагменты данных можно получить с помощью **SQLGetData** и **SQLParamData**.  
  
## <a name="see-also"></a>См. также  
 [Компоненты SQL Server Native Client](../../../relational-databases/native-client/features/sql-server-native-client-features.md)  
  
  
