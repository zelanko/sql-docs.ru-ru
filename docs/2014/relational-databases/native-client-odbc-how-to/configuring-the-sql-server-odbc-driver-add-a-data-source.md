---
title: Добавление источника данных (ODBC) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- data sources [ODBC]
ms.assetid: b4ac6f0e-8e6a-4b1a-9a7e-60e0a69b2180
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c050efd2f309ccec76b80fd24b519e7d2389e4ea
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63126078"
---
# <a name="add-a-data-source-odbc"></a>Добавление источника данных (ODBC)
  Можно добавить источник данных с помощью администратора ODBC программным способом (с помощью [SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md)), или путем создания файла.  
  
### <a name="to-add-a-data-source-by-using-odbc-administrator"></a>Добавление источника данных при помощи администратора ODBC  
  
1.  Из **панели управления**, доступ **Администрирование** и затем **источники данных (ODBC)** . Можно также вызвать программу odbcad32.exe.  
  
2.  Нажмите кнопку **DSN пользователя**, **системный DSN**, или **файловый DSN** , а затем щелкните **добавить**.  
  
3.  Нажмите кнопку **SQL Server**, а затем нажмите кнопку **Готово**.  
  
4.  Выполните шаги по созданию нового источника данных в мастере SQL Server.  
  
### <a name="to-add-a-data-source-programmatically"></a>Добавление источника данных программно  
  
1.  Вызовите [SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md) с второго параметра, равно либо ODBC_ADD_DSN, либо ODBC_ADD_SYS_DSN.  
  
### <a name="to-add-a-file-data-source"></a>Добавление файла источника данных  
  
1.  Вызовите [SQLDriverConnect](../native-client-odbc-api/sqldriverconnect.md) SAVEFILE = file_name параметр в строке соединения. Если соединение успешно, драйвер ODBC создаст файл источника данных с параметрами соединения, место расположения которого указано параметром SAVEFILE.  
  
## <a name="see-also"></a>См. также  
 [Инструкции по настройке драйвера ODBC SQL Server](../../database-engine/dev-guide/configuring-the-sql-server-odbc-driver-how-to-topics.md)  
  
  
