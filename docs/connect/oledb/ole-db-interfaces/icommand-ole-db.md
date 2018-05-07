---
title: ICommand (OLE DB) | Документы Microsoft
description: Интерфейс ICommand (OLE DB)
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: ole-db-interfaces
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ICommand [OLE DB Driver for SQL Server]
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 4ecb3b505d7da116711bb09f7a35def4e008faf3
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="icommand-ole-db"></a>ICommand (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  В этой статье обсуждаются особенности OLE DB, которая относится к драйвер OLE DB для SQL Server.  
  
## <a name="icommandexecute"></a>ICommand::Execute  
 Вставка данных, превышающих размер столбца, как правило, приводит к ошибке. Однако в некоторых ситуациях происходит возврат значения S_OK, хотя параметру *dwStatus* присваивается значение DBSTATUS_S_TRUNCATED. Она обычно возникает при вставке данных с параметрами, где столбец недостаточен для хранения данных, и **ICommandWithParameters::SetParameterInfo** еще не был вызван.  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы & #40; OLE DB & #41;](../../oledb/ole-db-interfaces/oledb-driver-for-sql-server-ole-db-interfaces.md)
  
  
