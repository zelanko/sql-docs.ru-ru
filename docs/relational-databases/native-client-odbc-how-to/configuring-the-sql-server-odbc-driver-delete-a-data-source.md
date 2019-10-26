---
title: Удаление источника данных (ODBC) | Документация Майкрософт
ms.custom: ''
ms.date: 08/01/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- data sources [ODBC]
ms.assetid: 910e3e16-7b91-49d8-80bb-b4243926afaa
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 714823ca585e85d8c1c3840da37630d975b9fdb6
ms.sourcegitcommit: 2a06c87aa195bc6743ebdc14b91eb71ab6b91298
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/25/2019
ms.locfileid: "72908218"
---
# <a name="configuring-the-sql-server-odbc-driver---delete-a-data-source"></a>Настройка драйвера ODBC SQL Server — удаление источника данных
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Перед использованием приложений ODBC с [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] или более поздней версией необходимо знать, как обновлять версию хранимых процедур каталога на предыдущих версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и как добавлять, удалять и проверять источники данных.  
  
  Источник данных можно удалить с помощью администратора ODBC, программно (с помощью [SQLConfigDataSource](../../relational-databases/native-client-odbc-api/sqlconfigdatasource.md)) или путем удаления файла (если имя источника данных файла).  
  
### <a name="to-delete-a-data-source-by-using-odbc-administrator"></a>Удаление источника данных с помощью администратора ODBC  
  
1.  На **панели управления**откройте **меню Администрирование**, а затем дважды щелкните **Источники данных ODBC (64-разрядная версия)** или **Источники данных ODBC (32-бит)** . Либо можно запустить файл odbcad32.exe из командной строки.  
  
2.  Щелкните вкладку **DSN пользователя**, **системное имя DSN**или **Файловый DSN** .  
  
3.  Выберите источник данных для удаления.  
  
4.  Нажмите кнопку **Удалить**, а затем подтвердите удаление.  

## <a name="example"></a>Пример  
 Чтобы программно удалить источник данных, вызовите [SQLConfigDataSource](../../relational-databases/native-client-odbc-api/sqlconfigdatasource.md) , используя ODBC_REMOVE_DSN или ODBC_REMOVE_SYS_DSN в качестве второго параметра.  
  
 В следующем образце показана процедура удаления источника данных программным способом.  
  
```  
// remove_odbc_data_source.cpp  
// compile with: ODBCCP32.lib user32.lib  
#include <iostream>  
#include \<windows.h>  
#include \<odbcinst.h>  
  
int main() {   
   LPCSTR provider = "SQL Server";   // Windows SQL Server Driver  
   LPCSTR provider = "SQL Server";   // Windows SQL Server driver  
   LPCSTR provider2 = "SQL Server Native Client 11.0";   // SQL Server 2012 Native Client driver  
   LPCSTR dsnname = "DSN=data2";  
   BOOL retval = SQLConfigDataSource(NULL, ODBC_REMOVE_DSN, provider, dsnname);  
   std::cout << retval;   // 1 if successful  
}  
```  
  
## <a name="see-also"></a>См. также статью  
 [Добавление источника &#40;данных ODBC&#41;](../../relational-databases/native-client-odbc-how-to/configuring-the-sql-server-odbc-driver-add-a-data-source.md)  
  
  
