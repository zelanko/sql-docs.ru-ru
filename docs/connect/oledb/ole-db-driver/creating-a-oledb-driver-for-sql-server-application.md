---
title: Создание драйвером OLE DB для приложения SQL Server | Документы Microsoft
description: Создание драйвер OLE DB для SQL Server приложения
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: oledb-driver-for-sql-server
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, application creation
- applications [OLE DB Driver for SQL Server]
- OLE DB, creating applications
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a0deaf6cba6f6a7b51b8467fa868e9aa2c8094e3
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="creating-an-ole-db-driver-for-sql-server-application"></a>Создание драйвером OLE DB для приложения SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Создание драйвер OLE DB для приложения SQL Server включает в себя следующие действия:  
  
1.  установление соединения с источником данных;  
  
2.  выполнение команды;  
  
3.  обработку результатов.  
  
> [!NOTE]  
>  По возможности используйте аутентификацию Windows. Если проверка подлинности Windows недоступна, запросите у пользователя ввод учетных данных во время выполнения. Избегайте хранения учетных данных в файле. Если необходимо сохранить учетные данные, зашифруйте их с [Win32 cryptoAPI](http://go.microsoft.com/fwlink/?LinkId=9504).  
  
## <a name="in-this-section"></a>В этом разделе  
  
-   [Установление подключения к источнику данных](../../oledb/ole-db-driver/establishing-a-connection-to-a-data-source.md)  
  
-   [Выполнение команды](../../oledb/ole-db-driver/executing-a-command.md)  
  
-   [Обработка результатов](../../oledb/ole-db-driver/processing-results.md)  
  
-   [О свойствах OLE DB](../../oledb/ole-db-driver/about-ole-db-properties.md)  
  
-   [Использование предложения OUTPUT с OLE DB в драйвере OLE DB для SQL Server](../../oledb/ole-db-driver/using-the-output-clause-with-ole-db-in-oledb-driver-for-sql-server.md)  
  
## <a name="see-also"></a>См. также  
 [Программирование драйвера OLE DB для SQL Server](../../oledb/ole-db/oledb-driver-for-sql-server-programming.md)  
  
  
