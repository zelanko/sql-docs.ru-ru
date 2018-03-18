---
title: "SET PARSEONLY (Transact-SQL) | Документы Майкрософт"
ms.custom: 
ms.date: 11/27/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- PARSEONLY_TSQL
- SET_PARSEONLY_TSQL
- PARSEONLY
- SET PARSEONLY
dev_langs:
- TSQL
helpviewer_keywords:
- parsing [SQL Server], SET PARSEONLY statement
- checking syntax
- PARSEONLY option
- syntax [SQL Server], verifying
- verifying syntax
- SET PARSEONLY statement
ms.assetid: 514ab042-c53e-4d96-be71-fb08fcc6ef3c
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: eb009b23f9d4a751f6850218f4845c6c70c3bbd3
ms.sourcegitcommit: 531d0245f4b2730fad623a7aa61df1422c255edc
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/01/2017
---
# <a name="set-parseonly-transact-sql"></a>SET PARSEONLY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-asdb-asdw-pdw-md.md)]

  Исследует синтаксис каждой инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] и возвращает сообщения об ошибках без компиляции или выполнения инструкции.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SET PARSEONLY { ON | OFF }  
```  
  
## <a name="remarks"></a>Remarks  
 Если для SET PARSEONLY установлено значение ON, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] только осуществляет синтаксический анализ инструкции. Если для SET PARSEONLY установлено значение OFF, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] компилирует и выполняет инструкцию.  
  
 Установка значения SET PARSEONLY осуществляется перед синтаксическим анализом, а не во время выполнения или запуска.  
  
 Не используйте PARSEONLY в хранимой процедуре или триггере. Инструкция SET PARSEONLY возвращает смещение, если параметру OFFSETS присвоено значение ON, и ошибки не возникают.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо быть членом роли **public** .  
  
## <a name="see-also"></a>См. также:  
 [Инструкции SET (Transact-SQL)](../../t-sql/statements/set-statements-transact-sql.md)   
 [SET OFFSETS (Transact-SQL)](../../t-sql/statements/set-offsets-transact-sql.md)  
  
  
