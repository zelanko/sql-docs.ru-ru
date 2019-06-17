---
title: Изменения ограничений ЦП и памяти для SQL Server Reporting Services Standard и Enterprise | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: dd553715-2b95-4119-8f58-d01de388d9ab
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 4d8e18215c6078026b617e079879da1eadbca612
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66095954"
---
# <a name="changes-to-cpu-and-memory-limits-for-sql-server-reporting-services-standard-and-enterprise"></a>Изменения ограничений ЦП и памяти для выпусков служб SQL Server Reporting Services Standard Edition и Enterprise Edition
  Начиная с версии [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], выпуски служб Reporting Services Standard и Enterprise поддерживают до 64 ГБ системной памяти.  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
### <a name="description"></a>Описание  
 Начиная с версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], выпуски служб Reporting Services Standard и Enterprise поддерживают до 64 ГБ системной памяти. Может потребоваться повторно настроить параметры системы, чтобы поддерживать обновленные ограничения.  
  
 Дополнительные сведения об ограничениях ЦП и памяти для других выпусков [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], см. в разделе [Compute Capacity Limits by Edition of SQL Server](../compute-capacity-limits-by-edition-of-sql-server.md), и [объем памяти, поддерживаемый разными выпусками SQL Server](https://go.microsoft.com/fwlink/?LinkId=212633).  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Может потребоваться повторно настроить параметры системы, чтобы поддерживать обновленные ограничения. Дополнительные сведения см. в разделе [ALTER SERVER CONFIGURATION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-server-configuration-transact-sql), и [параметры конфигурации сервера Server Memory](../../database-engine/configure-windows/server-memory-server-configuration-options.md).  
  
## <a name="see-also"></a>См. также  
 [Функции, поддерживаемые различными выпусками SQL Server 2014](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)   
 [Обратная совместимость](../../../2014/getting-started/backward-compatibility.md)  
  
  
