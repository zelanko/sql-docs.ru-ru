---
title: bcp_readfmt | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_readfmt
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_readfmt function
ms.assetid: 654001c8-ae9f-425c-b820-f0191bf89367
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 76ccc4271877b81ae103a89b5df727b74017d9ab
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62688669"
---
# <a name="bcp_readfmt"></a>bcp_readfmt
  Считывает определение формата файла данных из указанного файла форматирования.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
RETCODE bcp_readfmt (  
HDBC   
hdbc  
,  
LPCTSTR   
szFormatFile  
);  
  
```  
  
## <a name="arguments"></a>Аргументы  
 *hdbc*  
 Дескриптор соединения ODBC с поддержкой массового копирования.  
  
 *szFormatFile*  
 Путь и имя файла, содержащего значения формата для файла данных.  
  
## <a name="returns"></a>Возвращает  
 SUCCEED или FAIL.  
  
## <a name="remarks"></a>Remarks  
 После `bcp_readfmt` считывания значений формата они выполняют соответствующие вызовы [bcp_columns](bcp-columns.md) и [bcp_colfmt](bcp-colfmt.md). Пользователю не требуется анализировать файл форматирования и выполнять эти вызовы.  
  
 Чтобы сохранить файл форматирования, вызовите функцию [bcp_writefmt](bcp-writefmt.md). Вызовы метода `bcp_readfmt` могут ссылаться на сохраненные форматы. Дополнительные сведения см. в разделе [bcp_init](bcp-init.md).  
  
 Кроме того, программа полного копирования (**bcp**) может сохранять пользовательские форматы данных в файлах, на которые может ссылаться `bcp_readfmt`. Дополнительные сведения о программе **bcp** и структуре файлов формата данных **bcp** см. в статье инструкции по [импорту и экспорту данных &#40;SQL Server&#41;](../import-export/bulk-import-and-export-of-data-sql-server.md).  
  
 `BCPDELAYREADFMT` Значение параметра *eOption* [bcp_control](bcp-control.md) изменяет поведение bcp_readfmt.  
  
> [!NOTE]  
>  Файл форматирования должен быть создан с помощью программы **bcp** версии 4.2 или более поздней.  
  
## <a name="example"></a>Пример  
  
```  
// Variables like henv not specified.  
HDBC      hdbc;  
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
if (bcp_init(hdbc, _T("myTable"), _T("myData.csv"),  
   _T("myErrors"),    DB_IN) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
if (bcp_readfmt(hdbc, _T("myFmtFile.fmt")) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
if (bcp_exec(hdbc, &nRowsProcessed) == SUCCEED)  
   {  
   cout << nRowsProcessed << " rows copied to SQL Server\n";  
   }  
  
// Carry on.  
```  
  
## <a name="see-also"></a>См. также:  
 [Bulk Copy Functions](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
