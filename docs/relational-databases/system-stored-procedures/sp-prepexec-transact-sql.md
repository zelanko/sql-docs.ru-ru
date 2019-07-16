---
title: sp_prepexec (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_cursor_prepexec
- sp_cursor_prepexec_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_prepexec
ms.assetid: f9141850-a62b-43bf-8e46-b2f92b75ca56
author: stevestein
ms.author: sstein
ms.openlocfilehash: 163bbe741b09ffe9163b124c4223a845b8b8cd8f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68056360"
---
# <a name="spprepexec-transact-sql"></a>sp_prepexec (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Подготавливает и выполняет параметризованную [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкции. sp_prepexec объединяет в себе процедуры sp_prepare и sp_execute. Вызывается с ID =13 в пакете потока табличных данных (TDS).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_prepexec handle OUTPUT, params , stmt  
    [ , bound param ] [ ,...n]]  
```  
  
## <a name="arguments"></a>Аргументы  
 *Дескриптор*  
 — [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Созданный *обрабатывать* идентификатор. *обрабатывать* является обязательным параметром с **int** возвращаемое значение.  
  
 *params*  
 Указывает параметризованные инструкции. *Params* определения переменных подставляется вместо маркеров параметров в инструкции. *params* является обязательным параметром, который вызывает для **ntext**, **nchar**, или **nvarchar** входного значения. Если инструкция не параметризована, необходимо ввести значение NULL.  
  
 *stmt*  
 Определяет результирующий набор курсора. *Stmt* параметр является обязательным и требует **ntext**, **nchar** или **nvarchar** входного значения.  
  
 *bound_param*  
 Означает необязательное использование дополнительных параметров. *bound_param* вызывает для входного значения любого типа данных для обозначения дополнительных параметров.  
  
## <a name="examples"></a>Примеры  
 В следующем примере подготавливается и выполняется простая инструкция.  
  
```  
Declare @P1 int;  
EXEC sp_prepexec @P1 output,   
    N'@P1 nvarchar(128), @P2 nvarchar(100)',  
    N'SELECT database_id, name  
      FROM sys.databases  
      WHERE name=@P1 AND state_desc = @P2',   
@P1 = 'tempdb', @P2 = 'ONLINE';   
EXEC sp_unprepare @P1;  
```  
  
## <a name="see-also"></a>См. также  
 [sp_prepare &#40;Transact SQL&#41;](../../relational-databases/system-stored-procedures/sp-prepare-transact-sql.md)   
 [sp_execute &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-execute-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
