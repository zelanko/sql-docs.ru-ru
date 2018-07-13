---
title: MSSQLSERVER_1457 | Документация Майкрософт
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 1457 (Database Engine error)
ms.assetid: 28434ba1-b033-4866-ab41-111fccef45a2
caps.latest.revision: 15
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d0cf2eed90e1aea1f636322a0a728720222e0935
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37423483"
---
# <a name="mssqlserver1457"></a>MSSQLSERVER_1457
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|1457|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|DBM_PAGE_UNDO_PENDING|  
|Текст сообщения|Синхронизация зеркальной базы данных «%.*ls» прервана, база данных осталась в несогласованном состоянии. Ошибка при выполнении команды ALTER DATABASE. Убедитесь, что создана резервная копия зеркальной базы данных и она находится в режиме «в сети», а затем подключите заново экземпляр зеркального сервера и дайте возможность зеркальной базе данных завершить синхронизацию.|  
  
## <a name="explanation"></a>Объяснение  
 Это сообщение указывает на неуспешное завершение инструкции ALTER DATABASE *имя_базы_данных* SET PARTNER OFF. Неуспешная попытка удалить зеркальное отображение базы данных прервала синхронизацию зеркальной базы данных. База данных в несогласованном состоянии.  
  
## <a name="user-action"></a>Действие пользователя  
 Для устранения этой ошибки можно предпринять одно из следующих действий.  
  
-   Восстановите связь между зеркальным и основным сервером, чтобы обеспечить синхронизацию зеркальной базы данных.  
  
-   Удалите зеркальную базу данных.  
  
     После удаления зеркальной базы данных можно создать новую базу данных из резервных копий.  
  
    > [!NOTE]  
    >  Удалить зеркальную базу данных при включенном зеркальном отображении можно только после того, как инструкция SET PARTNER OFF завершается ошибкой.  
  
## <a name="see-also"></a>См. также  
 [Зеркальное отображение базы данных (SQL Server)](../../database-engine/database-mirroring/database-mirroring-sql-server.md)   
 [ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql)   
 [Настройка зеркального отображения базы данных (SQL Server)](../../database-engine/database-mirroring/setting-up-database-mirroring-sql-server.md)   
 [Удаление зеркального отображения базы данных (SQL Server)](../../database-engine/database-mirroring/removing-database-mirroring-sql-server.md)   
 [Подготовка зеркальной базы данных к зеркальному отображению (SQL Server)](../../database-engine/database-mirroring/prepare-a-mirror-database-for-mirroring-sql-server.md)  
  
  
