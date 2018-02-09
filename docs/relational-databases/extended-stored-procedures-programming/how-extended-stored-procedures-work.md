---
title: "Принципы работы расширенных хранимых процедур | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: extended-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], about extended stored procedures
ms.assetid: 6e946d8c-3268-4b59-8a1c-1637909cd701
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: eb9c6663cd2891669140c7eb59e44e110f3d5607
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="how-extended-stored-procedures-work"></a>Принципы работы расширенных хранимых процедур
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Используйте вместо этого интеграцию со средой CLR.  
  
 Принцип работы расширенной хранимой процедуры заключается в следующем.  
  
1.  Когда клиент выполняет расширенную хранимую процедуру, запрос передается в поток табличных данных (TDS) или формате Simple Object Access Protocol (SOAP) из клиентского приложения для [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
2.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ищет DLL-Библиотеки, связанные с расширенной хранимой процедуры и загружает библиотеку DLL, если он еще не загружен.  
  
3.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] вызывает запрошенную расширенную хранимую процедуру (реализованную как функцию внутри DLL).  
  
4.  Расширенная хранимая процедура передает результирующий набор и возвращает параметры обратно на сервер через API-интерфейс расширенной хранимой процедуры.  
  
## <a name="see-also"></a>См. также  
 [Программирование расширенных хранимых процедур ядра СУБД](../../relational-databases/database-engine-extended-stored-procedure-programming.md)  
  
  
