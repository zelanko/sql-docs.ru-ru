---
title: bcp_moretext | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
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
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: cfa6968d4bb4254b52efd3e09d7f04e3c7fa9268
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82701920"
---
# <a name="bcp_moretext"></a>bcp_moretext
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
 *hdbc*  
 Дескриптор соединения ODBC с поддержкой массового копирования.  
  
 *cbData*  
 Число байтов данных, копируемых в SQL Server из данных, на которые ссылается *pData*. Значение SQL_NULL_DATA соответствует значению NULL.  
  
 *pData*  
 Представляет собой указатель на ту часть значения поддерживаемого длинного типа данных переменной длины, которую нужно переслать в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="returns"></a>Возвращаемое значение  
 SUCCEED или FAIL.  
  
## <a name="remarks"></a>Remarks  
 Эта функция может использоваться в сочетании с [bcp_bind](bcp-bind.md) и [bcp_sendrow](bcp-sendrow.md) для копирования длинных значений данных переменной длины, которые SQL Serverся в нескольких меньших фрагментах. **bcp_moretext** можно использовать со столбцами, имеющими следующие SQL Server типов данных: `text` , `ntext` , `image` ,,, `varchar(max)` `nvarchar(max)` `varbinary(max)` , определяемый пользователем тип (UDT) и XML. **bcp_moretext** не поддерживает преобразования данных, указанные данные должны соответствовать типу данных целевого столбца.  
  
 Если **bcp_bind** вызывается с параметром *pData* , не равным null, для типов данных, поддерживаемых **bcp_moretext**, `bcp_sendrow` отправляет все значения данных, независимо от длины. Однако, если **bcp_bind** имеет параметр *pData* NULL для поддерживаемых типов данных, **bcp_moretext** можно использовать для копирования данных сразу после успешного возврата с того, `bcp_sendrow` что все связанные столбцы с данными уже обработаны.  
  
 Если для отправки одного столбца поддерживаемого типа данных в строке используется **bcp_moretext** , необходимо также использовать его для отправки всех остальных поддерживаемых столбцов типа данных в строке. Ни один столбец не может быть пропущен. Поддерживаемыми типами данных являются SQLTEXT, SQLNTEXT, SQLIMAGE, SQLUDT и SQLXML. То же относится к типам данных SQLCHARACTER, SQLVARCHAR, SQNCHAR, SQLBINARY и SQLVARBINARY, если столбец имеет тип varchar(max), nvarchar(max) или varbinary(max) соответственно.  
  
 Вызов либо **bcp_bind** , либо [bcp_collen](bcp-collen.md) задает общую длину всех частей данных, копируемых в столбец SQL Server. Попытка отправить SQL Server больше байтов, чем указано в вызове функции **bcp_bind** или `bcp_collen` выдает ошибку. Эта ошибка может возникнуть, например, в приложении, которое использовалось `bcp_collen` для установки длины доступных данных для SQL Server `text` столбца в 4500, затем вызывается **bcp_moretext** пять раз, указывая на каждый вызов, длина буфера данных которой составила 1000 байт.  
  
 Если скопированная строка содержит более одного столбца переменной длины, **bcp_moretext** сначала отправляет свои данные в столбец с наименьшим порядковым номером, за которым следует столбец с наименьшим порядковым номером и так далее. Необходимо правильно задать длину ожидаемых данных. Какой-либо иной способ определения того, что в операции массового копирования получены все данные столбца, кроме проверки по заданной длине, отсутствует.  
  
 Если `var(max)` значения отправляются на сервер с помощью bcp_sendrow и bcp_moretext, нет необходимости вызывать bcp_collen для задания длины столбца. Вместо этого для этих типов значение завершается вызовом bcp_sendrow с нулевой длиной.  
  
 Приложение обычно вызывает `bcp_sendrow` и **bcp_moretext** в циклах для отправки нескольких строк данных. Ниже приведена схема того, как это сделать для таблицы, содержащей два `text` столбца:  
  
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
 В этом примере показано, как использовать **bcp_moretext** с **bcp_bind** и `bcp_sendrow` :  
  
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
 [Bulk Copy Functions](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
