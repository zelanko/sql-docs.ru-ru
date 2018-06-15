---
title: ICommandWithParameters | Документы Microsoft
description: Интерфейс ICommandWithParameters
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 647c161b2a12ae530edfe610b7d3cbac3b745e50
ms.sourcegitcommit: f16003fd1ca28b5e06d5700e730f681720006816
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35305103"
---
# <a name="icommandwithparameters"></a>ICommandWithParameters
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Улучшения в ядро базы данных, начиная с [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] разрешить ICommandWithParameters::GetParameterInfo получать более точные описания ожидаемых результатов. Эти более точные результаты могут отличаться от значения, возвращаемые методом CommandWithParameters::GetParameterInfo в предыдущих версиях [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в разделе [обнаружение метаданных](../../oledb/features/metadata-discovery.md).  
  
 Кроме того, начиная с [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], при вызове метода ICommandWithParameters::SetParameterInfo значение, передаваемое *pwszName* параметр должен быть допустимым идентификатором. Дополнительные сведения см. в разделе [Идентификаторы баз данных](../../../relational-databases/databases/database-identifiers.md).  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/oledb-driver-for-sql-server-ole-db-interfaces.md) 
  
  
