---
title: ICommandWithParameters (поставщик собственного клиента OLE DB) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 66644c70-def7-46d8-8c47-b883292a0288
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: cf7393a1b89678fc6f8544c1662ba23272978093
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/28/2020
ms.locfileid: "87243965"
---
# <a name="icommandwithparameters-native-client-ole-db-provider"></a>ICommandWithParameters (поставщик собственного клиента OLE DB)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Улучшения ядра СУБД, появившиеся с версии [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], позволяют методу ICommandWithParameters::GetParameterInfo получать более точные описания ожидаемых результатов. Эти более точные результаты могут отличаться от значений, которые метод CommandWithParameters::GetParameterInfo возвращает в предыдущих версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в разделе [Обнаружение метаданных](../../relational-databases/native-client/features/metadata-discovery.md).  
  
 Кроме того, начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] при вызове интерфейса ICommandWithParameters::SetParameterInfo значение, передаваемое параметру *pwszName*, должно быть допустимым идентификатором. Дополнительные сведения см. в разделе [Идентификаторы баз данных](../../relational-databases/databases/database-identifiers.md).  
  
## <a name="see-also"></a>См. также:  
 [Интерфейсы (OLE DB)](https://msdn.microsoft.com/library/34c33364-8538-45db-ae41-5654481cda93)  
  
  
