---
title: bcp_moretext | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- bcp_moretext
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_moretext function
ms.assetid: 23e98015-a8e4-4434-9b3f-9c7350cf965f
caps.latest.revision: 39
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 30ddae53cc452796de0617bb5718d04156dcda41
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37430183"
---
# <a name="bcpmoretext"></a>bcp_moretext
  Отправляет в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] часть значения длинного типа данных переменной длины.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
RETCODE bcp_moretext (  
HDBC   
hdbc  
,  
DBINT   
cbData  
,  
LPCBYTE   
pData  
);  
  
```  
  
## <a name="arguments"></a>Аргументы  
 *HDBC*  
 Дескриптор соединения ODBC с поддержкой массового копирования.  
  
 *cbData*  
 Число байтов данных, копируемых в SQL Server на основе данных, который ссылается *pData*. Значение SQL_NULL_DATA соответствует значению NULL.  
  
 *pData*  
 Представляет собой указатель на ту часть значения поддерживаемого длинного типа данных переменной длины, которую нужно переслать в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="returns"></a>Возвращает  
 SUCCEED или FAIL.  
  
## <a name="remarks"></a>Примечания  
 Эта функция может использоваться в сочетании с [bcp_bind](bcp-bind.md) и [bcp_sendrow](bcp-sendrow.md) долго, копирование значений данных переменной длины в SQL Server в виде фрагментов меньшего размера. **bcp_moretext** может использоваться со столбцами, имеющими следующие типы данных SQL Server: `text`, `ntext`, `image`, `varchar(max)`, `nvarchar(max)`, `varbinary(max)`, определяемого пользователем типа (UDT) и XML. **bcp_moretext** не поддерживает преобразование данных, передаваемых данных должен соответствовать тип данных целевого столбца.  
  
 Если **bcp_bind** вызывается с отличным от NULL *pData* параметров для типов данных, поддерживаемых **bcp_moretext**, `bcp_sendrow` отправляет значения типа данных, независимо от того, длины. Если, однако **bcp_bind** имеет значение NULL *pData* параметр для поддерживаемых типов данных, **bcp_moretext** можно использовать для копирования данных сразу после успешного возвращения из `bcp_sendrow` , указывающее, что все привязанные столбцы с данными, которые присутствуют были обработаны.  
  
 Если вы используете **bcp_moretext** для отправки один столбец типа данных, поддерживаемых в строке, необходимо также использовать его для отправки всех остальных столбцов типа данных, поддерживаемых в строке. Ни один столбец не может быть пропущен. Поддерживаемыми типами данных являются SQLTEXT, SQLNTEXT, SQLIMAGE, SQLUDT и SQLXML. То же относится к типам данных SQLCHARACTER, SQLVARCHAR, SQNCHAR, SQLBINARY и SQLVARBINARY, если столбец имеет тип varchar(max), nvarchar(max) или varbinary(max) соответственно.  
  
 Вызов любого **bcp_bind** или [bcp_collen](bcp-collen.md) задает общую длину всех фрагментов данных для копирования столбца SQL Server. При попытке отправки SQL Server большее число байтов, чем указано в вызове **bcp_bind** или `bcp_collen` приводит к ошибке. Эта ошибка возникает, если, например, в приложении после использования `bcp_collen` для задания длины допустимых данных для SQL Server `text` столбца равной 4500, а затем вызывал **bcp_moretext** пять раз во время, указывающее, при каждом вызове Длина буфера данных было 1000 байт.  
  
 Если копируемая строка содержит более одного столбца long и variable-length, **bcp_moretext** сначала передает данные к меньшему порядковым номером столбца, следуют следующей наименьшей столбец с порядковым номером и т. д. Необходимо правильно задать длину ожидаемых данных. Какой-либо иной способ определения того, что в операции массового копирования получены все данные столбца, кроме проверки по заданной длине, отсутствует.  
  
 Когда `var(max)` значения отправляются на сервер, с помощью команды bcp_sendrow и bcp_moretext, нет необходимости вызывать bcp_collen для задания длины столбца. Вместо этого только для указанных типов, значение завершается путем вызова bcp_sendrow с нулевой длины.  
  
 Приложение обычно вызывает `bcp_sendrow` и **bcp_moretext** в циклах для пересылки нескольких строк данных. Ниже приводится объяснение того, как это сделать для таблицы, содержащий два `text` столбцы:  
  
```  
while (there are still rows to send)  
{  
bcp_sendrow(...);  
  
for (all the data in the first varbinary(max) column)  
bcp_moretext(...);  
bcp_moretext(hdbc, 0, NULL);  
  
for (all the data in the second varbinary(max) column)  
bcp_moretext(...);  
bcp_moretext(hdbc, 0, NULL);  
  
}  
  
```  
  
## <a name="example"></a>Пример  
 В этом примере показано, как использовать **bcp_moretext** с **bcp_bind** и `bcp_sendrow`:  
  
```  
// Variables like henv not specified.  
HDBC      hdbc;  
DBINT      idRow = 5;  
char*      pPart1 = "This text value isn't very long,";  
char*      pPart2 = " but it's broken into three parts";  
char*      pPart3 = " anyhow.";  
DBINT      cbAllParts;  
DBINT      nRowsProcessed;  
  
// Application initiation, get an ODBC environment handle, allocate the  
// hdbc, and so on.  
...   
  
// Enable bulk copy prior to connecting on allocated hdbc.  
SQLSetConnectAttr(hdbc, SQL_COPT_SS_BCP, (SQLPOINTER) SQL_BCP_ON,  
   SQL_IS_INTEGER);  
  
// Connect to the data source, return on error.  
if (!SQL_SUCCEEDED(SQLConnect(hdbc, _T("myDSN"), SQL_NTS,  
   _T("myUser"), SQL_NTS, _T("myPwd"), SQL_NTS)))  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Initialize bulk copy.   
if (bcp_init(hdbc, "comdb..articles", NULL, NULL, DB_IN) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Bind program variables to table columns.   
if (bcp_bind(hdbc, (LPCBYTE) &idRow, 0, SQL_VARLEN_DATA, NULL, 0,  
   SQLINT4, 1)    == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
cbAllParts = (DBINT) (strnlen(pPart1, sizeof(pPart1) + 1) + strnlen(pPart2, sizeof(pPart2) + 1) + strnlen(pPart3, sizeof(pPart3) + 1));  
if (bcp_bind(hdbc, NULL, 0, cbAllParts, NULL, 0, SQLTEXT, 2) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Send this row, with the text value broken into three chunks.   
if (bcp_sendrow(hdbc) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
if (bcp_moretext(hdbc, (DBINT) strnlen(pPart1, sizeof(pPart1) + 1), pPart1) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
if (bcp_moretext(hdbc, (DBINT) strnlen(pPart2, sizeof(pPart2) + 1), pPart2) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
if (bcp_moretext(hdbc, (DBINT) strnlen(pPart3, sizeof(pPart3) + 1), pPart3) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// All done. Get the number of rows processed (should be one).  
nRowsProcessed = bcp_done(hdbc);  
  
// Carry on.  
```  
  
## <a name="see-also"></a>См. также  
 [Функции массового копирования](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
