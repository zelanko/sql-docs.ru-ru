---
title: Команды, формирующие результаты, содержащие | Документы Microsoft
description: Команды, формирующие результаты, содержащие
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-commands
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- multiple rowsets
- rowsets [OLE DB], multiple
- OLE DB Driver for SQL Server, commands
- OLE DB Driver for SQL Server, multiple rowsets
- commands [OLE DB]
- multiple-rowset results
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 86d7f36e64ddb051af8c1746c8472a41483b0ecc
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="commands-generating-multiple-rowset-results"></a>Команды, формирующие результаты с несколькими наборами строк
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Драйвер OLE DB для SQL Server может возвращать несколько наборов строк из [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] инструкции. Инструкции [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] возвращают результаты, содержащие несколько наборов строк, в следующих случаях.  
  
-   Пакетные инструкции SQL представляются как единая команда.  
  
-   Хранимые процедуры реализуют пакет инструкций SQL.  
  
## <a name="batches"></a>Пакеты  
 Драйвер OLE DB для SQL Server распознает символ точки с запятой в качестве разделителя пакета инструкций SQL:  
  
```  
WCHAR*       wSQLString = L"SELECT * FROM Categories; "  
                          L"SELECT * FROM Products";  
```  
  
 Отправка нескольких инструкций SQL в одном пакете более эффективна, чем выполнение каждой инструкции SQL по отдельности. Отправка одного пакета уменьшает количество циклов приема-передачи данных с клиента на сервер.  
  
## <a name="stored-procedures"></a>Хранимые процедуры  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] возвращает результирующий набор для каждой инструкции в хранимой процедуре, поэтому большинство хранимых процедур [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] возвращает несколько результирующих наборов.  
  
## <a name="in-this-section"></a>В этом разделе  
  
-   [Обработка нескольких результирующих наборов при помощи интерфейса IMultipleResults](../../oledb/ole-db-commands/using-imultipleresults-to-process-multiple-result-sets.md)  
  
## <a name="see-also"></a>См. также:  
 [Команды](../../oledb/ole-db-commands/commands.md)  
  
  
