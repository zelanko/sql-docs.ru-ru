---
title: "Параметр конфигурации сервера \"max full-text crawl range\" | Документы Майкрософт"
ms.custom: 
ms.date: 03/02/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: configure-windows
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- TSQL
helpviewer_keywords:
- crawls [full-text search]
- max full-text crawl range option
ms.assetid: a49de86b-0891-4dcd-89c0-ead30aab00e0
caps.latest.revision: 24
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 81514b4562657bb01d5d0ec841dc5e6ec1865099
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="max-full-text-crawl-range-server-configuration-option"></a>Параметр конфигурации сервера «max full-text crawl range»
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Параметр **max full-text crawl range** применяется для оптимизации использования ЦП, что позволяет улучшить производительность полнотекстового сканирования. С помощью этого параметра можно указать количество секций, которые [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] будет использовать при полном сканировании индекса. Например, при неоптимальном использовании нескольких ЦП значение этого параметра можно увеличить до максимума. Помимо этого параметра, определение фактического числа используемых секций в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] производится с учетом ряда других факторов, например количества строк в таблице или количества ЦП.  
  
 Значение этого параметра по умолчанию равно 4, минимальное значение равно 1, а максимальное значение равно 256. Изменения этого параметра влияют только на последующие процессы сканирования. Изменение этого параметра не влияет на еще незавершенные процессы сканирования.  
  
 Параметр **max full-text crawl range** относится к дополнительным параметрам. При вызове системной хранимой процедуры **sp_configure** параметр **max full-text crawl range** может быть изменен только в том случае, если параметр **show advanced options** установлен в значение 1. Параметр вступает в силу сразу без перезапуска сервера.  
  
## <a name="see-also"></a>См. также:  
 [RECONFIGURE (Transact-SQL)](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  

