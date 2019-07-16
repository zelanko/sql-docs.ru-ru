---
title: Выполнение хранимых процедур (OLE DB) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- stored procedures [OLE DB], executing
- OLE DB, stored procedures
- SQL Server Native Client OLE DB provider, stored procedures
ms.assetid: c77d9be9-2176-4438-8c7a-04b63ebece08
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: b139200b9c4e574fe79ab4a0306368a88b191d4e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68031846"
---
# <a name="stored-procedures---running"></a>Выполнение хранимых процедур
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  При выполнении инструкций вызов хранимой процедуры в источнике данных (вместо выполнения или подготовки инструкции непосредственно в клиентском приложении) может обеспечить следующее:  
  
-   высокую производительность;  
  
-   низкие издержки сети;  
  
-   лучшую согласованность;  
  
-   большую точность;  
  
-   дополнительные возможности.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента поддерживает три следующих механизмов, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] использовать хранимые процедуры для возврата данных:  
  
-   Каждая инструкция SELECT в хранимой процедуре формирует результирующий набор.  
  
-   Процедура может возвращать данные через выходные параметры.  
  
-   Процедура может иметь целочисленный код возврата.  
  
 Приложение должно быть способно обработать все эти данные, возвращаемые хранимыми процедурами.  
  
 Разные поставщики OLE DB возвращают выходные параметры и значения на разных этапах во время обработки результатов. В частности [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента, выходные параметры и коды возврата не предоставляются до после потребитель получит или отменено результирующие наборы, возвращаемые хранимой процедурой. Коды возврата и выходные параметры возвращаются сервером в последнем пакете потока табличных данных.  
  
 Поставщики используют свойство DBPROP_OUTPUTPARAMETERAVAILABILITY для сообщения о возвращении выходных параметров и возвращаемых значений. Это свойство доступно в наборе свойств DBPROPSET_DATASOURCEINFO.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента присваивает свойству DBPROP_OUTPUTPARAMETERAVAILABILITY значение dbpropval_oa_atrowrelease, указывая, что коды возврата и выходные параметры не возвращаются до результирующий набор будет обработан или освобожден.  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры](../../../relational-databases/native-client/ole-db/stored-procedures.md)  
  
  
