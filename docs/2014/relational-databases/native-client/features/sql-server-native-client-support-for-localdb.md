---
title: Поддержка SQL Server Native Client для LocalDB | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client  - "database-engine" - "docset-sql-devref"
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 127569d1-a9f7-49bf-a561-c084986a8871
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c62b4a7c6db2bc7a53c616079d75110ff8c3ad95
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37414053"
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
  
  
