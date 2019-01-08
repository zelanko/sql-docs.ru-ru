---
title: Изменения ограничений ЦП и памяти для SQL Server Reporting Services Standard и Enterprise | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: dd553715-2b95-4119-8f58-d01de388d9ab
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: efc71378e6570a86d075ed50e206284a93b0532a
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/13/2018
ms.locfileid: "53353872"
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
  
  
