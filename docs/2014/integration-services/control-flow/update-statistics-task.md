---
title: Задача "Обновление статистики" | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.updatestatisticstask.f1
helpviewer_keywords:
- updating statistics
- Update Statistics task [Integration Services]
ms.assetid: 0247483b-f092-4511-8fa8-3610108bd1bc
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1507ada1e4fa087901383930fce4996c191fb553
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/26/2020
ms.locfileid: "85438071"
---
# <a name="update-statistics-task"></a>Задача «Обновление статистики»
  Задача «Обновление статистики» обновляет данные о распределении ключевых значений одной или более статистических групп (коллекций) в определенной таблице или индексированном представлении. Дополнительные сведения см. в статье [Managing statistics on tables in SQL Data Warehouse](../../relational-databases/statistics/statistics.md) (Управление статистикой таблиц в хранилище данных SQL).  
  
 При помощи задачи «Обновление статистики» пакет может обновлять статистику в одной или нескольких базах данных. Если задача обновляет статистику только одной базы данных, можно выбрать представления и таблицы, статистику которых данная задача обновляет. Можно определить, необходимо ли обновлять всю статистику, только статистику столбцов, или только статистику индекса.  
  
 Эта задача содержит инструкцию UPDATE STATISTICS, включающую следующие аргументы и предложения:  
  
-   Аргумент *table_name* или *view_name* .  
  
-   Если необходимо обновление всех статистик, нужно применить предложение WITH ALL.  
  
-   Если необходимо обновление только столбцов, применяется предложение WITH COLUMN.  
  
-   Если необходимо обновление только индексов, применяется предложение WITH INDEX.  
  
 Если задача «Обновление статистики» обновляет статистику в нескольких базах данных, она запускает несколько инструкций UPDATE STATISTICS, каждую для отдельной таблицы или представления. Все экземпляры инструкции UPDATE STATISTICS используют одно и то же предложение, но различные значения аргументов *table_name* или *view_name* . Дополнительные сведения см. в разделах [CREATE STATISTICS (Transact-SQL)](/sql/t-sql/statements/create-statistics-transact-sql) и [UPDATE STATISTICS (Transact-SQL)](/sql/t-sql/statements/update-statistics-transact-sql).  
  
> [!IMPORTANT]  
>  Время, которое необходимо задаче для создания инструкции Transact-SQL, пропорционально числу статистик, которые обновляет задача. Если задача настроена на обновление статистики во всех таблицах и представлениях базы данных с большим числом индексов или на обновление статистики в нескольких базах данных, ей может потребоваться существенное количество времени для формирования инструкции Transact-SQL.  
  
## <a name="configuration-of-the-update-statistics-task"></a>Настройка задачи «Обновление статистики»  
 Свойства задаются с помощью конструктора служб [!INCLUDE[ssIS](../../../includes/ssis-md.md)] . Эта задача находится в разделе **Задачи плана обслуживания** **области элементов** в конструкторе служб [!INCLUDE[ssIS](../../../includes/ssis-md.md)] .  
  
 Дополнительные сведения о свойствах, которые можно задать в конструкторе служб [!INCLUDE[ssIS](../../../includes/ssis-md.md)] , см. в следующих разделах:  
  
-   [Задача "Обновление статистики" (план обслуживания)](../../relational-databases/maintenance-plans/update-statistics-task-maintenance-plan.md)  
  
## <a name="related-tasks"></a>Связанные задачи  
 Дополнительные сведения об установке этих свойств в конструкторе служб [!INCLUDE[ssIS](../../../includes/ssis-md.md)] см. в следующем разделе:  
  
-   [Задание свойств задач или контейнеров](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="see-also"></a>См. также:  
 [Задачи служб Integration Services](integration-services-tasks.md)   
 [Поток управления](control-flow.md)  
  
  
