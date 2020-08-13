---
title: ICommandWithParameters (драйвер OLE DB) | Документация Майкрософт
description: Интерфейс ICommandWithParameters interface
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
author: pmasl
ms.author: pelopes
ms.openlocfilehash: afb49ad0dd1d1bf6275fb093b42c97e34cb7d670
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/28/2020
ms.locfileid: "87244495"
---
# <a name="icommandwithparameters"></a>ICommandWithParameters
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Улучшения ядра СУБД, появившиеся с версии [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], позволяют методу ICommandWithParameters::GetParameterInfo получать более точные описания ожидаемых результатов. Эти более точные результаты могут отличаться от значений, которые метод CommandWithParameters::GetParameterInfo возвращает в предыдущих версиях [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в разделе [Обнаружение метаданных](../../oledb/features/metadata-discovery.md).  
  
 Кроме того, начиная с [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] при вызове интерфейса ICommandWithParameters::SetParameterInfo значение, передаваемое параметру *pwszName*, должно быть допустимым идентификатором. Дополнительные сведения см. в разделе [Идентификаторы баз данных](../../../relational-databases/databases/database-identifiers.md).  
  
## <a name="see-also"></a>См. также:  
 [Интерфейсы (OLE DB)](../../oledb/ole-db-interfaces/oledb-driver-for-sql-server-ole-db-interfaces.md) 
  
  
