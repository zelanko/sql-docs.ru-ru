---
title: Поддержка SQL Server Native Client для LocalDB | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 127569d1-a9f7-49bf-a561-c084986a8871
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3a3f5a8214c2966b1958c3a4ea08edbee5af6a2d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63225478"
---
# <a name="sql-server-native-client-support-for-localdb"></a>Поддержка SQL Server Native Client для LocalDB
  Начиная с версии [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], будет доступна облегченная версия SQL Server, называемая LocalDB. В этом разделе обсуждается, как можно установить соединение с базой данных на экземпляре LocalDB.  
  
## <a name="remarks"></a>Примечания  
 Дополнительные сведения о LocalDB, включая способы его установки и настройки, см. в разделе:  
  
-   [Справочник по SQL Server Express LocalDB](../../sql-server-express-localdb-reference.md)  
  
-   [SQL Server 2014 Express LocalDB](../../../database-engine/configure-windows/sql-server-2016-express-localdb.md)  
  
 LocalDB позволяет выполнять следующие действия.  
  
-   Использовать программу `sqllocaldb.exe i` для поиска имени экземпляра по умолчанию.  
  
-   Использовать ключевое слово строки подключения `AttachDBFilename` для указания файла базы данных, который сервер должен присоединить. При использовании `AttachDBFilename`, если вы не укажете имя базы данных с **базы данных** ключевое слово строки подключения базы данных удаляется из экземпляра LocalDB при закрытии приложения.  
  
-   Чтобы указать экземпляр LocalDB в строке подключения, выполните следующие действия.  
  
```  
SERVER=(localdb)\v11.0  
```  
  
 При необходимости можно создать экземпляр LocalDB с помощью программы sqllocaldb.exe. Для добавления и изменения баз данных в локальном экземпляре LocalDB можно также воспользоваться программой sqlcmd.exe. Например, `sqlcmd -S (localdb)\v11.0`.  
  
## <a name="see-also"></a>См. также  
 [Компоненты SQL Server Native Client](sql-server-native-client-features.md)  
  
  
