---
title: Команды, создающие результаты из нескольких наборов строк (поставщик собственного клиента OLE DB) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- multiple rowsets
- rowsets [OLE DB], multiple
- SQL Server Native Client OLE DB provider, commands
- SQL Server Native Client OLE DB provider, multiple rowsets
- commands [OLE DB]
- multiple-rowset results
ms.assetid: 4567668d-35fd-4162-b61f-f7536862cdcb
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: a8f689ecd7d6c66880f217a8ea262acc113591af
ms.sourcegitcommit: 591bbf4c7e4e2092f8abda6a2ffed263cb61c585
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/22/2020
ms.locfileid: "86942887"
---
# <a name="commands-generating-multiple-rowset-results"></a>Команды, формирующие результаты с несколькими наборами строк
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Поставщик OLE DB собственного клиента может возвращать несколько наборов строк из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] инструкций. Инструкции [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращают результаты, содержащие несколько наборов строк, в следующих случаях.  
  
-   Пакетные инструкции SQL представляются как единая команда.  
  
-   Хранимые процедуры реализуют пакет инструкций SQL.  
  
## <a name="batches"></a>Пакеты  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Поставщик OLE DB собственного клиента распознает символ точки с запятой как разделитель пакетной службы для инструкций SQL:  
  
```  
WCHAR*       wSQLString = L"SELECT * FROM Categories; "  
                          L"SELECT * FROM Products";  
```  
  
 Отправка нескольких инструкций SQL в одном пакете более эффективна, чем выполнение каждой инструкции SQL по отдельности. Отправка одного пакета уменьшает количество циклов приема-передачи данных с клиента на сервер.  
  
## <a name="stored-procedures"></a>Хранимые процедуры  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращает результирующий набор для каждой инструкции в хранимой процедуре, поэтому большинство хранимых процедур [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращает несколько результирующих наборов.  
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Обработка нескольких результирующих наборов при помощи интерфейса IMultipleResults](../../relational-databases/native-client-ole-db-commands/using-imultipleresults-to-process-multiple-result-sets.md)  
  
## <a name="see-also"></a>См. также  
 [Команды](../../relational-databases/native-client-ole-db-commands/commands.md)  
  
  
