---
title: MSSQLSERVER_1457 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 1457 (Database Engine error)
ms.assetid: 28434ba1-b033-4866-ab41-111fccef45a2
caps.latest.revision: 14
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 7f5a3300cd0cd910492247a46855b130852b82f1
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver1457"></a>MSSQLSERVER_1457
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
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
    > Удалить зеркальную базу данных при включенном зеркальном отображении можно только после того, как инструкция SET PARTNER OFF завершается ошибкой.  
  
## <a name="see-also"></a>См. также:  
[Зеркальное отображение базы данных (SQL Server)](~/database-engine/database-mirroring/database-mirroring-sql-server.md)  
[ALTER DATABASE (Transact-SQL)](~/t-sql/statements/alter-database-transact-sql-set-options.md)  
[Настройка зеркального отображения базы данных (SQL Server)](~/database-engine/database-mirroring/setting-up-database-mirroring-sql-server.md)  
[Удаление зеркального отображения базы данных (SQL Server)](~/database-engine/database-mirroring/removing-database-mirroring-sql-server.md)  
[Подготовка зеркальной базы данных к зеркальному отображению (SQL Server)](~/database-engine/database-mirroring/prepare-a-mirror-database-for-mirroring-sql-server.md)  
  
