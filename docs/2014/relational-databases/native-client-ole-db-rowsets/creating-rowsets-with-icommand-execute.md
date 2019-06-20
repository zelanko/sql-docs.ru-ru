---
title: Создание наборов строк с помощью метода ICommand::Execute | Документация Майкрософт
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- rowsets [OLE DB], creating
- SQL Server Native Client OLE DB provider, rowsets
- OLE DB rowsets, creating
- Execute method
ms.assetid: 9b530b7d-8165-49d4-a978-5ced17c6705e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3e81f322bde3c4439b26acebb0ad24c925d583a0
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63183679"
---
# <a name="creating-rowsets-with-icommandexecute"></a>Создание наборов строк при помощи метода ICommand::Execute
  Для наборов строк, созданных с помощью метода **ICommand::Execute**, нужные свойства в результирующем наборе строк могут ограничивать текст команды. Это особенно важно для потребителей, поддерживающих команды с динамическим текстом.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Нельзя использовать поставщик OLE DB для собственного клиента [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] курсоры для поддержки результаты несколькими наборами строк, сформированных несколькими командами. Если потребитель запрашивает набор строк, требующий поддержки курсора [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], то возникнет ошибка, если текст команды в качестве результата сформирует несколько наборов строк. Дополнительные сведения см. в разделе [результаты, содержащие генерации команд](../native-client-ole-db-commands/commands-generating-multiple-rowset-results.md).  
  
 Прокручиваемые [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает наборы строк поставщика OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] курсоров. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] накладывает ограничения на чувствительные к изменениям курсоры, созданные другими пользователями базы данных. В частности, строки в некоторых курсорах не могут быть упорядочены, поэтому попытка создать набор строк командой, содержащей предложение SQL ORDER BY, может завершиться ошибкой. Дополнительные сведения см. в статье [Наборы строк и курсоры SQL Server](rowsets-and-sql-server-cursors.md).  
  
## <a name="see-also"></a>См. также  
 [Наборы строк](rowsets.md)  
  
  
