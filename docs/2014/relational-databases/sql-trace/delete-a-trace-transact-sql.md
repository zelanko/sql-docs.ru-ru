---
title: Удаление трассировки (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], deleting
- removing traces
- deleting traces
ms.assetid: a5502814-b281-42dd-b885-5c9368025ae6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b3551cff36ef6e2c2e9cc6a4d9b7056ae44cb950
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85068302"
---
# <a name="delete-a-trace-transact-sql"></a>удалить трассировку (Transact-SQL)
  В этом подразделе описано использование хранимых процедур для удаления трассировок.  
  
 Пример использования хранимых процедур трассировки см. в разделе [Создание трассировки (Transact-SQL)](create-a-trace-transact-sql.md).  
  
### <a name="to-delete-a-trace"></a>Удаление трассировки  
  
1.  Чтобы остановить трассировку, выполните процедуру **sp_trace_setstatus** , указав параметр **@status =0**.  
  
2.  Чтобы закрыть трассировку и удалить сведения о ней с сервера, выполните процедуру **sp_trace_setstatus** , указав параметр **@status =2**.  
  
> [!NOTE]  
>  Перед закрытием трассировка должна быть остановлена.  
  
## <a name="see-also"></a>См. также:  
 [Хранимая процедура sp_trace_setstatus (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql)   
 [Системные хранимые процедуры (Transact-SQL)](/sql/relational-databases/system-stored-procedures/system-stored-procedures-transact-sql)   
 [Хранимые процедуры приложения SQL Server Profiler (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sql-server-profiler-stored-procedures-transact-sql)  
  
  
