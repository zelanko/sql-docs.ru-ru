---
title: "Имя DLL-библиотеки DBCC (FREE) (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/16/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
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
caps.latest.revision: 27
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e6d70bdab3515c883ea6f541ece6857f8ecda914
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="dbcc-dllname-free-transact-sql"></a>DBCC dllname (FREE) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]Выгружает указанный расширенной хранимой процедуры DLL из памяти.
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
```sql
DBCC <dllname> ( FREE ) [ WITH NO_INFOMSGS ]  
```  
  
## <a name="arguments"></a>Аргументы  
 \<*имя DLL-библиотеки*>  
 Имя DLL-библиотеки, подлежащей удалению из памяти.  
  
 WITH NO_INFOMSGS  
 Подавляет вывод всех информационных сообщений.  
  
## <a name="remarks"></a>Замечания
При выполнении расширенной хранимой процедуры DLL-библиотека остается загруженной экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] до момента отключения сервера. Эта инструкция позволяет выгружать библиотеку DLL из памяти без отключения [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Для отображения DLL-файлов, загруженных в данный момент с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], выполнение **sp_helpextendedproc**
  
## <a name="result-sets"></a>Результирующие наборы  
При указании допустимой DLL-Библиотеки, DBCC *dllname* (FREE) возвращает:
  
```sql
DBCC execution completed. If DBCC printed error messages, contact your system administrator.  
```  
  
## <a name="permissions"></a>Permissions  
Необходимо быть членом предопределенной роли сервера **sysadmin** или предопределенной роли базы данных **db_owner** .
  
## <a name="examples"></a>Примеры  
В следующем примере предполагается, что `xp_sample` реализована как xp_sample.dll и была выполнена. DBCC \< *dllname*> (FREE) выгружает файл xp_sample.dll связанные с `xp_sample` расширенной процедуры.
  
```sql  
DBCC xp_sample (FREE);  
```  
  
## <a name="see-also"></a>См. также:  
[DBCC (Transact-SQL)](../../t-sql/database-console-commands/dbcc-transact-sql.md)  
[Характеристики выполнения расширенных хранимых процедур](../../relational-databases/extended-stored-procedures-programming/execution-characteristics-of-extended-stored-procedures.md)  
[sp_addextendedproc &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-addextendedproc-transact-sql.md)  
[sp_dropextendedproc &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-dropextendedproc-transact-sql.md)  
[sp_helpextendedproc &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helpextendedproc-transact-sql.md)  
[Выгрузка расширенной хранимой процедуры библиотеки DLL](../../relational-databases/extended-stored-procedures-programming/unloading-an-extended-stored-procedure-dll.md)
  
  

