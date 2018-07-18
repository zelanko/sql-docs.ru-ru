---
title: '@@SERVERNAME (Transact-SQL) | Документы Майкрософт'
ms.custom: ''
ms.date: 09/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- '@@SERVERNAME'
- '@@SERVERNAME_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- '@@SERVERNAME function'
- local servers [SQL Server]
ms.assetid: b0ef33fb-954a-4294-b05b-a87c14ce25a3
caps.latest.revision: 34
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a0adbdba1c04ad4cc2e39f532ded83d3964a47ea
ms.sourcegitcommit: 05e18a1e80e61d9ffe28b14fb070728b67b98c7d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/04/2018
ms.locfileid: "37787365"
---
# <a name="x40x40servername-transact-sql"></a>@@SERVERNAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает имя локального сервера, на котором работает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  

[!INCLUDE[ssMIlimitation](../../includes/sql-db-mi-limitation.md)]

 ![Значок ссылки на статью](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на статью") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
@@SERVERNAME  
```  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 **nvarchar**  
  
## <a name="remarks"></a>Remarks  
 Программа установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] присваивает серверу имя компьютера. Чтобы изменить имя сервера, выполните процедуру **sp_addserver**, а затем перезапустите [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 При наличии нескольких установленных экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] функция @@SERVERNAME возвращает указанные ниже сведения об имени локального сервера, если это имя не было изменено после установки.  
  
|Экземпляр|Информация о сервере|  
|--------------|------------------------|  
|Экземпляр по умолчанию|'*имя_сервера*'|  
|Именованный экземпляр|'*имя_сервера*\\*имя_экземпляра*'|  
|экземпляр отказоустойчивого кластера — экземпляр по умолчанию|'*имя_виртуального_сервера*'|  
|экземпляр отказоустойчивого кластера — именованный экземпляр|'*имя_виртуального_сервера*\\*имя_экземпляра*'|  
  
 Хотя функция @@SERVERNAME и свойство SERVERNAME функции SERVERPROPERTY могут возвращать строки в похожих форматах, эта информация может различаться. Свойство SERVERNAME автоматически сообщает об изменениях сетевого имени компьютера.  
  
 Функция @@SERVERNAME, напротив, не сообщает о таких изменениях. Функция @@SERVERNAME информирует об изменении имени локального сервера, которое было выполнено с помощью хранимых процедур **sp_addserver** или **sp_dropserver**.  
  
## <a name="examples"></a>Примеры  
 Следующий пример демонстрирует использование процедуры `@@SERVERNAME`.  
  
```  
SELECT @@SERVERNAME AS 'Server Name'  
```  
  
 Ниже приводится образец результирующего набора.  
  
```  
Server Name  
---------------------------------  
ACCTG  
  
```  
  
## <a name="see-also"></a>См. также:  
 [Функции настройки (Transact-SQL)](../../t-sql/functions/configuration-functions-transact-sql.md)   
 [SERVERPROPERTY (Transact-SQL)](../../t-sql/functions/serverproperty-transact-sql.md)   
 [sp_addserver (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addserver-transact-sql.md)  
  
  
