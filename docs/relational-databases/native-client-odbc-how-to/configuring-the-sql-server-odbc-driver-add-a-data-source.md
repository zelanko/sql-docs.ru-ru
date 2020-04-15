---
title: Добавить источник данных (ODBC) Документы Майкрософт
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
ms.openlocfilehash: 55ae4f357aa850f6b3ff4ba9cca0b59a2ccbc570
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298337"
---
# <a name="configuring-the-sql-server-odbc-driver---add-a-data-source"></a>Настройка драйвера ODBC SQL Server — добавление источника данных
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Перед использованием приложений ODBC с [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] или более поздней версией необходимо знать, как обновлять версию хранимых процедур каталога на предыдущих версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и как добавлять, удалять и проверять источники данных.  
  
  Вы можете добавить источник данных с помощью администратора ODBC, программно (с помощью [S'LConfigDataSource),](../../relational-databases/native-client-odbc-api/sqlconfigdatasource.md)или путем создания файла.  
  
### <a name="to-add-a-data-source-by-using-odbc-administrator"></a>Добавление источника данных при помощи администратора ODBC  
  
1.  С **панели управления**, доступ **к административным инструментам,** а затем либо **ODBC источников данных (64-битных)** или **ODBC источников данных (32-битный)**. Можно также вызвать программу odbcad32.exe.  
  
2.  Нажмите на вкладку **Пользователя DSN,** **System DSN**или **File DSN,** а затем нажмите **Добавить.**  
  
3.  Нажмите **на сервер S'L,** а затем нажмите **«Завершение».**  
  
4.  Завершите этапы создания нового источника данных для мастера **серверов S'L.**  
  
### <a name="to-add-a-data-source-programmatically"></a>Добавление источника данных программно  
  
1.  Позвоните [в S'LConfigDataSource](../../relational-databases/native-client-odbc-api/sqlconfigdatasource.md) со вторым параметром, установленным для ODBC_ADD_DSN или ODBC_ADD_SYS_DSN.  
  
### <a name="to-add-a-file-data-source"></a>Добавление файла источника данных  
  
1.  Позвоните [в S'LDriverConnect](../../relational-databases/native-client-odbc-api/sqldriverconnect.md) с помощью параметра SAVEFILE-file_name в строке подключения. Если соединение успешно, драйвер ODBC создаст файл источника данных с параметрами соединения, место расположения которого указано параметром SAVEFILE.  
  
## <a name="see-also"></a>См. также:  
[Удалить источник данных &#40;&#41;ODBC](../../relational-databases/native-client-odbc-how-to/configuring-the-sql-server-odbc-driver-delete-a-data-source.md)    
  
  
