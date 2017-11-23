---
title: "SET REMOTE_PROC_TRANSACTIONS (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- REMOTE_PROC_TRANSACTIONS_TSQL
- SET REMOTE_PROC_TRANSACTIONS
- REMOTE_PROC_TRANSACTIONS
- SET_REMOTE_PROC_TRANSACTIONS_TSQL
dev_langs: TSQL
helpviewer_keywords:
- remote stored procedures [SQL Server]
- SET REMOTE_PROC_TRANSACTIONS statement
- distributed transactions [SQL Server], starting
- REMOTE_PROC_TRANSACTIONS option
- active transactions
ms.assetid: 4d284ae9-3f5f-465a-b0dd-1328a4832a03
caps.latest.revision: "37"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 97d4599c98e68a3cf4bd8682ec2b4601aec19568
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="set-remoteproctransactions-transact-sql"></a>SET REMOTE_PROC_TRANSACTIONS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Указывает, когда активна локальная транзакция, выполнение удаленной хранимой процедуры запускает [!INCLUDE[tsql](../../includes/tsql-md.md)] распределенной транзакции управляются [!INCLUDE[msCoName](../../includes/msconame-md.md)] координатора распределенных транзакций (MS DTC).  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextDontUse](../../includes/ssnotedepnextdontuse-md.md)] Этот параметр предоставлен, чтобы обеспечить обратную совместимость для приложений, использующих удаленные хранимые процедуры. Вместо вызова удаленных хранимых процедур используйте распределенные запросы, ссылающиеся на связанные серверы. Они определяются с помощью [sp_addlinkedserver](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SET REMOTE_PROC_TRANSACTIONS { ON | OFF }   
```  
  
## <a name="arguments"></a>Аргументы  
 ON | OFF  
 Если указан аргумент ON, то распределенная транзакция [!INCLUDE[tsql](../../includes/tsql-md.md)] запускается при выполнении удаленной хранимой процедуры из локальной транзакции. Если указан аргумент OFF, вызов удаленных хранимых процедур из локальной транзакции не приводит к запуску распределенной транзакции [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
## <a name="remarks"></a>Замечания  
 Если REMOTE_PROC_TRANSACTIONS установлен на ON, вызов удаленной хранимой процедуры приводит к запуску распределенной транзакции и привлекает к выполнению транзакции MS DTC. Экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], вызывающий удаленную хранимую процедуру, является инициатором транзакции и контролирует ее завершение. Когда последующая инструкция COMMIT TRANSACTION или ROLLBACK TRANSACTION выдается для соединения, контролирующий экземпляр предписывает MS DTC управлять завершением распределенной транзакции на всех вовлеченных компьютерах.  
  
 После запуска распределенной транзакции [!INCLUDE[tsql](../../includes/tsql-md.md)] могут выполняться вызовы удаленных хранимых процедур обращениями к другим экземплярам [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], определенным в качестве удаленных серверов. Все удаленные серверы связаны с распределенной транзакцией [!INCLUDE[tsql](../../includes/tsql-md.md)], и MS DTC обеспечивает завершение транзакции на каждом из удаленных серверов.  
  
 REMOTE_PROC_TRANSACTIONS является параметром уровня соединения, который может использоваться для переопределения уровня экземпляра **удаленного proc trans хранимой процедуры sp_configure** параметр.  
  
 Если REMOTE_PROC_TRANSACTIONS установлен на OFF, вызовы удаленных хранимых процедур не становятся частью локальной транзакции. Изменения, произведенные удаленной хранимой процедурой, подтверждаются или откатываются в момент завершения выполнения хранимой процедуры. Последующие инструкции COMMIT TRANSACTION или ROLLBACK TRANSACTION, выданные соединением, которым была вызвана удаленная хранимая процедура, не оказывают воздействия на обработку, выполненную процедурой.  
  
 Параметр REMOTE_PROC_TRANSACTIONS является параметром совместимости, который влияет на вызовы только удаленных хранимых процедур, направленные экземплярам [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] определяется как удаленными серверами с использованием **sp_addserver**. Этот параметр не применяется к распределенным запросам, выполнить хранимую процедуру на экземпляре, определенном в качестве связанного сервера с использованием **sp_addlinkedserver**.  
  
 Параметр SET REMOTE_PROC_TRANSACTIONS устанавливается во время выполнения или запуска, но не во время синтаксического анализа.  
  
## <a name="permissions"></a>Permissions  
 Необходимо быть членом роли **public** .  
  
## <a name="see-also"></a>См. также:  
 [BEGIN DISTRIBUTED TRANSACTION (Transact-SQL)](../../t-sql/language-elements/begin-distributed-transaction-transact-sql.md)   
 [Инструкции SET (Transact-SQL)](../../t-sql/statements/set-statements-transact-sql.md)  
  
  
