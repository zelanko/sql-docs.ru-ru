---
title: SET PARSEONLY (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 11/27/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
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
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 069bc3ebb8423b24664a9b144471678a80c5ec95
ms.sourcegitcommit: 8ffc23126609b1cbe2f6820f9a823c5850205372
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2020
ms.locfileid: "81632998"
---
# <a name="set-parseonly-transact-sql"></a>SET PARSEONLY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Исследует синтаксис каждой инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] и возвращает сообщения об ошибках без компиляции или выполнения инструкции.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```syntaxsql
  
SET PARSEONLY { ON | OFF }  
```  
  
## <a name="remarks"></a>Remarks  
 Если для SET PARSEONLY установлено значение ON, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] только осуществляет синтаксический анализ инструкции. Если для SET PARSEONLY установлено значение OFF, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] компилирует и выполняет инструкцию.  
  
 Установка значения SET PARSEONLY осуществляется перед синтаксическим анализом, а не во время выполнения или запуска.  
  
 Не используйте PARSEONLY в хранимой процедуре или триггере. Инструкция SET PARSEONLY возвращает смещение, если параметру OFFSETS присвоено значение ON, и ошибки не возникают.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо быть членом роли **public**.  
  
## <a name="see-also"></a>См. также:  
 [Инструкции SET (Transact-SQL)](../../t-sql/statements/set-statements-transact-sql.md)   
 [SET OFFSETS (Transact-SQL)](../../t-sql/statements/set-offsets-transact-sql.md)  
  
  
