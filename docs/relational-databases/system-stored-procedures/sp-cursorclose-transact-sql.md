---
title: sp_cursorclose (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_cursor_close_TSQL
- sp_cursor_close
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cursorclose
ms.assetid: d9b7b44d-cdff-456e-97df-7031a3b9beb6
author: stevestein
ms.author: sstein
ms.openlocfilehash: 543e8c0b41000ec2afe9ab07aef08aa86967c2ce
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68108559"
---
# <a name="sp_cursorclose-transact-sql"></a>sp_cursorclose (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Закрывает и размещает курсор, а также освобождает все связанные ресурсы; то есть удаляется временная таблица, используемая для поддержки ключевого набора ключей или статического **курсора**. sp_cursorclose вызывается путем указания ID = 9 в пакете потока табличных данных (TDS).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_cursorclose cursor  
```  
  
## <a name="arguments"></a>Аргументы  
 *набора*  
 Значение *обработчика* курсора, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] созданное и возвращаемое процедурой sp_cursoropen. *cursor* является обязательным параметром, который вызывает входное значение **int** .  
  
> [!NOTE]  
>  Входное значение -1 относится ко всем курсорам в текущем соединении.  
  
## <a name="remarks"></a>Remarks  
 *курсор* возвратит сообщения об ошибках, если процедура была выполнена после закрытия курсора или если указан недопустимый маркер.  
  
 Состояние RPC обозначает общий успех или общий неуспех.  
  
 Счетчик строк DONE всегда равен 0.  
  
## <a name="see-also"></a>См. также:  
 [sp_cursoropen &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-cursoropen-transact-sql.md)   
 [Системные хранимые процедуры &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
