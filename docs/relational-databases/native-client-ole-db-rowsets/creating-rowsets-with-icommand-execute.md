---
title: "Создание наборов строк с ICommand::Execute | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-ole-db-rowsets
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- rowsets [OLE DB], creating
- SQL Server Native Client OLE DB provider, rowsets
- OLE DB rowsets, creating
- Execute method
ms.assetid: 9b530b7d-8165-49d4-a978-5ced17c6705e
caps.latest.revision: "30"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: cbdf11a30bae49d71ccb2699b1bee8e1e6ebf119
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="creating-rowsets-with-icommandexecute"></a>Создание наборов строк при помощи метода ICommand::Execute
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Для наборов строк, созданных с помощью **ICommand::Execute** метода, свойства, которые нужно в результирующем наборе строк могут ограничивать текст команды. Это особенно важно для потребителей, поддерживающих команды с динамическим текстом.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Нельзя использовать поставщик OLE DB для собственного клиента [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] курсоры для поддержки результаты нескольких строк, сформированных несколькими командами. Если потребитель запрашивает набор строк, требующий поддержки курсора [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], то возникнет ошибка, если текст команды в качестве результата сформирует несколько наборов строк. Дополнительные сведения см. в разделе [результаты, содержащие команды создания](../../relational-databases/native-client-ole-db-commands/commands-generating-multiple-rowset-results.md).  
  
 Прокручиваемые [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживаемые наборы строк поставщика OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] курсоров. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] накладывает ограничения на чувствительные к изменениям курсоры, созданные другими пользователями базы данных. В частности, строки в некоторых курсорах не могут быть упорядочены, поэтому попытка создать набор строк командой, содержащей предложение SQL ORDER BY, может завершиться ошибкой. Дополнительные сведения см. в разделе [наборы строк и курсоры SQL Server](../../relational-databases/native-client-ole-db-rowsets/rowsets-and-sql-server-cursors.md).  
  
## <a name="see-also"></a>См. также:  
 [Наборы строк](../../relational-databases/native-client-ole-db-rowsets/rowsets.md)  
  
  
