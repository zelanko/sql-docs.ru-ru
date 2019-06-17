---
title: Свойства сеанса | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- sessions [OLE DB]
- SQL Server Native Client OLE DB provider, sessions
ms.assetid: 2498fbad-b3db-4bea-8fc6-fef5317d3eba
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 19ce2c6ca7b36a5d2147e7efda657fb2433aef25
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63062544"
---
# <a name="session-properties"></a>Свойства сеанса
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента интерпретирует свойства сеанса OLE DB следующим образом.  
  
|Идентификатор свойства|Описание|  
|-----------------|-----------------|  
|DBPROP_SESS_AUTOCOMMITISOLEVELS|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщик OLE DB для собственного клиента поддерживает все уровни изоляции автофиксации транзакций за исключением уровня хаоса, DBPROPVAL_TI_CHAOS.|  
  
 В от поставщика наборе свойств DBPROPSET_SQLSERVERSESSION [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB для собственного клиента определяет следующее дополнительное свойство.  
  
|Идентификатор свойства|Описание|  
|-----------------|-----------------|  
|SSPROP_QUOTEDCATALOGNAMES|Тип: VT_BOOL<br /><br /> И ЗАПИСЬ: чтение и запись<br /><br /> По умолчанию: VARIANT_FALSE<br /><br /> Описание. Заключенные в кавычки идентификаторы, разрешенных в ограничением CATALOG.<br /><br /> VARIANT_TRUE: Заключенные в кавычки идентификаторы распознаются ограничением каталога для наборов строк схемы, предоставляющих поддержку распределенным запросам.<br /><br /> VARIANT_FALSE: Заключенные в кавычки идентификаторы не распознаются ограничением каталога для наборов строк схемы, предоставляющих поддержку распределенным запросам.<br /><br /> Дополнительные сведения о наборах строк схемы, обеспечивающих поддержку распределенных запросов, см. в статье [Поддержка распределенных запросов в наборах строк схемы](../native-client/ole-db/schema-rowsets-distributed-query-support.md).|  
|Свойство SSPROP_ALLOWNATIVEVARIANT|Тип: VT_BOOL<br /><br /> И ЗАПИСЬ: Чтение и запись<br /><br /> По умолчанию: VARIANT_FALSE<br /><br /> Описание. Определяет, является ли данные, полученные в качестве DBTYPE_VARIANT или DBTYPE_SQLVARIANT.<br /><br /> VARIANT_TRUE: Возвращается тип столбца dbtype_sqlvariant в котором случае буфера будет сохраняется структура SSVARIANT.<br /><br /> VARIANT_FALSE: Тип столбца возвращается DBTYPE_VARIANT и буфера будет иметь структура VARIANT.|  
|SSPROP_ASYNCH_BULKCOPY|Для использования асинхронного режима задайте значение VARIANT_TRUE характерного для поставщика свойства SSPROP_ASYNCH_BULKCOPY сеанса до вызова метода BCPExec. Это свойство доступно в наборе свойств DBPROPSET_SQLSERVERSESSION.|  
  
## <a name="see-also"></a>См. также  
 [Объекты источника данных &#40;OLE DB&#41;](data-source-objects-ole-db.md)  
  
  
