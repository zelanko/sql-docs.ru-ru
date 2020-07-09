---
title: DBCC TRACEON (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 07/17/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DBCC_TRACEON_TSQL
- TRACEON
- DBCC TRACEON
- TRACEON_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- DBCC TRACEON statement
- trace flags [SQL Server], enabling
ms.assetid: 93085324-ebaa-4e38-aac8-5e57b4b0d36d
author: pmasl
ms.author: umajay
ms.openlocfilehash: ace26fc4586a3833217aca5a0330097b7f084024
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85896251"
---
# <a name="dbcc-traceon-transact-sql"></a>DBCC TRACEON (Transact-SQL)
[!INCLUDE [SQL Server - ASDBMI](../../includes/applies-to-version/sql-asdbmi.md)]

Активирует указанные флаги трассировки.
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```syntaxsql
DBCC TRACEON ( trace# [ ,...n ][ , -1 ] ) [ WITH NO_INFOMSGS ]  
```  
  
## <a name="arguments"></a>Аргументы  
*trace#*  
Номер флага трассировки, подлежащего активации.  
  
*n*  
Заполнитель, показывающий, что можно задавать несколько флагов трассировки.  
  
-1  
Включает указанные флаги трассировки глобально. Этот аргумент является обязательным в Управляемом экземпляре Azure SQL. 
  
WITH NO_INFOMSGS  
Подавляет вывод всех информационных сообщений.  
  
## <a name="remarks"></a>Remarks  
На рабочем сервере, чтобы избежать непредсказуемого поведения, рекомендуется активировать флаги трассировки по всему серверу используя только следующие способы.
-   Используйте в командной строке параметр **-T** при запуске файла Sqlservr.exe. Этот метод рекомендуется как наилучший, поскольку обеспечивает выполнение всех инструкций с установленным флагом трассировки. Сюда относятся команды в скриптах запуска. Дополнительные сведения см. в статье [sqlservr Application](../../tools/sqlservr-application.md).  
-   Используйте DBCC TRACEON **(** _trace#_ [ **,** ... *.n*] **,-1)** только тогда, когда пользователи или приложения не выполняют параллельно инструкции в системе.  

Флаги трассировки используются для пользовательской настройки определенных характеристик в целях управления работой [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. После активации флаги трассировки остаются включенными на сервере до отключения их посредством выполнения инструкции DBCC TRACEOFF. В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] существуют два типа флагов трассировки: для сеанса и глобальные. Флаги трассировки сеанса действуют во время данного соединения и доступны только для этого соединения. Глобальные флаги трассировки устанавливаются на уровне сервера и доступны для каждого соединения с этим сервером. Чтобы определить состояние флага трассировки, используйте инструкцию DBCC TRACESTATUS. Чтобы отключить флаги трассировки, используйте инструкцию DBCC TRACEOFF.
  
После включения флага трассировки, влияющего на планы запросов, выполните `DBCC FREEPROCCACHE;`, чтобы кэшированные планы были перекомпилированы с использованием нового поведения, определяющего влияние на планы.

Управляемый экземпляр Базы данных SQL Azure поддерживает следующие глобальные флаги трассировки: 460,2301,2389,2390,2453,2467,7471,8207,9389,10316 и 11024

## <a name="result-sets"></a>Результирующие наборы  
 Инструкция DBCC TRACEON возвращает следующий результирующий набор (сообщение):  
  
```sql
DBCC execution completed. If DBCC printed error messages, contact your system administrator.  
```  
  
## <a name="permissions"></a>Разрешения  
Необходимо членство в предопределенной роли сервера **sysadmin** .
  
## <a name="examples"></a>Примеры  
В нижеследующем примере отключается аппаратное сжатие для драйверов накопителей на магнитной ленте посредством включения флага трассировки `3205`. Эта метка включается только для текущего соединения.
  
```sql  
DBCC TRACEON (3205);  
GO  
```  
  
В нижеследующем примере флаг трассировки `3205` включается глобально.
  
```sql  
DBCC TRACEON (3205, -1);  
GO  
```  
  
В следующем примере флаги трассировки `3205` и `260` включаются глобально.
  
```sql  
DBCC TRACEON (3205, 260, -1);  
GO  
```  
  
## <a name="see-also"></a>См. также:  
[DBCC (Transact-SQL)](../../t-sql/database-console-commands/dbcc-transact-sql.md)  
[DBCC TRACEOFF (Transact-SQL)](../../t-sql/database-console-commands/dbcc-traceoff-transact-sql.md)  
[DBCC TRACESTATUS (Transact-SQL)](../../t-sql/database-console-commands/dbcc-tracestatus-transact-sql.md)  
[Флаги трассировки (Transact-SQL)](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)  
[Включение оптимизатора запросов SQL Server, влияющего на план выполнения, которым можно управлять с помощью разных флагов трассировки на уровне конкретного запроса](https://support.microsoft.com/kb/2801413)
  
  
