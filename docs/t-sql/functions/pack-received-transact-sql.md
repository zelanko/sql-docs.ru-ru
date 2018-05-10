---
title: '@@PACK_RECEIVED (Transact-SQL) | Документы Майкрософт'
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-database
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- '@@PACK_RECEIVED_TSQL'
- '@@PACK_RECEIVED'
dev_langs:
- TSQL
helpviewer_keywords:
- '@@PACK_RECEIVED function'
- number of packets read
- packets [SQL Server], number read
ms.assetid: 5c0b3d36-bfad-4f0b-abb8-e8f6391b32cd
caps.latest.revision: 18
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: b89ac13d1f9a545fd858e2c775904c871efb62f9
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="x40x40packreceived-transact-sql"></a>&#x40;&#x40;PACK_RECEIVED (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает количество входных пакетов, считанных из сети сервером [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с момента его последнего запуска.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
@@PACK_RECEIVED  
```  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 **integer**  
  
## <a name="remarks"></a>Remarks  
 Для отображения отчета, содержащего статистику по нескольким экземплярам [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], включая перечень полученных и переданных пакетов, выполните процедуру **sp_monitor**.  
  
## <a name="examples"></a>Примеры  
 В следующем примере показано использование функции `@@PACK_RECEIVED`.  
  
```  
SELECT @@PACK_RECEIVED AS 'Packets Received';   
```  
  
 Ниже приводится образец результирующего набора.  
  
```  
Packets Received  
----------------  
128  
```  
  
## <a name="see-also"></a>См. также:  
 [@@PACK_SENT](../../t-sql/functions/pack-sent-transact-sql.md)   
 [sp_monitor](../../relational-databases/system-stored-procedures/sp-monitor-transact-sql.md)   
 [Системные статистические функции](../../t-sql/functions/system-statistical-functions-transact-sql.md)  
  
  
