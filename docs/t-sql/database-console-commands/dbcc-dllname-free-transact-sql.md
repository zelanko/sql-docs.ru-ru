---
title: "DBCC dllname (FREE) (Transact-SQL) | Документы Майкрософт"
ms.custom: 
ms.date: 07/16/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|database-console-commands
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dbcc_dllname_(FREE)_TSQL
- dllname
- dbcc dllname (FREE)
- FREE
- dbcc_dllname(FREE)_TSQL
- FREE_TSQL
- dllname_TSQL
- dbcc dllname(FREE)
dev_langs:
- TSQL
helpviewer_keywords:
- DLL unloading [SQL Server]
- DBCC dllname (FREE)
- freeing DLLs
- unloading DLLs
ms.assetid: 1eb71c17-fe15-430b-8916-e4e312dcf9c0
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0ad6b900d45ef1c87c0aca0d961685c68a72a33d
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="dbcc-dllname-free-transact-sql"></a>DBCC dllname (FREE) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)] Выгружает из памяти указанную библиотеку DLL расширенных хранимых процедур.
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
```sql
DBCC <dllname> ( FREE ) [ WITH NO_INFOMSGS ]  
```  
  
## <a name="arguments"></a>Аргументы  
 \<*dllname*>  
 Имя DLL-библиотеки, подлежащей удалению из памяти.  
  
 WITH NO_INFOMSGS  
 Подавляет вывод всех информационных сообщений.  
  
## <a name="remarks"></a>Remarks
При выполнении расширенной хранимой процедуры DLL-библиотека остается загруженной экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] до момента отключения сервера. Эта инструкция позволяет выгружать библиотеку DLL из памяти без отключения [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Для отображения DLL-файлов, загруженных в настоящее время средствами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], выполните процедуру **sp_helpextendedproc**.
  
## <a name="result-sets"></a>Результирующие наборы  
При указании допустимой библиотеки DLL команда DBCC *dllname* (FREE) возвращает:
  
```sql
DBCC execution completed. If DBCC printed error messages, contact your system administrator.  
```  
  
## <a name="permissions"></a>Разрешения  
Необходимо быть членом предопределенной роли сервера **sysadmin** или предопределенной роли базы данных **db_owner** .
  
## <a name="examples"></a>Примеры  
В приведенном ниже примере предполагается, что расширенная процедура `xp_sample` реализована как xp_sample.dll и была выполнена. DBCC \<*dllname*> (FREE) выгружает файл xp_sample.dll, связанный с расширенной процедурой `xp_sample`.
  
```sql  
DBCC xp_sample (FREE);  
```  
  
## <a name="see-also"></a>См. также:  
[DBCC (Transact-SQL)](../../t-sql/database-console-commands/dbcc-transact-sql.md)  
[Характеристики выполнения расширенных хранимых процедур](../../relational-databases/extended-stored-procedures-programming/execution-characteristics-of-extended-stored-procedures.md)  
[sp_addextendedproc (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addextendedproc-transact-sql.md)  
[sp_dropextendedproc (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-dropextendedproc-transact-sql.md)  
[sp_helpextendedproc (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helpextendedproc-transact-sql.md)  
[Выгрузка DLL-библиотеки расширенной хранимой процедуры](../../relational-databases/extended-stored-procedures-programming/unloading-an-extended-stored-procedure-dll.md)
  
  
