---
title: Задача "Реорганизация индекса" | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.reorganizeindextask.f1
helpviewer_keywords:
- reorganizing indexes
- Reorganize Index task [Integration Services]
- indexes [Integration Services]
ms.assetid: 9ed87861-e5c3-4fcd-8760-d112f4c0af0c
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 4869120627fd867fa3bd0573381477fc31a97f5a
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "62830575"
---
# <a name="reorganize-index-task"></a>Задача «Реорганизация индекса»
  Задача «Реорганизация индекса» перестраивает индексы в таблицах и представлениях базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Дополнительные сведения об управлении индексами см. в разделе [Реорганизация и перестроение индексов](../../relational-databases/indexes/reorganize-and-rebuild-indexes.md).  
  
 Используя задачу «Реорганизация индекса», пакет может перестроить индексы в одной или нескольких базах данных. Если задача перестраивает индексы только одной базы данных, можно выбрать представления или таблицы, чьи индексы будут реорганизованы. Задача «Реорганизация индекса» также содержит параметр сжатия больших объектов данных. Большой объект данных — это данные, содержащие значение типа данных `image`, `text`, `ntext`, `varchar(max)`, `nvarchar(max)`, `varbinary(max)` или `xml`. Дополнительные сведения см. в разделе [Типы данных (Transact-SQL)](/sql/t-sql/data-types/data-types-transact-sql).  
  
 Задача «Реорганизация индекса» содержит инструкцию Transact-SQL ALTER INDEX. Если необходимо сжать большой объект данных, инструкция использует предложение REORGANIZE WITH (LOB_COMPACTION = ON), иначе значение LOB_COMPACTION устанавливается в OFF. Дополнительные сведения см. в разделе [ALTER INDEX (Transact-SQL)](/sql/t-sql/statements/alter-index-transact-sql).  
  
> [!IMPORTANT]  
>  Время, необходимое на создание инструкции Transact-SQL, которая будет выполнена задачей, пропорционально количеству индексов, которые необходимо перестроить. Если задача настроена на перестроение всех таблиц и представлений базы данных, которая содержит большое количество индексов, или нужно перестроить индексы нескольких баз данных, то создание инструкции Transact-SQL может занять значительное время.  
  
## <a name="configuration-of-the-reorganize-index-task"></a>Настройка задачи «Реорганизация индекса»  
 Свойства задаются с помощью конструктора служб [!INCLUDE[ssIS](../../../includes/ssis-md.md)] . Эта задача находится в разделе **Задачи плана обслуживания** **области элементов** в конструкторе служб [!INCLUDE[ssIS](../../../includes/ssis-md.md)] .  
  
 Дополнительные сведения о свойствах, которые можно задать в конструкторе служб [!INCLUDE[ssIS](../../../includes/ssis-md.md)] , см. в следующих разделах:  
  
-   [Задача "Реорганизация индекса" (план обслуживания)](../../relational-databases/maintenance-plans/reorganize-index-task-maintenance-plan.md)  
  
## <a name="related-tasks"></a>Связанные задачи  
 Дополнительные сведения о настройке свойств этих свойств в конструкторе [!INCLUDE[ssIS](../../../includes/ssis-md.md)] см. в разделе [Задание свойств задач или контейнеров](../set-the-properties-of-a-task-or-container.md).  
  
## <a name="see-also"></a>См. также:  
 [Задачи служб Integration Services](integration-services-tasks.md)   
 [Поток управления](control-flow.md)  
  
  
