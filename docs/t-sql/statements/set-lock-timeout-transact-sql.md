---
title: SET LOCK_TIMEOUT (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 09/11/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
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
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: df2683d7a0c580624dd56aa8d35e183ab7ac6bbf
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62942812"
---
# <a name="set-locktimeout-transact-sql"></a>SET LOCK_TIMEOUT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Указывает количество миллисекунд, в течение которых инструкция ожидает снятия блокировки.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
SET LOCK_TIMEOUT timeout_period  
```  
  
## <a name="arguments"></a>Аргументы  
 *timeout_period*  
 Количество миллисекунд до того, как [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] вернет ошибку блокировки. Значение -1 (по умолчанию) указывает на отсутствие времени ожидания (то есть инструкция будет ждать всегда).  
  
 Когда ожидание блокировки превышает значение времени ожидания, возвращается ошибка. Значение «0» означает, что ожидание отсутствует, а сообщение возвращается, как только встречается блокировка.  
  
## <a name="remarks"></a>Remarks  
 В начале соединения этот параметр имеет значение -1. После изменения новое значение остается в силе в течение работы соединения.  
  
 Настройка SET LOCK_TIMEOUT установлена на запуск во время выполнения, но не во время синтаксического анализа.  
  
 Рекомендация блокировки READPAST представляет собой альтернативу данному параметру SET.  
  
 Инструкции CREATE DATABASE, ALTER DATABASE и DROP DATABASE не поддерживают настройки SET LOCK_TIMEOUT.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо быть членом роли **public**.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-set-the-lock-timeout-to-1800-milliseconds"></a>A. Установка времени ожидания блокировки равным 1800 миллисекундам  
 В следующем примере время ожидания блокировки устанавливается на `1800` миллисекунд.  
  
```sql  
SET LOCK_TIMEOUT 1800;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="b-set-the-lock-timeout-to-wait-forever-for-a-lock-to-be-released"></a>Б. Установка для времени ожидания бесконечного ожидания снятия блокировки.  
 В следующем примере для времени ожидания блокировки задается бесконечное ожидание и неограниченная длительность. Это поведение по умолчанию, которое уже задано в начале каждого подключения.  
  
```sql  
SET LOCK_TIMEOUT -1;  
```  
  
 В следующем примере время ожидания блокировки устанавливается на `1800` миллисекунд. В этом выпуске [!INCLUDE[ssDW](../../includes/ssdw-md.md)] начнет успешно анализировать инструкцию, но будет игнорировать значение 1800 и продолжать использовать поведение по умолчанию.  
  
```sql  
SET LOCK_TIMEOUT 1800;  
```  
  
## <a name="see-also"></a>См. также:  
 [@@LOCK_TIMEOUT (Transact-SQL)](../../t-sql/functions/lock-timeout-transact-sql.md)   
 [Инструкции SET (Transact-SQL)](../../t-sql/statements/set-statements-transact-sql.md)  
  
  

