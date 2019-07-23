---
title: 'Создание наборов строк с помощью метода ICommand:: Execute | Документация Майкрософт'
description: Создание наборов строк с помощью метода ICommand::Execute
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- rowsets [OLE DB], creating
- OLE DB Driver for SQL Server, rowsets
- OLE DB rowsets, creating
- Execute method
author: pmasl
ms.author: pelopes
ms.openlocfilehash: f89db69fba4e4a661d4128122181dae9fb9d3ece
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67994318"
---
# <a name="creating-rowsets-with-icommandexecute"></a>Создание наборов строк при помощи метода ICommand::Execute
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Для наборов строк, созданных с помощью метода **ICommand::Execute**, нужные свойства в результирующем наборе строк могут ограничивать текст команды. Это особенно важно для потребителей, поддерживающих команды с динамическим текстом.  
  
 Драйвер OLE DB для SQL Server не может использовать курсоры [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] для поддержки нескольких результирующих наборов строк, сформированных несколькими командами. Если потребитель запрашивает набор строк, требующий поддержки курсора [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], то возникнет ошибка, если текст команды в качестве результата сформирует несколько наборов строк. Дополнительные сведения см. в разделе [команды, создающие результаты с несколькими наборами строк](../../oledb/ole-db-commands/commands-generating-multiple-rowset-results.md).  
  
 Прокручиваемый Драйвер OLE DB для наборов строк SQL Server поддерживаются [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] курсорами. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] накладывает ограничения на чувствительные к изменениям курсоры, созданные другими пользователями базы данных. В частности, строки в некоторых курсорах не могут быть упорядочены, поэтому попытка создать набор строк командой, содержащей предложение SQL ORDER BY, может завершиться ошибкой. Дополнительные сведения см. в статье [Наборы строк и курсоры SQL Server](../../oledb/ole-db-rowsets/rowsets-and-sql-server-cursors.md).  
  
## <a name="see-also"></a>См. также:  
 [Наборы строк](../../oledb/ole-db-rowsets/rowsets.md)  
  
  
