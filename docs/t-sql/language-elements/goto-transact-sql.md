---
title: "Оператор GOTO (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- GOTO
- GOTO_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- skipping statements
- Transact-SQL statements, skipping
- labels [SQL Server]
- statements [SQL Server], skipping
- GOTO statement
ms.assetid: 589b6f8e-dc80-416f-9e74-48bed5337f58
caps.latest.revision: 33
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 4c5614843f961d1ff3188ba1f3caa589d77c4735
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="goto-transact-sql"></a>GOTO (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Переводит поток выполнения на метку. Инструкции языка [!INCLUDE[tsql](../../includes/tsql-md.md)] или инструкции, следующие за инструкцией GOTO, пропускаются, и выполнение продолжается с метки. Инструкция GOTO и метки могут быть включены в процедуру, пакет или блок инструкций. Инструкции GOTO могут быть вложенными.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Define the label:   
label:   
Alter the execution:  
GOTO label   
```  
  
## <a name="arguments"></a>Аргументы  
 *Метка*  
 Точка, с которой начинается обработка инструкций после перехода на текущую метку с помощью инструкции GOTO. Метки должны соответствовать правилам для [идентификаторы](../../relational-databases/databases/database-identifiers.md). Метка может применяться без инструкции GOTO как метод комментирования.  
  
## <a name="remarks"></a>Замечания  
 Инструкция GOTO может существовать внутри условных инструкций, управляющих потоком, блоков инструкций или процедур, однако не может ссылаться на метку, расположенную вне этого пакета. Инструкция GOTO может ссылаться на метку, расположенную как до нее, так и после.  
  
## <a name="permissions"></a>Permissions  
 Разрешения GOTO по умолчанию предоставляются всем допустимым пользователям.  
  
## <a name="examples"></a>Примеры  
 В следующем примере показано, как использовать разрешения `GOTO` в качестве механизма ветви.  
  
```  
DECLARE @Counter int;  
SET @Counter = 1;  
WHILE @Counter < 10  
BEGIN   
    SELECT @Counter  
    SET @Counter = @Counter + 1  
    IF @Counter = 4 GOTO Branch_One --Jumps to the first branch.  
    IF @Counter = 5 GOTO Branch_Two  --This will never execute.  
END  
Branch_One:  
    SELECT 'Jumping To Branch One.'  
    GOTO Branch_Three; --This will prevent Branch_Two from executing.  
Branch_Two:  
    SELECT 'Jumping To Branch Two.'  
Branch_Three:  
    SELECT 'Jumping To Branch Three.';  
```  
  
## <a name="see-also"></a>См. также:  
 [Язык управления выполнением &#40; Transact-SQL &#41;](~/t-sql/language-elements/control-of-flow.md)   
 [BEGIN... КОНЕЦ &#40; Transact-SQL &#41;](../../t-sql/language-elements/begin-end-transact-sql.md)   
 [РАЗРЫВ &#40; Transact-SQL &#41;](../../t-sql/language-elements/break-transact-sql.md)   
 [ПРОДОЛЖИТЬ &#40; Transact-SQL &#41;](../../t-sql/language-elements/continue-transact-sql.md)   
 [IF... ELSE &#40; Transact-SQL &#41;](../../t-sql/language-elements/if-else-transact-sql.md)   
 [Инструкция WAITFOR &#40; Transact-SQL &#41;](../../t-sql/language-elements/waitfor-transact-sql.md)   
 [WHILE &#40;Transact-SQL&#41;](../../t-sql/language-elements/while-transact-sql.md)  
  
  

