---
title: Поддержка LocalDB
description: Узнайте, как подключиться к базе данных в экземпляре LocalDB, которая является облегченной версией SQL Server, поддерживаемой SQL Server Native Client.
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 127569d1-a9f7-49bf-a561-c084986a8871
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: bc043b9e26f9a940575689b9392efef5b7ee1a4a
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.contentlocale: ru-RU
ms.lasthandoff: 07/06/2020
ms.locfileid: "86009892"
---
# <a name="sql-server-native-client-support-for-localdb"></a>Поддержка SQL Server Native Client для LocalDB
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

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
  
## <a name="see-also"></a>См. также  
 [Компоненты собственного клиента SQL Server](../../../relational-databases/native-client/features/sql-server-native-client-features.md)  
  
  
