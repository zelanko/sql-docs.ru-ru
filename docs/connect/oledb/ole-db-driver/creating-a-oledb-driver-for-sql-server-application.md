---
title: Создание приложения драйвера OLE DB для SQL Server | Документы Майкрософт
description: Сведения о действиях, необходимых для создания приложения OLE DB Driver for SQL Server и поиска дополнительных ресурсов.
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, application creation
- applications [OLE DB Driver for SQL Server]
- OLE DB, creating applications
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ed150ea18d1141e6116efe177e65836c235cf703
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/05/2020
ms.locfileid: "91727233"
---
# <a name="creating-an-ole-db-driver-for-sql-server-application"></a>Создание приложения драйвера OLE DB для SQL Server
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Чтобы создать приложение OLE DB Driver for SQL Server, необходимо выполнить такие шаги:  
  
1.  установление соединения с источником данных;  
  
2.  выполнение команды;  
  
3.  обработку результатов.  
  
> [!NOTE]  
>  По возможности используйте аутентификацию Windows. Если проверка подлинности Windows недоступна, запросите у пользователя ввод учетных данных во время выполнения. Избегайте хранения учетных данных в файле. Если необходимо сохранение учетных данных, зашифруйте их с помощью [API-интерфейса шифрования Win32](/windows/win32/seccng/cng-portal).  
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Установка подключения к источнику данных](../../oledb/ole-db-driver/establishing-a-connection-to-a-data-source.md)  
  
-   [Выполнение команды](../../oledb/ole-db-driver/executing-a-command.md)  
  
-   [Обработка результатов](../../oledb/ole-db-driver/processing-results.md)  
  
-   [О свойствах OLE DB](../../oledb/ole-db-driver/about-ole-db-properties.md)  
  
-   [Использование предложения OUTPUT с OLE DB в драйвере OLE DB для SQL Server](../../oledb/ole-db-driver/using-the-output-clause-with-ole-db-in-oledb-driver-for-sql-server.md)  
  
## <a name="see-also"></a>См. также:  
 [Программирование драйвера OLE DB для SQL Server](../../oledb/ole-db/oledb-driver-for-sql-server-programming.md)  
  
