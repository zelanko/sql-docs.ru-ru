---
title: ICommand (OLE DB) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ICommand [SQL Server Native Client]
ms.assetid: 5e24b3a0-0658-44fc-b653-f4c52f9eb328
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: e04f91926d9855031626a1ecb7097b30c68e8d58
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85785430"
---
# <a name="icommand-ole-db"></a>ICommand (OLE DB)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asdw-pdw.md)]

  В этом разделе обсуждаются особенности OLE DB, касающиеся собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="icommandexecute"></a>ICommand::Execute  
 Вставка данных, превышающих размер столбца, как правило, приводит к ошибке. Однако в некоторых ситуациях происходит возврат значения S_OK, хотя параметру *dwStatus* присваивается значение DBSTATUS_S_TRUNCATED. Обычно такая ситуация возникает при вставке данных с параметрами, когда размера столбца не хватает для размещения данных и не был вызван метод **ICommandWithParameters::SetParameterInfo** .  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы (OLE DB)](https://msdn.microsoft.com/library/34c33364-8538-45db-ae41-5654481cda93)  
  
  
