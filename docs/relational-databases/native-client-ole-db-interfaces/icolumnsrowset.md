---
description: IColumnsRowset (поставщик собственного клиента OLE DB)
title: IColumnsRowset (поставщик собственного клиента OLE DB) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: e35d37ed-dd9b-4a34-a76a-bc9251f06c4f
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: cd3af620c9958d510b7a4839d9d511064fb0028a
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97460337"
---
# <a name="icolumnsrowset-native-client-ole-db-provider"></a>IColumnsRowset (поставщик собственного клиента OLE DB)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Собственный клиент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] добавляет столбец DBCOLUMN_BASETABLEINSTANCE в набор, возвращаемый методом IColumnsRowset::GetColumnRowset. Этот столбец имеет тип данных DBTYPE_I2 и зарезервирован корпорацией Майкрософт для будущего использования. В будущих версиях данные из этого столбца могут быть изменены.  
  
## <a name="see-also"></a>См. также:  
 [Интерфейсы (OLE DB)](./sql-server-native-client-ole-db-interfaces.md)  
  
