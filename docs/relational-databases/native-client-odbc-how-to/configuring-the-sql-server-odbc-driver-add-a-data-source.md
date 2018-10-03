---
title: Добавление источника данных (ODBC) | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 21ba3a1507588e0110bbcf281f2cbbe9f41742a3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47787942"
---
# <a name="configuring-the-sql-server-odbc-driver---add-a-data-source"></a>Настройка драйвера ODBC SQL Server — добавление источника данных
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Перед использованием приложений ODBC с [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] или более поздней версией необходимо знать, как обновлять версию хранимых процедур каталога на предыдущих версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и как добавлять, удалять и проверять источники данных.  
  
  Можно добавить источник данных с помощью администратора ODBC программным способом (с помощью [SQLConfigDataSource](../../relational-databases/native-client-odbc-api/sqlconfigdatasource.md)), или путем создания файла.  
  
### <a name="to-add-a-data-source-by-using-odbc-administrator"></a>Добавление источника данных при помощи администратора ODBC  
  
1.  Из **панели управления**, доступ **Администрирование** и затем либо **источников данных ODBC (64-разрядная версия)** или **источников данных ODBC (32-разрядная версия)**. Можно также вызвать программу odbcad32.exe.  
  
2.  Нажмите кнопку **DSN пользователя**, **системный DSN**, или **файловый DSN** , а затем щелкните **добавить**.  
  
3.  Нажмите кнопку **SQL Server**, а затем нажмите кнопку **Готово**.  
  
4.  Выполните действия, описанные в **создать новый источник данных для SQL Server** мастера.  
  
### <a name="to-add-a-data-source-programmatically"></a>Добавление источника данных программно  
  
1.  Вызовите [SQLConfigDataSource](../../relational-databases/native-client-odbc-api/sqlconfigdatasource.md) с второго параметра, равно либо ODBC_ADD_DSN, либо ODBC_ADD_SYS_DSN.  
  
### <a name="to-add-a-file-data-source"></a>Добавление файла источника данных  
  
1.  Вызовите [SQLDriverConnect](../../relational-databases/native-client-odbc-api/sqldriverconnect.md) SAVEFILE = file_name параметр в строке соединения. Если соединение успешно, драйвер ODBC создаст файл источника данных с параметрами соединения, место расположения которого указано параметром SAVEFILE.  
  
## <a name="see-also"></a>См. также  
[Удаление источника данных &#40;ODBC&#41;](../../relational-databases/native-client-odbc-how-to/configuring-the-sql-server-odbc-driver-delete-a-data-source.md)    
  
  
