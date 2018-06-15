---
title: Свойства сеанса - драйвер OLE DB для SQL Server | Документы Microsoft
description: Свойства сеанса - драйвер OLE DB для SQL Server
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-data-source-objects
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- sessions [OLE DB]
- OLE DB Driver for SQL Server, sessions
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: a0d7e97017a8d188eaf9fb9cc24b0b2fbc0e80b2
ms.sourcegitcommit: e1bc8c486680e6d6929c0f5885d97d013a537149
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2018
ms.locfileid: "35666434"
---
# <a name="session-properties---ole-db-driver-for-sql-server"></a>Свойства сеанса - драйвер OLE DB для SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Драйвер OLE DB для SQL Server интерпретирует свойства сеанса OLE DB следующим образом.  
  
|Идентификатор свойства|Описание|  
|-----------------|-----------------|  
|DBPROP_SESS_AUTOCOMMITISOLEVELS|Драйвер OLE DB для SQL Server поддерживает все уровни изоляции транзакций автоматической фиксации за исключением уровня хаоса, DBPROPVAL_TI_CHAOS.|  
  
 В наборе данных от поставщика свойств DBPROPSET_SQLSERVERSESSION драйвер OLE DB для SQL Server определяет следующее дополнительное свойство.  
  
|Идентификатор свойства|Описание|  
|-----------------|-----------------|  
|SSPROP_QUOTEDCATALOGNAMES|Тип: VT_BOOL<br /><br /> R Чтение и запись: чтение и запись<br /><br /> По умолчанию: значение VARIANT_FALSE<br /><br /> Описание: Заключенные в кавычки идентификаторы допускаются в ограничение КАТАЛОГА.<br /><br /> VARIANT_TRUE: Заключенные в кавычки идентификаторы распознаются ограничением каталога для наборов строк схемы, предоставляющих поддержку распределенным запросам.<br /><br /> VARIANT_FALSE: Заключенные в кавычки идентификаторы не распознаются ограничением каталога для наборов строк схемы, предоставляющих поддержку распределенным запросам.<br /><br /> Дополнительные сведения о наборах строк схемы, предоставляющих поддержку распределенным запросам см. в разделе [поддержка распределенных запросов в наборах строк схемы](../../oledb/ole-db/schema-rowsets-distributed-query-support.md).|  
|Свойство SSPROP_ALLOWNATIVEVARIANT|Тип: VT_BOOL<br /><br /> R Чтение и запись: чтение и запись<br /><br /> По умолчанию: значение VARIANT_FALSE<br /><br /> Описание: Определяет, является ли данные, полученные в качестве DBTYPE_VARIANT или DBTYPE_SQLVARIANT.<br /><br /> VARIANT_TRUE: Dbtype_sqlvariant в котором случае в буфере сохраняется структура SSVARIANT возвращается тип столбца.<br /><br /> VARIANT_FALSE: Тип столбца возвращается DBTYPE_VARIANT и буфер будет иметь структура VARIANT.|  
|SSPROP_ASYNCH_BULKCOPY|Для использования асинхронного режима задайте значение VARIANT_TRUE характерного для поставщика свойства SSPROP_ASYNCH_BULKCOPY сеанса до вызова метода BCPExec. Это свойство доступно в наборе свойств DBPROPSET_SQLSERVERSESSION.|  
  
## <a name="see-also"></a>См. также  
 [Объекты источников данных &#40;OLE DB&#41;](../../oledb/ole-db-data-source-objects/data-source-objects-ole-db.md)  
  
  
