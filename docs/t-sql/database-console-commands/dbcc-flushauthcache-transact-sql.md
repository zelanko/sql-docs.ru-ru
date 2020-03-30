---
title: DBCC FLUSHAUTHCACHE (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 07/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DBCC FLUSHAUTHCACHE
- FLUSHAUTHCACHE
- DBCC_FLUSHAUTHCACHE_TSQL
- FLUSHAUTHCACHE_TSQL
helpviewer_keywords:
- DBCC FLUSHAUTHCACHE
ms.assetid: 681ef31d-ceb9-4da5-86bf-bf1240df950f
author: VanMSFT
ms.author: vanto
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 00497dfe67c03eab4d9d0bc1798f6d5537628ed7
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "68101939"
---
# <a name="dbcc-flushauthcache-transact-sql"></a>DBCC FLUSHAUTHCACHE (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

Очищает кэш проверки подлинности базы данных, в котором содержатся сведения об именах для входа и правилах брандмауэра, для текущей пользовательской базы данных в [!INCLUDE[ssSDS](../../includes/sssds-md.md)]. Эта инструкция не применяется к логической базе данных master, так как у базы данных master есть физическое хранилище для сведений об именах для входа и правилах брандмауэра. Пользователь, выполняющий инструкцию, и другие подключенные в настоящее время пользователи остаются подключенными. (Инструкция DBCC FLUSHAUTHCACHE сейчас не поддерживается для [!INCLUDE[ssSDW_md](../../includes/sssdw-md.md)].)
 
![Значок ссылки на статью](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на статью") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
DBCC FLUSHAUTHCACHE [ ; ]  
```  
  
## <a name="arguments"></a>Аргументы  
Нет.
  
## <a name="remarks"></a>Remarks  
Кэш проверки подлинности создает копию имен для входа и правил брандмауэра сервера, хранящихся в базе данных master, и помещает их в память в пользовательской базе данных.  Так как сведения о пользователях автономной базы данных уже хранятся в пользовательской базе данных, ее пользователи данных не включаются в кэш проверки подлинности.
Для поддержания подключений к [!INCLUDE[ssSDS](../../includes/sssds-md.md)] в активном состоянии требуется повторная авторизация (выполняемая компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)]) по крайней мере каждые 10 часов. [!INCLUDE[ssDE](../../includes/ssde-md.md)] пытается выполнить повторную авторизацию с использованием первоначального пароля. Пользователю не нужно вводить никаких данных. Для повышения производительности при сбросе пароля в [!INCLUDE[ssSDS](../../includes/sssds-md.md)] повторная проверка подлинности подключения не проводится, даже если подключение сбрасывается из-за создания пула подключений. В локальном развертывании [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поведение иное. Если пароль изменился с момента первоначальной авторизации подключения, такое подключение должно быть завершено. Должно быть установлено новое подключение с использованием нового пароля. Пользователь с разрешением KILL DATABASE CONNECTION может явным образом завершить подключение к [!INCLUDE[ssSDS](../../includes/sssds-md.md)] с помощью команды [KILL (Transact-SQL)](../../t-sql/language-elements/kill-transact-sql.md).
  
## <a name="permissions"></a>Разрешения  
Требуется учетная запись администратора [!INCLUDE[ssSDS](../../includes/sssds-md.md)].
  
## <a name="example"></a>Пример  
Приведенная ниже инструкция очищает кэш проверки подлинности для текущей базы данных.
  
```sql
DBCC FLUSHAUTHCACHE;  
```  
  
## <a name="see-also"></a>См. также:  
[DBCC (Transact-SQL)](../../t-sql/database-console-commands/dbcc-transact-sql.md)
  
