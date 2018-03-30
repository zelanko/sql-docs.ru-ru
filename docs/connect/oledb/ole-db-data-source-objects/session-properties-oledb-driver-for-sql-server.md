---
title: Свойства сеанса - драйвер OLE DB для SQL Server | Документы Microsoft
description: Свойства сеанса - драйвер OLE DB для SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-data-source-objects
ms.reviewer: ''
ms.suite: sql
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- sessions [OLE DB]
- OLE DB Driver for SQL Server, sessions
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ffe6f6a0c2a8c7100bb458b2e939b7e50f3a888a
ms.sourcegitcommit: 9f4330a4b067deea396b8567747a6771f35e6eee
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2018
---
# <a name="session-properties---ole-db-driver-for-sql-server"></a>Свойства сеанса - драйвер OLE DB для SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Драйвер OLE DB для SQL Server интерпретирует свойства сеанса OLE DB следующим образом.  
  
|Идентификатор свойства|Description|  
|-----------------|-----------------|  
|DBPROP_SESS_AUTOCOMMITISOLEVELS|Драйвер OLE DB для SQL Server поддерживает все уровни изоляции транзакций автоматической фиксации за исключением уровня хаоса, DBPROPVAL_TI_CHAOS.|  
  
 В наборе данных от поставщика свойств DBPROPSET_SQLSERVERSESSION драйвер OLE DB для SQL Server определяет следующее дополнительное свойство.  
  
|Идентификатор свойства|Description|  
|-----------------|-----------------|  
|SSPROP_QUOTEDCATALOGNAMES|Тип: VT_BOOL<br /><br /> R Чтение и запись: чтение и запись<br /><br /> По умолчанию: значение VARIANT_FALSE<br /><br /> Описание: Заключенные в кавычки идентификаторы допускаются в ограничение КАТАЛОГА.<br /><br /> VARIANT_TRUE: Заключенные в кавычки идентификаторы распознаются ограничением каталога для наборов строк схемы, предоставляющих поддержку распределенным запросам.<br /><br /> VARIANT_FALSE: Заключенные в кавычки идентификаторы не распознаются ограничением каталога для наборов строк схемы, предоставляющих поддержку распределенным запросам.<br /><br /> Дополнительные сведения о наборах строк схемы, предоставляющих поддержку распределенным запросам см. в разделе [поддержка распределенных запросов в наборах строк схемы](../../oledb/ole-db/schema-rowsets-distributed-query-support.md).|  
|Свойство SSPROP_ALLOWNATIVEVARIANT|Тип: VT_BOOL<br /><br /> R Чтение и запись: чтение и запись<br /><br /> По умолчанию: значение VARIANT_FALSE<br /><br /> Описание: Определяет, является ли данные, полученные в качестве DBTYPE_VARIANT или DBTYPE_SQLVARIANT.<br /><br /> VARIANT_TRUE: Dbtype_sqlvariant в котором случае в буфере сохраняется структура SSVARIANT возвращается тип столбца.<br /><br /> VARIANT_FALSE: Тип столбца возвращается DBTYPE_VARIANT и буфер будет иметь структура VARIANT.|  
|SSPROP_ASYNCH_BULKCOPY|Для использования асинхронного режима задайте значение VARIANT_TRUE характерного для поставщика свойства SSPROP_ASYNCH_BULKCOPY сеанса до вызова метода BCPExec. Это свойство доступно в наборе свойств DBPROPSET_SQLSERVERSESSION.|  
  
## <a name="see-also"></a>См. также:  
 [Объекты источника данных &#40; OLE DB &#41;](../../oledb/ole-db-data-source-objects/data-source-objects-ole-db.md)  
  
  
