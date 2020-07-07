---
title: Создание наборов строк при помощи метода ICommand::Execute | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- rowsets [OLE DB], creating
- SQL Server Native Client OLE DB provider, rowsets
- OLE DB rowsets, creating
- Execute method
ms.assetid: 9b530b7d-8165-49d4-a978-5ced17c6705e
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: a251583af46da1b264c33909dcf2a7fe75bc2c3d
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.contentlocale: ru-RU
ms.lasthandoff: 07/06/2020
ms.locfileid: "86005232"
---
# <a name="creating-rowsets-with-icommandexecute"></a>Создание наборов строк при помощи метода ICommand::Execute
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Для наборов строк, созданных с помощью метода **ICommand::Execute**, нужные свойства в результирующем наборе строк могут ограничивать текст команды. Это особенно важно для потребителей, поддерживающих команды с динамическим текстом.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Поставщик OLE DB собственного клиента не может использовать [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] курсоры для поддержки результатов с несколькими наборами строк, созданных многими командами. Если потребитель запрашивает набор строк, требующий поддержки курсора [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], то возникнет ошибка, если текст команды в качестве результата сформирует несколько наборов строк. Дополнительные сведения см. в статье [Команды, формирующие результаты с несколькими наборами строк](../../relational-databases/native-client-ole-db-commands/commands-generating-multiple-rowset-results.md).  
  
 Прокрутки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного клиента OLE DB наборы строк поставщика поддерживаются [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] курсорами. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] накладывает ограничения на чувствительные к изменениям курсоры, созданные другими пользователями базы данных. В частности, строки в некоторых курсорах не могут быть упорядочены, поэтому попытка создать набор строк командой, содержащей предложение SQL ORDER BY, может завершиться ошибкой. Дополнительные сведения см. в статье [Наборы строк и курсоры SQL Server](../../relational-databases/native-client-ole-db-rowsets/rowsets-and-sql-server-cursors.md).  
  
## <a name="see-also"></a>См. также  
 [Наборы строк](../../relational-databases/native-client-ole-db-rowsets/rowsets.md)  
  
  
