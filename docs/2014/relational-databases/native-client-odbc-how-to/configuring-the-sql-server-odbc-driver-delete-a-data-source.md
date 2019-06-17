---
title: Удаление источника данных (ODBC) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- data sources [ODBC]
ms.assetid: 910e3e16-7b91-49d8-80bb-b4243926afaa
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ff882caf0ce5d9ef7d2e9f059daed89ed4b50d82
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63126107"
---
# <a name="delete-a-data-source-odbc"></a>Удаление источника данных (ODBC)
  Источник данных можно удалить с помощью администратора ODBC программным способом (с помощью [SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md)), или путем удаления файла (если имя файла источника данных).  
  
### <a name="to-delete-a-data-source-by-using-odbc-administrator"></a>Удаление источника данных с помощью администратора ODBC  
  
1.  В **панели управления**откройте **Администрирование**, а затем дважды щелкните **источники данных (ODBC)** . Либо можно запустить файл odbcad32.exe из командной строки.  
  
2.  Нажмите кнопку **DSN пользователя**, **системный DSN**, или **файловый DSN** вкладки.  
  
3.  Щелкните источник данных, который нужно удалить.  
  
4.  Нажмите кнопку **удалить**, а затем подтвердите удаление.  
  
## <a name="example"></a>Пример  
 Чтобы программно удалить источник данных, вызовите [SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md) с помощью значение ODBC_REMOVE_DSN или ODBC_REMOVE_SYS_DSN в качестве второго параметра.  
  
 В следующем образце показана процедура удаления источника данных программным способом.  
  
```  
// remove_odbc_data_source.cpp  
// compile with: ODBCCP32.lib user32.lib  
#include <iostream>  
#include <windows.h>  
#include <odbcinst.h>  
  
int main() {   
   LPCSTR provider = "SQL Server";   // Windows SQL Server Driver  
   LPCSTR provider = "SQL Server";   // Windows SQL Server driver  
   LPCSTR provider2 = "SQL Server Native Client 11.0";   // SQL Server 2012 Native Client driver  
   LPCSTR dsnname = "DSN=data2";  
   BOOL retval = SQLConfigDataSource(NULL, ODBC_REMOVE_DSN, provider, dsnname);  
   std::cout << retval;   // 1 if successful  
}  
```  
  
## <a name="see-also"></a>См. также  
 [Инструкции по настройке драйвера ODBC SQL Server](../../database-engine/dev-guide/configuring-the-sql-server-odbc-driver-how-to-topics.md)  
  
  
