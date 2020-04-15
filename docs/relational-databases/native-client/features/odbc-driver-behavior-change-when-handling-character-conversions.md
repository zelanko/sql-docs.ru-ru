---
title: Преобразование ODBC изменения символа
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303839"
---
# <a name="odbc-driver-behavior-change-when-handling-character-conversions"></a>Изменение поведения драйвера ODBC при обработке преобразования символов
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Драйвер [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] ODBC родного клиента (S'LNCLI11.dll) изменил то, как он делает SQL_WCHAR » (NCHAR/NVARCHAR/NVARCHAR (MAX)) и SQL_CHAR\* (CHAR/VARCHAR/NARCHAR(MAX)) конверсий. При использовании драйвера Native Client ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 2012 функции ODBC, например SQLGetData, SQLBindCol и SQLBindParameter, возвращают (-4) SQL_NO_TOTAL в качестве параметра длины или индикатора. Предыдущие версии драйвера Native Client ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] возвращали значение длины, которое могло быть неверным.  
  
## <a name="sqlgetdata-behavior"></a>Поведение SQLGetData  
 Многие функции Windows позволяют указывать нулевой размер буфера, при этом возвращаемая длина является размером возвращаемых данных. Следующий вариант является стандартным для программистов Windows:  
  
```  
int iSize = 0;  
BYTE * pBuffer = NULL;  
GetMyFavoriteAPI(pBuffer, &iSize);   // Returns needed size in iSize  
pBuffer = new BYTE[iSize];   // Allocate buffer   
GetMyFavoriteAPI(pBuffer, &iSize);   // Retrieve actual data  
```  
  
 Тем не менее, в этом сценарии не следует использовать **S'LGetData.** Не следует использовать следующий вариант.  
  
```  
// bad  
int iSize = 0;  
WCHAR * pBuffer = NULL;  
SQLGetData(hstmt, SQL_W_CHAR, ...., (SQLPOINTER*)0x1, 0, &iSize);   // Get storage size needed  
pBuffer = new WCHAR[(iSize/sizeof(WCHAR)) + 1];   // Allocate buffer  
SQLGetData(hstmt, SQL_W_CHAR, ...., (SQLPOINTER*)pBuffer, iSize, &iSize);   // Retrieve data  
```  
  
 **SLGetData** можно вызвать только для получения фрагментов фактических данных. Использование **S'LGetData** для получения размера данных не поддерживается без поддержки.  
  
 Далее показано влияние изменения драйвера, которое проявляется при использовании неверного варианта. Это приложение запрашивает столбец **varchar** и привязывается к Unicode (SQL_UNICODE/SQL_WCHAR):  
  
 Запроса:`select convert(varchar(36), '123')`  
  
```  
SQLGetData(hstmt, SQL_WCHAR, ....., (SQLPOINTER*) 0x1, 0 , &iSize);   // Attempting to determine storage size needed  
```  
  
|Версия драйвера Native Client ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]|Итоговая длина или индикатор|Описание|  
|-----------------------------------------------------------------|---------------------------------|-----------------|  
|Native Client [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] или более ранняя версия|6|Драйвер ошибочно предположил, что преобразование CHAR в WCHAR можно было выполнить как умножение длины на 2.|  
|Native Client [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] (версия 11.0.2100.60) или более поздняя версия|-4 (SQL_NO_TOTAL)|Драйвер больше не предполагает, что преобразование из CHAR в WCHAR \*или WCHAR в CHAR является (умножение) 2 или (разделить)/2 действие.<br /><br /> Вызов **S'LGetData** больше не возвращает продолжительность ожидаемого преобразования. Драйвер обнаруживает преобразование из CHAR в WCHAR или обратное преобразование и возвращает (-4) SQL_NO_TOTAL вместо *2 или /2, что могло быть неверным.|  
  
 Для извлечения фрагментов данных используйте **s'LGetData.** (Показан псевдокод).  
  
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
 Запроса:`select convert(varchar(36), '1234567890')`  
  
```  
SQLBindCol(... SQL_W_CHAR, ...)   // Only bound a buffer of WCHAR[4] - Expecting String Data Right Truncation behavior  
```  
  
|Версия драйвера Native Client ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]|Итоговая длина или индикатор|Описание|  
|-----------------------------------------------------------------|---------------------------------|-----------------|  
|Native Client [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] или более ранняя версия|20|**S'LFetch** сообщает, что есть усечение на правой стороне данных.<br /><br /> Длина является длиной возращенных данных, а не того, что было сохранено (предполагается преобразование CHAR в WCHAR при помощи операции *2, что может быть неверным для глифов).<br /><br /> В буфере хранятся следующие данные: 123\0. Буфер гарантированно заканчивается на NULL.|  
|Native Client [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] (версия 11.0.2100.60) или более поздняя версия|-4 (SQL_NO_TOTAL)|**S'LFetch** сообщает, что есть усечение на правой стороне данных.<br /><br /> Длина указывает -4 (SQL_NO_TOTAL), поскольку остальные данные не были преобразованы.<br /><br /> В буфере хранятся следующие данные: 123\0. - Буфер гарантированно заканчивается на NULL.|  
  
## <a name="sqlbindparameter-output-parameter-behavior"></a>SQLBindParameter (поведение параметра OUTPUT)  
 Запроса:`create procedure spTest @p1 varchar(max) OUTPUT`  
  
 `select @p1 = replicate('B', 1234)`  
  
```  
SQLBindParameter(... SQL_W_CHAR, ...)   // Only bind up to first 64 characters  
```  
  
|Версия драйвера Native Client ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]|Итоговая длина или индикатор|Описание|  
|-----------------------------------------------------------------|---------------------------------|-----------------|  
|Native Client [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] или более ранняя версия|2468|**S'LFetch** возвращает больше не доступные данные.<br /><br /> **S'LMoreResults** возвращает больше не доступные данные.<br /><br /> Длина указывает размер данных, возвращенных с сервера, а нет тех, которые хранятся в буфере.<br /><br /> Первоначальный буфер содержит 63 байта и признак конца NULL. Буфер гарантированно заканчивается на NULL.|  
|Native Client [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] (версия 11.0.2100.60) или более поздняя версия|-4 (SQL_NO_TOTAL)|**S'LFetch** возвращает больше не доступные данные.<br /><br /> **S'LMoreResults** возвращает больше не доступные данные.<br /><br /> Длина указывает (-4) SQL_NO_TOTAL, поскольку остальные данные не были преобразованы.<br /><br /> Первоначальный буфер содержит 63 байта и признак конца NULL. Буфер гарантированно заканчивается на NULL.|  
  
## <a name="performing-char-and-wchar-conversions"></a>Выполнение преобразований CHAR и WCHAR  
 Драйвер Native Client ODBC [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] предлагает несколько вариантов выполнения преобразования CHAR и WCHAR. Логика похожа на манипулирование капли (varchar (макс), nvarchar (макс), ...):  
  
-   Данные сохраняются или усечены в указанном буфере при связывании с **S'LBindCol** или **S'LBindParameter.**  
  
-   Если вы не связываетесь, вы можете получить данные в кусках с помощью **S'LGetData** и **S'LParamData**.  
  
## <a name="see-also"></a>См. также:  
 [Компоненты собственного клиента SQL Server](../../../relational-databases/native-client/features/sql-server-native-client-features.md)  
  
  
