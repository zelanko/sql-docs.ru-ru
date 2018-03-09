---
title: "MSSQLSERVER_ 10785 | Документация Майкрософт"
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 10785 (Database Engine error)
ms.assetid: 32f96c1e-9e94-4603-9bcd-b0c2e4af9fda
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0e1bbd7fd69ada1530d8e8efc4a63f7d7b901e99
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver10785"></a>MSSQLSERVER_10785
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|MSSQLSERVER|  
|Идентификатор события|10785|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|P3_HEKATON_XACT|  
|Текст сообщения|*Построение* "*функция*" не поддерживается для активных транзакций, которые обращаются к оптимизированным для памяти таблицам или скомпилированным в собственном коде хранимым процедурам.|  
  
## <a name="user-action"></a>Действие пользователя  
Список неподдерживаемых компонентов и рекомендации по альтернативным решениям см. в статье [Конструкции языка Transact-SQL, не поддерживаемые в In-Memory OLTP](~/relational-databases/in-memory-oltp/transact-sql-constructs-not-supported-by-in-memory-oltp.md).  
  
Дополнительные сведения см. в разделе [In-Memory OLTP (оптимизация в памяти)](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
