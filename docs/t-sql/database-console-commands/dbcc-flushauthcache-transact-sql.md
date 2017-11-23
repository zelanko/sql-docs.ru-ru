---
title: "FLUSHAUTHCACHE DBCC (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: t-sql|database-console-commands
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DBCC FLUSHAUTHCACHE
- FLUSHAUTHCACHE
- DBCC_FLUSHAUTHCACHE_TSQL
- FLUSHAUTHCACHE_TSQL
helpviewer_keywords: DBCC FLUSHAUTHCACHE
ms.assetid: 681ef31d-ceb9-4da5-86bf-bf1240df950f
caps.latest.revision: "11"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 18fe9c70a774bce85bfdb8a59b54b57064e6c1ad
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="dbcc-flushauthcache-transact-sql"></a>FLUSHAUTHCACHE DBCC (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

Очищает кэш проверки подлинности базы данных, содержащий сведения об именах входа и правила брандмауэра, для текущей базы данных пользователя в [!INCLUDE[ssSDS](../../includes/sssds-md.md)]. Этот оператор неприменим логической базе данных master, так как база данных master содержит физическое хранилище для информации об именах входа и правила брандмауэра. Пользователь, выполняющий инструкцию и других пользователей, подключенных оставались подключенными. (DBCC FLUSHAUTHCACHE в настоящее время не поддерживается для [!INCLUDE[ssSDW_md](../../includes/sssdw-md.md)].)
 
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
DBCC FLUSHAUTHCACHE [ ; ]  
```  
  
## <a name="arguments"></a>Аргументы  
Нет.
  
## <a name="remarks"></a>Замечания  
Кэш проверки подлинности копия имена входа и правила брандмауэра сервера, которые хранятся в базе данных master и помещает их в памяти в базе данных пользователей.  Поскольку сведения о пользователях автономной базы данных уже были сохранены в базе данных пользователей, пользователи автономной базы данных не являются частью кэш проверки подлинности.
Постоянно активных подключений к [!INCLUDE[ssSDS](../../includes/sssds-md.md)] требуется повторная авторизация (выполненных [!INCLUDE[ssDE](../../includes/ssde-md.md)]) каждые 10 часов. [!INCLUDE[ssDE](../../includes/ssde-md.md)] Ввода попыток повторная авторизация с помощью изначально отправлено пароль и пользователь не является обязательным. Для повышения производительности при сбросе пароля в [!INCLUDE[ssSDS](../../includes/sssds-md.md)], соединение не будет повторно пройти проверку подлинности, даже если сброс подключения из-за пулов соединений. Это поведение отличается от поведения локального [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Если пароль был изменен с момента подключения изначально был авторизован, необходимо завершить соединения и установить новое соединение с помощью нового пароля. Пользователь с разрешением KILL DATABASE CONNECTION можно явно разрыва подключения к [!INCLUDE[ssSDS](../../includes/sssds-md.md)] с помощью [KILL &#40; Transact-SQL &#41; ](../../t-sql/language-elements/kill-transact-sql.md) команды.
  
## <a name="permissions"></a>Permissions  
Требуется [!INCLUDE[ssSDS](../../includes/sssds-md.md)] учетная запись администратора.
  
## <a name="example"></a>Пример  
Следующая инструкция удаляет кэш проверки подлинности в текущей базе данных.
  
```sql
DBCC FLUSHAUTHCACHE;  
```  
  
## <a name="see-also"></a>См. также:  
[DBCC (Transact-SQL)](../../t-sql/database-console-commands/dbcc-transact-sql.md)
  
  
