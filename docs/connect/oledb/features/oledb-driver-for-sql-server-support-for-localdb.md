---
title: Поддержка драйвера OLE DB для SQL Server в LocalDB | Документы Майкрософт
description: Поддержка драйвера OLE DB для SQL Server в LocalDB
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
author: pmasl
ms.author: pelopes
manager: jroth
ms.openlocfilehash: 099ffb2203397bd02b91af68651ccb42a23e2b5b
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66802962"
---
# <a name="ole-db-driver-for-sql-server-support-for-localdb"></a>Поддержка драйвера OLE DB для SQL Server в LocalDB
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Начиная с версии [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], будет доступна облегченная версия SQL Server, называемая LocalDB. В этом разделе обсуждается, как можно установить соединение с базой данных на экземпляре LocalDB.  
  
## <a name="remarks"></a>Remarks  
 Дополнительные сведения о LocalDB, включая способы его установки и настройки, см. в разделе:  
  
-   [Справочник по SQL Server Express LocalDB](../../../relational-databases/sql-server-express-localdb-reference.md)  
  
-   [SQL Server 2016 Express LocalDB](../../../database-engine/configure-windows/sql-server-2016-express-localdb.md)  
  
 LocalDB позволяет выполнять следующие действия.  
  
-   Использовать программу **sqllocaldb.exe i** для поиска имени экземпляра по умолчанию.  
  
-   Использовать ключевое слово строки подключения **AttachDBFilename** для указания файла базы данных, который сервер должен присоединить. Если при использовании **AttachDBFilename**не указано имя базы данных в ключевом слове строки подключения **Database** , то база данных будет удалена из экземпляра LocalDB при закрытии приложения.  
  
-   Чтобы указать экземпляр LocalDB в строке подключения, выполните следующие действия.  
  
```  
SERVER=(localdb)\v11.0  
```  
  
 При необходимости можно создать экземпляр LocalDB с помощью программы sqllocaldb.exe. Для добавления и изменения баз данных в локальном экземпляре LocalDB можно также воспользоваться программой sqlcmd.exe. Например, **sqlcmd -S (localdb)\v11.0**.  
  
## <a name="see-also"></a>См. также:  
 [Возможности драйвера OLE DB для SQL Server](../../oledb/features/oledb-driver-for-sql-server-features.md)  
  
  
