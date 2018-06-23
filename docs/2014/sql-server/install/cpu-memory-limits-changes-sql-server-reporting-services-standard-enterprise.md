---
title: Изменения ограничений ЦП и памяти для SQL Server Reporting Services Standard и Enterprise | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dd553715-2b95-4119-8f58-d01de388d9ab
caps.latest.revision: 11
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 5097398d50c2e3072c31724cd16e56d63f5e7676
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36094733"
---
# <a name="changes-to-cpu-and-memory-limits-for-sql-server-reporting-services-standard-and-enterprise"></a>Изменения ограничений ЦП и памяти для выпусков служб SQL Server Reporting Services Standard Edition и Enterprise Edition
  Начиная с версии [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], выпуски служб Reporting Services Standard и Enterprise поддерживают до 64 ГБ системной памяти.  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
### <a name="description"></a>Описание  
 Начиная с версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], выпуски служб Reporting Services Standard и Enterprise поддерживают до 64 ГБ системной памяти. Может потребоваться повторно настроить параметры системы, чтобы поддерживать обновленные ограничения.  
  
 Дополнительные сведения об ограничениях ЦП и памяти для других выпусков [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], в разделе [Compute Capacity Limits by Edition of SQL Server](../compute-capacity-limits-by-edition-of-sql-server.md), и [памяти, поддерживаемые различными выпусками SQL Server](http://go.microsoft.com/fwlink/?LinkId=212633).  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Может потребоваться повторно настроить параметры системы, чтобы поддерживать обновленные ограничения. Дополнительные сведения см. в разделе [ALTER SERVER CONFIGURATION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-server-configuration-transact-sql), и [сервера параметров конфигурации памяти сервера](../../database-engine/configure-windows/server-memory-server-configuration-options.md).  
  
## <a name="see-also"></a>См. также  
 [Возможности, поддерживаемые различными выпусками SQL Server 2014](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)   
 [Обратная совместимость](../../../2014/getting-started/backward-compatibility.md)  
  
  
