---
title: "FLUSHAUTHCACHE DBCC (Transact-SQL) | Документы Microsoft"
ms.custom:
- MSDN content
- MSDN - SQL DB
ms.date: 07/16/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DBCC FLUSHAUTHCACHE
- FLUSHAUTHCACHE
- DBCC_FLUSHAUTHCACHE_TSQL
- FLUSHAUTHCACHE_TSQL
helpviewer_keywords:
- DBCC FLUSHAUTHCACHE
ms.assetid: 681ef31d-ceb9-4da5-86bf-bf1240df950f
caps.latest.revision: 11
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3ba6a519ebcdbbc70bf19ec491539a3b07fb6c85
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="dbcc-flushauthcache-transact-sql"></a>FLUSHAUTHCACHE DBCC (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

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
  
  

