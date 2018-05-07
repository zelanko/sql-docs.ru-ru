---
title: sp_cursorclose (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_cursor_close_TSQL
- sp_cursor_close
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cursorclose
ms.assetid: d9b7b44d-cdff-456e-97df-7031a3b9beb6
caps.latest.revision: 7
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: bb3db5049ff370a9dccad98dd7e90efb2e346f0f
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="spcursorclose-transact-sql"></a>sp_cursorclose (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Закрывает и отменяет распределение курсора, а также освобождает все связанные ресурсы; то есть удаляется временная таблица, используемая типа KEYSET или STATIC **курсор**. sp_cursorclose вызывается указанием ID = 9 в пакете потока табличных данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_cursorclose cursor  
```  
  
## <a name="arguments"></a>Аргументы  
 *курсор*  
 Является курсором *обработки* значение, сформированное [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и возвращенное процедурой sp_cursoropen. *курсор* является обязательным параметром, который вызывает для **int** входного значения.  
  
> [!NOTE]  
>  Входное значение -1 относится ко всем курсорам в текущем соединении.  
  
## <a name="remarks"></a>Замечания  
 *курсор* вернет сообщение об ошибке, если процедура выполняется после закрытия курсора или указан недопустимый дескриптор.  
  
 Состояние RPC обозначает общий успех или общий неуспех.  
  
 Счетчик строк DONE всегда равен 0.  
  
## <a name="see-also"></a>См. также  
 [sp_cursoropen &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-cursoropen-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
