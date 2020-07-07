---
title: Добавление источника данных (ODBC) | Документация Майкрософт
description: Узнайте, как SQL Server драйвер ODBC вызывает хранимые процедуры в качестве удаленных хранимых процедур в SQL Server с помощью механизма вызова удаленной хранимой процедуры.
ms.custom: ''
ms.date: 08/01/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- data sources [ODBC]
ms.assetid: b4ac6f0e-8e6a-4b1a-9a7e-60e0a69b2180
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 499ca3cbd3c751e3f5a29260f46a5a4cfe8a6dce
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.contentlocale: ru-RU
ms.lasthandoff: 07/06/2020
ms.locfileid: "86009532"
---
# <a name="configuring-the-sql-server-odbc-driver---add-a-data-source"></a>Настройка драйвера ODBC SQL Server — добавление источника данных
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Перед использованием приложений ODBC с [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] или более поздней версией необходимо знать, как обновлять версию хранимых процедур каталога на предыдущих версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и как добавлять, удалять и проверять источники данных.  
  
  Источник данных можно добавить с помощью администратора ODBC, программно (с помощью [SQLConfigDataSource](../../relational-databases/native-client-odbc-api/sqlconfigdatasource.md)) или путем создания файла.  
  
### <a name="to-add-a-data-source-by-using-odbc-administrator"></a>Добавление источника данных при помощи администратора ODBC  
  
1.  В **панели управления**откройте **меню Администрирование** и выберите либо источники **данных ODBC (64-разрядные)** , либо **Источники данных ODBC (32-бит)**. Можно также вызвать программу odbcad32.exe.  
  
2.  Щелкните вкладку **DSN пользователя**, **системное имя DSN**или **Файловый DSN** , а затем нажмите кнопку **Добавить**.  
  
3.  Щелкните **SQL Server**и нажмите кнопку **Готово**.  
  
4.  Выполните действия, описанные в мастере **создания нового источника данных для SQL Server** .  
  
### <a name="to-add-a-data-source-programmatically"></a>Добавление источника данных программно  
  
1.  Вызовите [SQLConfigDataSource](../../relational-databases/native-client-odbc-api/sqlconfigdatasource.md) со вторым параметром, имеющим значение ODBC_ADD_DSN или ODBC_ADD_SYS_DSN.  
  
### <a name="to-add-a-file-data-source"></a>Добавление файла источника данных  
  
1.  Вызовите [SQLDriverConnect](../../relational-databases/native-client-odbc-api/sqldriverconnect.md) с параметром SAVEFILE = file_name в строке подключения. Если соединение успешно, драйвер ODBC создаст файл источника данных с параметрами соединения, место расположения которого указано параметром SAVEFILE.  
  
## <a name="see-also"></a>См. также  
[Удаление источника данных &#40;ODBC&#41;](../../relational-databases/native-client-odbc-how-to/configuring-the-sql-server-odbc-driver-delete-a-data-source.md)    
  
  
