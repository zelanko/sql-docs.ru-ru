---
title: Параметр конфигурации сервера "max full-text crawl range" | Документы Майкрософт
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- crawls [full-text search]
- max full-text crawl range option
ms.assetid: a49de86b-0891-4dcd-89c0-ead30aab00e0
author: MikeRayMSFT
ms.author: mikeray
manager: jroth
ms.openlocfilehash: f7056c3e04648c55b0665d32c0097cc81a699196
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66775891"
---
# <a name="max-full-text-crawl-range-server-configuration-option"></a>Параметр конфигурации сервера max full-text crawl range
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Параметр **max full-text crawl range** применяется для оптимизации использования ЦП, что позволяет улучшить производительность полнотекстового сканирования. С помощью этого параметра можно указать количество секций, которые [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] будет использовать при полном сканировании индекса. Например, при неоптимальном использовании нескольких ЦП значение этого параметра можно увеличить до максимума. Помимо этого параметра, определение фактического числа используемых секций в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] производится с учетом ряда других факторов, например количества строк в таблице или количества ЦП.  
  
 Значение этого параметра по умолчанию равно 4, минимальное значение равно 1, а максимальное значение равно 256. Изменения этого параметра влияют только на последующие процессы сканирования. Изменение этого параметра не влияет на еще незавершенные процессы сканирования.  
  
 Параметр **max full-text crawl range** относится к дополнительным параметрам. При вызове системной хранимой процедуры **sp_configure** параметр **max full-text crawl range** может быть изменен только в том случае, если параметр **show advanced options** установлен в значение 1. Параметр вступает в силу сразу без перезапуска сервера.  
  
## <a name="see-also"></a>См. также:  
 [RECONFIGURE (Transact-SQL)](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  
