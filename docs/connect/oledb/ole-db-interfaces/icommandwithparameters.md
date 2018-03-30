---
title: ICommandWithParameters | Документы Microsoft
description: Интерфейс ICommandWithParameters
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-interfaces
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 9d810ea13512537572bf39fbda938b6b59d64db7
ms.sourcegitcommit: 9f4330a4b067deea396b8567747a6771f35e6eee
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2018
---
# <a name="icommandwithparameters"></a>ICommandWithParameters
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Улучшения в ядро базы данных, начиная с [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] разрешить ICommandWithParameters::GetParameterInfo получать более точные описания ожидаемых результатов. Эти более точные результаты могут отличаться от значения, возвращаемые методом CommandWithParameters::GetParameterInfo в предыдущих версиях [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в разделе [Metadata Discovery](../../oledb/features/metadata-discovery.md).  
  
 Кроме того, начиная с [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], при вызове метода ICommandWithParameters::SetParameterInfo значение, передаваемое *pwszName* параметр должен быть допустимым идентификатором. Дополнительные сведения см. в разделе [Database Identifiers](../../../relational-databases/databases/database-identifiers.md).  
  
## <a name="see-also"></a>См. также:  
 [Интерфейсы &#40; OLE DB &#41;](../../oledb/ole-db-interfaces/oledb-driver-for-sql-server-ole-db-interfaces.md) 
  
  
