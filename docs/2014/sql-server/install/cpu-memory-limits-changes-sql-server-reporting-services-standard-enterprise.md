---
title: Изменения в ограничениях ресурсов ЦП и памяти для SQL Server Reporting Services Standard и Enterprise | Документация Майкрософт
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66095954"
---
# <a name="changes-to-cpu-and-memory-limits-for-sql-server-reporting-services-standard-and-enterprise"></a>Изменения ограничений ЦП и памяти для выпусков служб SQL Server Reporting Services Standard Edition и Enterprise Edition
  Начиная с версии [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], выпуски служб Reporting Services Standard и Enterprise поддерживают до 64 ГБ системной памяти.  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
### <a name="description"></a>Description  
 Начиная с версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], выпуски служб Reporting Services Standard и Enterprise поддерживают до 64 ГБ системной памяти. Может потребоваться повторно настроить параметры системы, чтобы поддерживать обновленные ограничения.  
  
 Дополнительные сведения об ограничениях ЦП и памяти для других выпусков [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]см. в разделе [ограничения вычислительной мощности по выпуску SQL Server](../compute-capacity-limits-by-edition-of-sql-server.md)и память, [поддерживаемая выпусками SQL Server](https://go.microsoft.com/fwlink/?LinkId=212633).  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Может потребоваться повторно настроить параметры системы, чтобы поддерживать обновленные ограничения. Дополнительные сведения см. в статье [Параметры конфигурации сервера](../../database-engine/configure-windows/server-memory-server-configuration-options.md) [ALTER Server Configuration &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-server-configuration-transact-sql)и Server Memory.  
  
## <a name="see-also"></a>См. также:  
 [Функции, поддерживаемые различными выпусками SQL Server 2014](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)   
 [Обратная совместимость](../../../2014/getting-started/backward-compatibility.md)  
  
  
