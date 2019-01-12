---
title: bcp_bind | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apiname:
- bcp_bind
apilocation:
- sqlncli11.dll
apitype: DLLExport
helpviewer_keywords:
- bcp_bind function
ms.assetid: 6e335a5c-64b2-4bcf-a88f-35dc9393f329
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 0574683e2f77efe0654a8c3193bee2f499a9400b
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/09/2019
ms.locfileid: "54135744"
---
# <a name="bcpbind"></a>bcp_bind
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Привязывает данные программной переменной к столбцу таблицы для массового копирования в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
RETCODE bcp_bind (  
        HDBC hdbc,   
        LPCBYTE pData,  
        INT cbIndicator,  
        DBINT cbData,  
        LPCBYTE pTerm,  
        INT cbTerm,  
        INT eDataType,  
        INT idxServerCol);  
```  
  
## <a name="arguments"></a>Аргументы  
 *HDBC*  
 Дескриптор соединения ODBC с поддержкой массового копирования.  
  
 *pData*  
 Указатель на копируемые данные. Если *eDataType* является SQLTEXT, SQLNTEXT, SQLXML, SQLUDT, SQLCHARACTER, SQLVARCHAR, SQLVARBINARY, SQLBINARY, SQLNCHAR или SQLIMAGE, *pData* может иметь значение NULL. Значение NULL *pData* означает, что данные большого будет отправлено для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] частями с помощью функции [bcp_moretext](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-moretext.md). Пользователь должен задать только для *pData* значение NULL, если столбец, соответствующий связанному полю — это столбец BLOB-ОБЪЕКТОВ, в противном случае **bcp_bind** завершится ошибкой.  
  
 Если в данных присутствуют признаки, они размещаются в памяти непосредственно перед данными. *PData* указывает на переменную признака, в данном случае и ширина признака, параметр *cbIndicator* , используется при массовом копировании для адресации пользовательских данных правильно.  
  
 *cbIndicator*  
 Ширина индикатора в байтах или значение NULL для данных столбца. Допускаются следующие значения длины признака: 0 (если признак не используется), 1, 2, 4 или 8. Признаки размещаются в памяти непосредственно перед данными. Например, следующее определение типа структуры можно использовать для вставки целочисленных значений в таблицу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью массового копирования:  
  
```  
typedef struct tagBCPBOUNDINT  
    {  
    int iIndicator;  
    int Value;  
    } BCPBOUNDINT;  
```  
  
 В этом примере *pData* параметр должен быть установлен на адрес объявленного экземпляра структуры, адреса элемента *iIndicator* член структуры. *CbIndicator* будет иметь значение для размера типа integer (sizeof(int)) и *cbData* параметр будет иметь значение для размера типа integer (sizeof(int)). Чтобы выполнить массовое копирование, значение строки на сервер, содержащий значение NULL для связанного столбца, значение экземпляра *iIndicator* член должен быть равным SQL_NULL_DATA.  
  
 *cbData*  
 Количество байт данных в программной переменной, исключая любую длину, NULL-индикатор или признак конца.  
  
 Установка *cbData* значения SQL_NULL_DATA означает, что все строки, скопированные на сервер содержит значение NULL для столбца.  
  
 Установка *cbData* значения SQL_VARLEN_DATA указывает, что система будет использовать строковый признак конца или другой метод, чтобы определить длину данных копирования.  
  
 Для типов данных фиксированной длины, например для целых чисел, система определяет длину данных на основе типа. Таким образом, для типов данных фиксированной длины *cbData* может иметь значение SQL_VARLEN_DATA или длину данных.  
  
 Для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] символьных и двоичных типов данных *cbData* может быть SQL_VARLEN_DATA, SQL_NULL_DATA, 0 или положительное значение. Если *cbData* имеет значение SQL_VARLEN_DATA, система использует либо признак длины, null (при его наличии), либо последовательность с признаком конца для определения длины данных. Если представлено и то, и другое, система использует то значение, которое приводит к наименьшему объему копируемых данных. Если *cbData* имеет значение SQL_VARLEN_DATA, тип данных столбца является [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] указан символ или двоичного типа и ни признак длины, ни последовательность с признаком конца, система возвращает сообщение об ошибке.  
  
 Если *cbData* равно 0 или положительное значение, система использует *cbData* как длину данных. Тем не менее если в дополнение к положительному *cbData* предоставляется значение, последовательность длины или признака конца, то система определяет длину данных с помощью метода, который вычисляет наименьший размер копируемых данных.  
  
 *CbData* значение параметра представляет число байтов данных. Если символьные данные представлены строкой знаков в Юникоде, то положительное *cbData* значение параметра представляет число символов, умноженное на размер в байтах каждого символа.  
  
 *pTerm*  
 Указатель на байтовый шаблон, если таковой имеется, являющийся признаком конца программной переменной. Например, строки ANSI и MBCS C обычно имеют 1-байтовый признаки конца строки (\0).  
  
 Если признак конца переменной отсутствует, присвойте *pTerm* значение NULL.  
  
 Для обозначения символа конца строки в качестве признака конца программной переменной в языке C можно использовать пустую строку (""). Так как пустая строка, завершающаяся нулем, составляет один байт (байт признака конца строки сам), задайте *cbTerm* 1. Например, чтобы указать, что строка, содержащаяся в *szName* заканчивается нулевым байтом и знак завершения, что следует использовать для указания длины:  
  
```  
bcp_bind(hdbc, szName, 0,  
   SQL_VARLEN_DATA, "", 1,  
   SQLCHARACTER, 2)  
```  
  
 Форму вариант этого примера может означать, что 15 символов, копируемых из *szName* переменной во второй столбец связанной таблицы:  
  
```  
bcp_bind(hdbc, szName, 0, 15,   
   NULL, 0, SQLCHARACTER, 2)  
```  
  
 При необходимости API-интерфейс массового копирования выполнит преобразование символов из Юникода в многобайтовую кодировку (MBCS). Убедитесь, что правильно задана строка байтов признака конца и количество байт в строке. Например, чтобы указать, что строка, содержащаяся в *szName* строка расширенных символов в Юникоде, оканчивающихся значением нулевого символа Юникода:  
  
```  
bcp_bind(hdbc, szName, 0,   
   SQL_VARLEN_DATA, L"",  
   sizeof(WCHAR), SQLNCHAR, 2)  
```  
  
 Если значение границы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] столбец содержит расширенные символы, не выполняют никаких преобразований на [bcp_sendrow](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md). Если столбец [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имеет символьный тип в кодировке MBCS, при передаче данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполняется преобразование расширенных символов в несколько символов.  
  
 *cbTerm*  
 Количество байт в признаке конца программной переменной, если такой имеется. Если признак конца переменной отсутствует, присвойте *cbTerm* 0.  
  
 *eDataType*  
 Тип данных языка C для программной переменной. Данные в программной переменной преобразуются в тип столбца базы данных. Если этот параметр равен 0, преобразование не выполняется.  
  
 *EDataType* перечисляется [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] токенами типов данных в файле sqlncli.h, не перечислителях типов данных ODBC C. Например, можно задать целое двухбайтовое значение ODBC типа SQL_C_SHORT с помощью типа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQLINT2.  
  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] появилась поддержка SQLXML и SQLUDT токенами типов данных в **_eDataType_** регистр.  
 
 В приведенной ниже таблице перечислены допустимые перечисляемые типы данных и соответствующие типы данных C в ODBC.
  
|eDataType|Тип C|  
|-----------------------|------------|  
|SQLTEXT|char *|  
|SQLNTEXT|wchar_t *|  
|SQLCHARACTER|char *|  
|SQLBIGCHAR|char *|  
|SQLVARCHAR|char *|  
|SQLBIGVARCHAR|char *|  
|SQLNCHAR|wchar_t *|  
|SQLNVARCHAR|wchar_t *|  
|SQLBINARY|unsigned char *|  
|SQLBIGBINARY|unsigned char *|  
|SQLVARBINARY|unsigned char *|  
|SQLBIGVARBINARY|unsigned char *|  
|SQLBIT|char;|  
|SQLBITN|char;|  
|SQLINT1|char;|  
|SQLINT2|short int|  
|SQLINT4|ssNoversion|  
|SQLINT8|_int64|  
|SQLINTN|*cbIndicator*<br /> 1: SQLINT1<br /> 2. SQLINT2<br /> 4. SQLINT4<br /> 8. SQLINT8|  
|SQLFLT4|FLOAT|  
|SQLFLT8|FLOAT|  
|SQLFLTN|*cbIndicator*<br /> 4. SQLFLT4<br /> 8. SQLFLT8|  
|SQLDECIMALN|SQL_NUMERIC_STRUCT|  
|SQLNUMERICN|SQL_NUMERIC_STRUCT|  
|SQLMONEY|DBMONEY|  
|SQLMONEY4|DBMONEY4|  
|SQLMONEYN|*cbIndicator*<br /> 4. SQLMONEY4<br /> 8. SQLMONEY|  
|SQLTIMEN|SQL_SS_TIME2_STRUCT|  
|SQLDATEN|SQL_DATE_STRUCT|  
|SQLDATETIM4|DBDATETIM4|  
|SQLDATETIME|DBDATETIME|  
|SQLDATETIMN|*cbIndicator*<br /> 4. SQLDATETIM4<br /> 8. SQLDATETIME|  
|SQLDATETIME2N|SQL_TIMESTAMP_STRUCT|  
|SQLDATETIMEOFFSETN|SQL_SS_TIMESTAMPOFFSET_STRUCT|  
|SQLIMAGE|unsigned char *|  
|SQLUDT|unsigned char *|  
|SQLUNIQUEID|SQLGUID|  
|SQLVARIANT|*Любой тип данных, кроме следующих:*<br />— text<br />— ntext<br />— image<br />— varchar(max)<br />— varbinary(max)<br />— nvarchar(max)<br />— xml<br />— timestamp|  
|SQLXML|*Поддерживаемые типы данных C:*<br />— char *<br />— wchar_t *<br />— unsigned char *|  
  
 *idxServerCol*  
 Порядковый номер столбца в таблице базы данных, в которую копируются данные. Первый столбец в таблице имеет порядковый номер 1. Порядковый номер столбца возвращается функцией [SQLColumns](../../relational-databases/native-client-odbc-api/sqlcolumns.md).  
  
## <a name="returns"></a>Возвращает  
 SUCCEED или FAIL.  
  
## <a name="remarks"></a>Примечания  
 Используйте **bcp_bind** быстрый и эффективный способ копирования данных из программной переменной в таблицу в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Вызовите [bcp_init](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-init.md) перед вызовом этой или любой другой функции массового копирования. Вызов **bcp_init** задает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] целевой таблицы для массового копирования. При вызове **bcp_init** для использования с **bcp_bind** и [bcp_sendrow](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md), **bcp_init** _szDataFile_параметр, указывающий файл данных имеет значение NULL; **bcp_init**_eDirection_ параметр имеет значение DB_IN.  
  
 Сделать отдельного **bcp_bind** вызова для каждого столбца в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] таблицы, в которую требуется скопировать. После необходимого **bcp_bind** вызовы были внесены, а затем вызовите **bcp_sendrow** отправлять строки данных из программной переменной в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Повторная привязка столбца не поддерживается.  
  
 При необходимости [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для фиксации уже полученные строки, вызовите [bcp_batch](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-batch.md). Например, вызвать **bcp_batch** один раз для каждой 1 000 вставленных строк или через любой другой интервал.  
  
 Если больше нет строк для вставки, вызовите [bcp_done](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-done.md). Несоблюдение этого правила приведет к ошибке.  
  
 Настройки параметров управления, указанный с помощью [bcp_control](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-control.md), не оказывают влияния на **bcp_bind** передачу строк.  
  
 Если *pData* для столбца имеет значение NULL, так как его значение будет предоставлено вызовами [bcp_moretext](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-moretext.md), любой последующий столбец со *eDataType* присвоено SQLTEXT, SQLNTEXT, SQLXML, SQLUDT, SQLCHARACTER, SQLVARCHAR, SQLVARBINARY, SQLBINARY, SQLNCHAR или SQLIMAGE должен быть также связан с *pData* присваивается значение NULL, и их значения, также должен быть указан при вызове **bcp_moretext**.  
  
 Для новых типов больших значений таких как **varchar(max)**, **varbinary(max)**, или **nvarchar(max)**, можно использовать значения SQLCHARACTER, SQLVARCHAR, SQLVARBINARY, SQLBINARY, и КАЧЕСТВЕ индикаторов типа в *eDataType* параметра.  
  
 Если *cbTerm* является не равен 0, любое значение (1, 2, 4 или 8) является допустимым для префикса (*cbIndicator*). В этом случае [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client будет искать признак конца, вычислять его длину данных признак конца (*я*) и задайте *cbData* наименьшее значение i и значение префикс.  
  
 Если *cbTerm* равно 0 и *cbIndicator* (префикс) не является 0, *cbIndicator* должна быть 8. Восьмибайтовый префикс может принимать следующие значения.  
  
-   0xFFFFFFFFFFFFFFFF означает значение NULL для поля.  
  
-   0xFFFFFFFFFFFFFFFE рассматривается как специальное значение префикса, которое используется для эффективной отправки на сервер данных, разбитых на фрагменты. Данные со специальным префиксом имеют следующий формат.  
  
-   < специальный_префикс > \<0 или больше ФРАГМЕНТОВ_ДАННЫХ >< нулевой_фрагмент > где:  
  
-   СПЕЦИАЛЬНЫЙ_ПРЕФИКС имеет значение 0xFFFFFFFFFFFFFFFE.  
  
-   ФРАГМЕНТ_ДАННЫХ является 4-байтовым префиксом, содержащим длину фрагмента, за которым следуют фактические данные, длина которых задана 4-байтовым префиксом.  
  
-   НУЛЕВОЙ_ФРАГМЕНТ является 4-байтовым значением, содержащим все нули (00000000), которое указывает конец данных.  
  
-   Любая другая 8-байтовая длина рассматривается как длина обычных данных.  
  
 Вызов [bcp_columns](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-columns.md) при использовании **bcp_bind** приводит к ошибке.  
  
## <a name="bcpbind-support-for-enhanced-date-and-time-features"></a>Поддержка функцией bcp_bind улучшенных возможностей даты и времени  
 Сведения о типах, используемых с *eDataType* параметров для типов даты и времени, см. в разделе [изменения массового копирования для типов усиленной даты и времени &#40;OLE DB и ODBC&#41;](../../relational-databases/native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md).  
  
 Дополнительные сведения см. в разделе [время улучшения функций даты и &#40;ODBC&#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="example"></a>Пример  
  
```  
#include sql.h  
#include sqlext.h  
#include odbcss.h  
// Variables like henv not specified.  
HDBC      hdbc;  
char         szCompanyName[MAXNAME];  
DBINT      idCompany;  
DBINT      nRowsProcessed;  
DBBOOL      bMoreData;  
char*      pTerm = "\t\t";  
  
// Application initiation, get an ODBC environment handle, allocate the  
// hdbc, and so on.  
...   
  
// Enable bulk copy prior to connecting on allocated hdbc.  
SQLSetConnectAttr(hdbc, SQL_COPT_SS_BCP, (SQLPOINTER) SQL_BCP_ON,  
   SQL_IS_INTEGER);  
  
// Connect to the data source; return on error.  
if (!SQL_SUCCEEDED(SQLConnect(hdbc, _T("myDSN"), SQL_NTS,  
   _T("myUser"), SQL_NTS, _T("myPwd"), SQL_NTS)))  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Initialize bcp.   
if (bcp_init(hdbc, "comdb..accounts_info", NULL, NULL  
   DB_IN) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Bind program variables to table columns.   
if (bcp_bind(hdbc, (LPCBYTE) &idCompany, 0, sizeof(DBINT), NULL, 0,  
   SQLINT4, 1)    == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
if (bcp_bind(hdbc, (LPCBYTE) szCompanyName, 0, SQL_VARLEN_DATA,  
   (LPCBYTE) pTerm, strnlen(pTerm, sizeof(pTerm)), SQLCHARACTER, 2) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
while (TRUE)  
   {  
   // Retrieve and process program data.   
   if ((bMoreData = getdata(&idCompany, szCompanyName)) == TRUE)  
      {  
      // Send the data.   
      if (bcp_sendrow(hdbc) == FAIL)  
         {  
         // Raise error and return.  
         return;  
         }  
      }  
   else  
      {  
      // Break out of loop.  
      break;  
      }  
   }  
  
// Terminate the bulk copy operation.  
if ((nRowsProcessed = bcp_done(hdbc)) == -1)  
   {  
   printf_s("Bulk-copy unsuccessful.\n");  
   return;  
   }  
  
printf_s("%ld rows copied.\n", nRowsProcessed);  
```  
  
## <a name="see-also"></a>См. также  
 [Функции массового копирования](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
