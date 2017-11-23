---
title: "НАБОР СМЕЩЕНИЯ (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SET_OFFSETS_TSQL
- OFFSETS_TSQL
- SET OFFSETS
- OFFSETS
dev_langs: TSQL
helpviewer_keywords:
- position relative to start of statement [SQL Server]
- OFFSETS option
- offsets [SQL Server]
- SET OFFSETS statement
ms.assetid: c7bcc697-0930-4630-acae-d8ccbfa4414c
caps.latest.revision: "25"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 232550be5756505082b615a84ccbd35ef84b1477
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="set-offsets-transact-sql"></a>SET OFFSETS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает смещение (позицию относительно начала инструкции) заданного ключевого слова в инструкциях [!INCLUDE[tsql](../../includes/tsql-md.md)] для приложений DB-Library.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
 
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SET OFFSETS keyword_list { ON | OFF }  
```  
  
## <a name="arguments"></a>Аргументы  
 *keyword_list*  
 Разделенный запятыми список конструкций [!INCLUDE[tsql](../../includes/tsql-md.md)], который включает в себя SELECT, FROM, ORDER, TABLE, PROCEDURE, STATEMENT, PARAM и EXECUTE.  
  
## <a name="remarks"></a>Замечания  
 SET OFFSETS используется только в приложениях DB-Library.  
  
 Значение SET OFFSETS устанавливается во время синтаксического анализа, но не во время исполнения. Установка во время синтаксического анализа означает, что если инструкция SET присутствует в пакете или хранимой процедуре, то она вступает в силу независимо от того, достигает ли фактическое выполнение кода соответствующей точки. Кроме того, инструкция SET вступает в силу до выполнения любых операторов. Например, даже если инструкция SET находится в блоке инструкций IF...ELSE, вход в который не осуществляется, инструкция SET, тем не менее, действует, поскольку блок инструкций IF...ELSE подлежит синтаксическому анализу.  
  
 Если инструкция SET OFFSETS установлена в хранимой процедуре, значение SET OFFSETS восстанавливается после того, как управление выходит из этой хранимой процедуры. Поэтому инструкция SET OFFSETS, определенная в динамическом коде SQL, не действует на инструкции, следующие за инструкцией динамического SQL.  
  
 Инструкция SET PARSEONLY возвращает смещение, если параметру OFFSETS присвоено значение ON, и ошибки не возникают.  
  
## <a name="permissions"></a>Permissions  
 Необходимо быть членом роли **public** .  
  
## <a name="see-also"></a>См. также:  
 [Инструкции SET (Transact-SQL)](../../t-sql/statements/set-statements-transact-sql.md)   
 [SET PARSEONLY &#40; Transact-SQL &#41;](../../t-sql/statements/set-parseonly-transact-sql.md)  
  
  
