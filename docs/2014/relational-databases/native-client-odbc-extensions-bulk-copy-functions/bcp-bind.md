---
title: bcp_bind | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_bind
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_bind function
ms.assetid: 6e335a5c-64b2-4bcf-a88f-35dc9393f329
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 711c82bb627ca9ad1620cf1e11fdbc9dfa5f4351
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "63140561"
---
# <a name="bcp_bind"></a>bcp_bind
  Привязывает данные программной переменной к столбцу таблицы для массового копирования в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
RETCODE bcp_bind (  
HDBC   
hdbc  
,   
LPCBYTE   
pData  
,  
INT   
cbIndicator  
,  
DBINT   
cbData  
,  
LPCBYTE   
pTerm  
,  
INT   
cbTerm  
,  
INT   
eDataType  
,  
INT   
idxServerCol  
);  
  
```  
  
## <a name="arguments"></a>Аргументы  
 *hdbc*  
 Дескриптор соединения ODBC с поддержкой массового копирования.  
  
 *pData*  
 Указатель на копируемые данные. Если *eDataType* имеет значение SQLTEXT, SQLNTEXT, SQLXML, SQLUDT, SQLCHARACTER, SQLVARCHAR, SQLVARBINARY, SqlBinary, SQLNCHAR или SQLIMAGE, *pData* может быть равен null. ЗНАЧЕНИЕ типа *pData* , указывающее, что значения длинных данных будут [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] отправляться в блоках с помощью [bcp_moretext](bcp-moretext.md). Пользователь должен задать для *pData* значение null, если столбец, соответствующий привязанному к пользователю полю, является столбцом большого двоичного объекта, иначе **bcp_bind** завершится ошибкой.  
  
 Если в данных присутствуют признаки, они размещаются в памяти непосредственно перед данными. Параметр *pData* указывает на переменную индикатора в этом случае, а ширина индикатора, параметр *кбиндикатор* , используется массовым копированием для правильного адресации данных пользователя.  
  
 *кбиндикатор*  
 Ширина индикатора в байтах или значение NULL для данных столбца. Допускаются следующие значения длины признака: 0 (если признак не используется), 1, 2, 4 или 8. Признаки размещаются в памяти непосредственно перед данными. Например, следующее определение типа структуры можно использовать для вставки целочисленных значений в таблицу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью массового копирования:  
  
```  
typedef struct tagBCPBOUNDINT  
    {  
    int iIndicator;  
    int Value;  
    } BCPBOUNDINT;  
```  
  
 В этом примере параметру *pData* присваивается адрес объявленного экземпляра структуры, адрес члена структуры *iIndicator* iIndicator. Для параметра *кбиндикатор* будет задан размер целого числа (sizeof (int)), а для параметра *cbData* снова будет задан размер целого числа (sizeof (int)). Чтобы выполнить операцию с массовым копированием строки на сервер, содержащий значение NULL для привязанного столбца, значение элемента *iIndicator* экземпляра должно быть установлено в SQL_NULL_DATA.  
  
 *cbData*  
 Количество байт данных в программной переменной, исключая любую длину, NULL-индикатор или признак конца.  
  
 Установка параметра *cbData* в значение SQL_NULL_DATA означает, что все строки, скопированные на сервер, содержат значение NULL для столбца.  
  
 Установка параметра *cbData* в значение SQL_VARLEN_DATA указывает, что система будет использовать признак конца строки или другой метод, чтобы определить длину копируемых данных.  
  
 Для типов данных фиксированной длины, например для целых чисел, система определяет длину данных на основе типа. Таким образом, для типов данных фиксированной длины *cbData* можно безопасно SQL_VARLEN_DATA или длину данных.  
  
 Для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] символьных и двоичных типов данных *cbData* может быть SQL_VARLEN_DATA, SQL_NULL_DATA, положительное значение или 0. Если *cbData* имеет SQL_VARLEN_DATA, система использует либо индикатор длины, либо значение null (если присутствует), либо последовательность признаков конца для определения длины данных. Если представлено и то, и другое, система использует то значение, которое приводит к наименьшему объему копируемых данных. Если *cbData* имеет SQL_VARLEN_DATA, то типом данных столбца является [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] символьный или двоичный тип, и не указан ни индикатор длины, ни последовательность признака конца, система возвращает сообщение об ошибке.  
  
 Если значение *cbData* равно 0 или положительному значению, система использует *cbData* в качестве длины данных. Однако если в дополнение к положительному значению *cbData* предоставляется индикатор длины или последовательность признака конца, система определяет длину данных с помощью метода, который приводит к наименьшему объему копируемых данных.  
  
 Значение параметра *cbData* представляет число байтов данных. Если символьные данные представлены расширенными символами Юникода, то положительное значение параметра *cbData* представляет собой число символов, умноженное на размер в байтах каждого символа.  
  
 *pTerm*  
 Указатель на байтовый шаблон, если таковой имеется, являющийся признаком конца программной переменной. Например, строки ANSI и MBCS C обычно имеют 1-байтовый признаки конца строки (\0).  
  
 Если для переменной нет терминатора, задайте для *птерм* значение null.  
  
 Для обозначения символа конца строки в качестве признака конца программной переменной в языке C можно использовать пустую строку (""). Поскольку пустая строка, заканчивающаяся нулем, образует один байт (сам байт признака конца), установите для *кбтерм* значение 1. Например, чтобы указать, что строка в параметре *szName* завершается нулем, и что для обозначения длины следует использовать признак конца:  
  
```  
bcp_bind(hdbc, szName, 0,  
   SQL_VARLEN_DATA, "", 1,  
   SQLCHARACTER, 2)  
```  
  
 Незавершенная форма этого примера может означать, что 15 символов будут скопированы из переменной *szName* во второй столбец связанной таблицы:  
  
```  
bcp_bind(hdbc, szName, 0, 15,   
   NULL, 0, SQLCHARACTER, 2)  
```  
  
 При необходимости API-интерфейс массового копирования выполнит преобразование символов из Юникода в многобайтовую кодировку (MBCS). Убедитесь, что правильно задана строка байтов признака конца и количество байт в строке. Например, чтобы указать, что строка в параметре *szName* является строкой расширенных символов Юникода, заканчивающейся значением конца Юникода NULL:  
  
```  
bcp_bind(hdbc, szName, 0,   
   SQL_VARLEN_DATA, L"",  
   sizeof(WCHAR), SQLNCHAR, 2)  
```  
  
 Если привязанный [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] столбец является расширенным символом, преобразование в [bcp_sendrow](bcp-sendrow.md)не выполняется. Если столбец [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имеет символьный тип в кодировке MBCS, при передаче данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполняется преобразование расширенных символов в несколько символов.  
  
 *cbTerm*  
 Количество байт в признаке конца программной переменной, если такой имеется. Если для переменной нет терминатора, задайте для *кбтерм* значение 0.  
  
 *eDataType*  
 Тип данных языка C для программной переменной. Данные в программной переменной преобразуются в тип столбца базы данных. Если этот параметр равен 0, преобразование не выполняется.  
  
 Параметр *eDataType* перечисляется маркерами типа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] данных в sqlncli. h, а не в перечислителях типа данных ODBC C. Например, можно задать целое двухбайтовое значение ODBC типа SQL_C_SHORT с помощью типа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQLINT2.  
  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]Добавлена поддержка токенов типа данных SQLXML и SQLUDT в параметре *`eDataType`* .  
  
 *idxServerCol*  
 Порядковый номер столбца в таблице базы данных, в которую копируются данные. Первый столбец в таблице имеет порядковый номер 1. Порядковый номер столбца возвращается функцией [SQLColumns](../native-client-odbc-api/sqlcolumns.md).  
  
## <a name="returns"></a>Возвращает  
 SUCCEED или FAIL.  
  
## <a name="remarks"></a>Remarks  
 Используйте **bcp_bind** для быстрого и эффективного способа копирования данных из программной переменной в таблицу в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Вызовите [bcp_init](bcp-init.md) перед вызовом этой или любой другой функции небольшого копирования. Вызов **bcp_init** задает целевую таблицу для выполнения [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] операции с массовым копированием. При вызове **bcp_init** для использования с **bcp_bind** и [bcp_sendrow](bcp-sendrow.md)параметр **bcp_init** _сздатафиле_ , указывающий файл данных, устанавливается в значение null. параметр **bcp_init**_eDirection_ имеет значение DB_IN.  
  
 Создайте отдельный **bcp_bind** вызов для каждого столбца в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] таблице, в которую необходимо выполнить копирование. После выполнения необходимых **bcp_bind** вызовов вызовите **bcp_sendrow** , чтобы отправить строку данных из переменных программы в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Повторная привязка столбца не поддерживается.  
  
 Когда нужно [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] зафиксировать уже полученные строки, вызовите [bcp_batch](bcp-batch.md). Например, вызовите **bcp_batch** один раз для каждых 1000 строк или в любой другой интервал.  
  
 Если строки для вставки не найдены, вызовите [bcp_done](bcp-done.md). Несоблюдение этого правила приведет к ошибке.  
  
 Параметры управления, указанные в параметре [bcp_control](bcp-control.md), не влияют на передачу **bcp_bind** строк.  
  
 Если *pData* для столбца имеет значение null, так как оно будет предоставлено вызовами [bcp_moretext](bcp-moretext.md), все последующие столбцы с *eDataType* , для которых заданы значения SQLTEXT, SQLNTEXT, SQLXML, SQLUDT, SQLCHARACTER, SQLVARCHAR, SQLVARBINARY, SqlBinary, SQLNCHAR или SQLIMAGE, также должны быть связаны с параметром *pData* , имеющим значение null, и их значения также должны `bcp_moretext`быть предоставлены вызовами.  
  
 Для новых типов больших значений, таких как `varchar(max)`, `varbinary(max)`или `nvarchar(max)`, можно использовать SQLCHARACTER, SQLVARCHAR, SQLVARBINARY, SqlBinary и SQLNCHAR в качестве индикаторов типов в параметре *eDataType* .  
  
 Если *кбтерм* не равен 0, то любое значение (1, 2, 4 или 8) допустимо для префикса (*кбиндикатор*). В этой ситуации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственный клиент выполняет поиск терминатора, вычисляет длину данных относительно терминатора (*i*) и устанавливает для *cbData* меньшее значение i и значение prefix.  
  
 Если *кбтерм* имеет значение 0 и *кбиндикатор* (префикс) не равно 0, *кбиндикатор* должен быть равен 8. Восьмибайтовый префикс может принимать следующие значения.  
  
-   0xFFFFFFFFFFFFFFFF означает значение NULL для поля.  
  
-   0xFFFFFFFFFFFFFFFE рассматривается как специальное значение префикса, которое используется для эффективной отправки на сервер данных, разбитых на фрагменты. Данные со специальным префиксом имеют следующий формат.  
  
-   <SPECIAL_PREFIX> \<0 или более фрагментов данных> <ZERO_CHUNK>, где:  
  
-   СПЕЦИАЛЬНЫЙ_ПРЕФИКС имеет значение 0xFFFFFFFFFFFFFFFE.  
  
-   ФРАГМЕНТ_ДАННЫХ является 4-байтовым префиксом, содержащим длину фрагмента, за которым следуют фактические данные, длина которых задана 4-байтовым префиксом.  
  
-   НУЛЕВОЙ_ФРАГМЕНТ является 4-байтовым значением, содержащим все нули (00000000), которое указывает конец данных.  
  
-   Любая другая 8-байтовая длина рассматривается как длина обычных данных.  
  
 Вызов [bcp_columns](bcp-columns.md) при использовании **bcp_bind** приводит к ошибке.  
  
## <a name="bcp_bind-support-for-enhanced-date-and-time-features"></a>Поддержка функцией bcp_bind улучшенных возможностей даты и времени  
 Дополнительные сведения о типах, используемых с параметром *eDataType* для типов даты и времени, см. в разделе " [изменения в ходе операции копирования для расширенных типов даты и времени &#40;OLE DB и ODBC&#41;](../native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md).  
  
 Дополнительные сведения см. в разделе [улучшения даты и времени &#40;&#41;ODBC ](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
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
  
## <a name="see-also"></a>См. также:  
 [Bulk Copy Functions](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
