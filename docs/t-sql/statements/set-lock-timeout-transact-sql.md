---
title: "SET LOCK_TIMEOUT (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 09/11/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- LOCK_TIMEOUT_TSQL
- SET_LOCK_TIMEOUT_TSQL
- SET LOCK_TIMEOUT
- LOCK_TIMEOUT
dev_langs:
- TSQL
helpviewer_keywords:
- timeout options [SQL Server], locks
- releasing locks
- LOCK_TIMEOUT option
- SET LOCK_TIMEOUT statement
- locking [SQL Server], time-outs
- wait time for lock releases [SQL Server]
ms.assetid: dd0c389e-956d-435e-bf71-e16624a0a215
caps.latest.revision: 26
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 754242a86367b07b98caa9f70f457b70d0840075
ms.openlocfilehash: 3de86c7f33afd6e708ad8e773470ec650e092d2c
ms.contentlocale: ru-ru
ms.lasthandoff: 09/12/2017

---
# <a name="set-locktimeout-transact-sql"></a>SET LOCK_TIMEOUT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Указывает количество миллисекунд, в течение которых инструкция ожидает снятия блокировки.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
SET LOCK_TIMEOUT timeout_period  
```  
  
## <a name="arguments"></a>Аргументы  
 *timeout_period*  
 Количество миллисекунд до того, [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] вернет ошибку блокировки. Значение -1 (по умолчанию) указывает на отсутствие времени ожидания (то есть инструкция будет ждать всегда).  
  
 Когда ожидание блокировки превышает значение времени ожидания, возвращается ошибка. Значение «0» означает, что ожидание отсутствует, а сообщение возвращается, как только встречается блокировка.  
  
## <a name="remarks"></a>Замечания  
 В начале соединения этот параметр имеет значение -1. После изменения новое значение остается в силе в течение работы соединения.  
  
 Настройка SET LOCK_TIMEOUT установлена на запуск во время выполнения, но не во время синтаксического анализа.  
  
 Рекомендация блокировки READPAST представляет собой альтернативу данному параметру SET.  
  
 Инструкции CREATE DATABASE, ALTER DATABASE и DROP DATABASE не поддерживают настройки SET LOCK_TIMEOUT.  
  
## <a name="permissions"></a>Permissions  
 Необходимо быть членом роли **public** .  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-set-the-lock-timeout-to-1800-milliseconds"></a>Ответ задать время ожидания блокировки равным 1 800 миллисекундам  
 В следующем примере время ожидания блокировки устанавливается на `1800` миллисекунд.  
  
```sql  
SET LOCK_TIMEOUT 1800;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="b-set-the-lock-timeout-to-wait-forever-for-a-lock-to-be-released"></a>Б. Задайте время ожидания блокировки бесконечно ожидать снятия блокировки.  
 В следующем примере задается ждать бесконечно и никогда не истекает время ожидания блокировки. Это поведение по умолчанию, которая задана в начале каждого подключения.  
  
```sql  
SET LOCK_TIMEOUT -1;  
```  
  
 В следующем примере время ожидания блокировки устанавливается на `1800` миллисекунд. В этом выпуске [!INCLUDE[ssDW](../../includes/ssdw-md.md)] будет успешно, выполнить синтаксический анализ инструкции, но будет игнорировать значение 1800 и продолжать использовать поведение по умолчанию.  
  
```sql  
SET LOCK_TIMEOUT 1800;  
```  
  
## <a name="see-also"></a>См. также:  
 [@@LOCK_TIMEOUT &#40;Transact-SQL&#41;](../../t-sql/functions/lock-timeout-transact-sql.md)   
 [Инструкции SET (Transact-SQL)](../../t-sql/statements/set-statements-transact-sql.md)  
  
  


