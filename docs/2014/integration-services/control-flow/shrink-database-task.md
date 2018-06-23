---
title: Задача "Сжатие базы данных" | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.shrinkdatabasetask.f1
helpviewer_keywords:
- Shrink Database task
- database shrinking [Integration Services]
- shrinking databases
ms.assetid: e66286f8-97b1-4e5a-86b4-e56f1932b7d5
caps.latest.revision: 41
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 8da3472bf3772654def991ede932f92a20283808
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36086712"
---
# <a name="shrink-database-task"></a>задача «Сжатие базы данных»
  Задача «Сжатие базы данных» уменьшает размер данных базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и файлов журналов.  
  
 Используя задачу «Сжатие базы данных», пакет может сжимать файлы как одной базы данных, так и множества баз данных.  
  
 Сжатие файлов данных позволяет освободить неиспользуемое пространство путем перемещения страниц данных с конца файла в незанятое пространство ближе к началу файла. Когда в конце файла образуется достаточно свободного места, страницы данных в конце файла могут быть освобождены и возвращены в файловую систему.  
  
> [!WARNING]  
>  Данные, перемещаемые в процессе сжатия файла, могут быть разбросаны по любым доступным местам в файле. Это вызывает фрагментацию индекса и может увеличить время выполнения запросов, выполняющих поиск в диапазоне индекса. Чтобы устранить фрагментацию, предусмотрите возможность перестроения индексов файла после сжатия.  
  
## <a name="commands"></a>Команды  
 Задача «Сжатие базы данных» содержит команду DBCC SHRINKDATABASE, включая следующие аргументы и параметры:  
  
-   *database_name*  
  
-   *target_percent*  
  
-   NOTRUNCATE или TRUNCATEONLY.  
  
 Если задача «Сжатие базы данных» сжимает множество баз данных, то задача запускает множество команд SHRINKDATABASE, по одной на каждую базу данных. Все экземпляры команды SHRINKDATABASE используют одинаковые значения аргументов, за исключением аргумента *database_name*. Дополнительные сведения см. в разделе [DBCC SHRINKDATABASE (Transact-SQL)](/sql/t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql).  
  
## <a name="configuration-of-the-shrink-database-task"></a>Настройка задачи «Сжатие базы данных»  
 Установить свойства можно с помощью конструктора служб [!INCLUDE[ssIS](../../../includes/ssis-md.md)] . Эта задача находится в разделе **Задачи плана обслуживания** **области элементов** в конструкторе служб [!INCLUDE[ssIS](../../../includes/ssis-md.md)] .  
  
 Дополнительные сведения о свойствах, которые можно установить с помощью конструктора служб [!INCLUDE[ssIS](../../../includes/ssis-md.md)] , см. в следующем разделе:  
  
-   [Задача "Сжатие базы данных" (план обслуживания)](../../relational-databases/maintenance-plans/shrink-database-task-maintenance-plan.md)  
  
 Дополнительные сведения об установке этих свойств в конструкторе служб [!INCLUDE[ssIS](../../../includes/ssis-md.md)] см. в следующем разделе:  
  
-   [Задание свойств задач или контейнеров](../set-the-properties-of-a-task-or-container.md)  
  
  
