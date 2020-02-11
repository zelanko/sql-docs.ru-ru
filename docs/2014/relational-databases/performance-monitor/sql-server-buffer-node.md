---
title: SQL Server:Buffer Node | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQLServer:Buffer Node
- Buffer Node object
ms.assetid: fd3f9f0f-7c38-4cfd-a0c5-ee93dd52d9a5
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 7e99c6e4f28ecef032ff3b793393e5465740156d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "63250743"
---
# <a name="sql-serverbuffer-node"></a>SQL Server:Buffer Node
  Объект **узел буфера** предоставляет счетчики, которые дополняют счетчики, предоставляемые объектом **диспетчер буферов** . Это позволяет контролировать распределение страницы буферного пула [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для каждого узла неоднородного доступа к памяти (NUMA). Для каждого используемого узла неоднородного доступа к памяти (NUMA) существует экземпляр объекта **узел буфера** . В архитектуре, отличной от NUMA, существует единственный экземпляр объекта **узел буфера** .  
  
## <a name="buffer-node-performance-objects"></a>Объекты производительности узла буфера  
 Объекты производительности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **узла буфера** описаны в следующей таблице.  
  
|Счетчики узла буфера SQL Server|Description|  
|-------------------------------------|-----------------|  
|**Страницы базы данных**|Указывает число страниц с содержимым базы данных в буферном пуле этого узла.|  
|**Ожидаемый срок жизни страницы**|Указывает минимальное количество секунд, в течение которых страница остается в буферном пуле этого узла без ссылок на нее.|  
|**Поисков страниц на локальном узле/с**|Указывает число запросов поиска с этого узла, которые были удовлетворены с этого узла.|  
|**Поисков страниц удаленной заметки/с**|Указывает число запросов поиска с этого узла, которые были удовлетворены с других узлов.|  
  
 Если SQL Server выполняется на оборудовании, отличном от NUMA, то счетчики объектов **узел буфера** и **диспетчер буферов** должны иметь одинаковые значения.  
  
 На оборудовании NUMA суммы соответствующих счетчиков всех **узлов буфера** должны соответствовать своим дополнениям **диспетчера буферов**.  
  
> [!NOTE]  
>  Значения и суммы счетчиков могут точно не совпадать по причине динамической природы счетчиков и точности отбора значений.  
  
## <a name="see-also"></a>См. также:  
 [SQL Server, объект диспетчера буферов](sql-server-buffer-manager-object.md)   
 [Параметры конфигурации сервера «Server Memory»](../../database-engine/configure-windows/server-memory-server-configuration-options.md)   
 [Мониторинг использования ресурсов &#40;системном мониторе&#41;](monitor-resource-usage-system-monitor.md)   
 [sys. dm_os_performance_counters &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql)  
  
  
