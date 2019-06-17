---
title: Переименуйте пользователя с именем sys | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- sys user names [SQL Server]
ms.assetid: d622d646-83e4-4b6f-9a21-77b301af04b5
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ce8656df63c9d415ca09b54ecb86b87aba8bd83a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66092862"
---
# <a name="rename-user-sys"></a>Переименуйте пользователя с именем sys
  Помощник по обновлению обнаружил в базе данных имя пользователя **sys** . Это имя зарезервировано. Переименуйте пользователя перед обновлением. Если пользователь не переименован, то после обновления база данных будет помечена как подозрительная и недоступна до тех пор, пока не будет переведена в режим «в сети».  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Описание  
 Пользователь **sys** зарезервирован.  
  
## <a name="corrective-action"></a>Действие по исправлению  
  
### <a name="before-upgrade-procedure"></a>Процедура перед началом обновления  
 Перед обновлением в каждой базе данных, содержащей пользователя **sys**, выполните следующие действия.  
  
1.  Создайте нового пользователя.  
  
2.  Используйте следующие инструкции, чтобы просмотреть все разрешения, предоставленные пользователем **sys** и предоставленные пользователю **sys**.  
  
    ```  
    -- Return permissions granted by user sys.  
    SELECT * FROM sysprotects WHERE grantor = USER_ID('sys')  
    -- Return permissions granted to user sys.  
    SELECT * FROM sysprotects WHERE uid = USER_ID('sys')  
    ```  
  
3.  Чтобы передать права владения для всех объектов, принадлежащих пользователю **sys** , новому пользователю, воспользуйтесь процедурой **sp_changeobjectowner**.  
  
4.  Удалите пользователя **sys**.  
  
5.  Чтобы восстановить первоначальные разрешения, записанные на шаге 2, используйте предложение AS *new_user* инструкции GRANT.  
  
6.  Измените скрипты, чтобы они ссылались на нового пользователя. Например, в скриптах необходимо изменить все инструкции, подобные `SELECT * FROM sys.my`_`table` , на `SELECT * FROM new_user.my_table`.  
  
### <a name="after-upgrade-procedure"></a>Процедура после обновления  
 Если пользователь **sys** не был переименован перед обновлением, выполните следующие действия.  
  
1.  Выполните инструкцию `ALTER DATABASE db_name SET ONLINE`. База данных перейдет в режим SINGLE_USER.  
  
2.  Выполните все шаги, описанные в разделе «Процедура перед началом обновления».  
  
3.  Выполните инструкцию `ALTER DATABASE db_name SET MULTI_USER`.  
  
## <a name="see-also"></a>См. также  
 [Проблемы обновления компонента Database Engine](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Помощник по обновлению SQL Server 2014 &#91;new&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
