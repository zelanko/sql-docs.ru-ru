---
title: Команды, создающие результаты с несколькими наборами строк | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 19a6dafd921edf924a35e30c7770155986203f5f
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2019
ms.locfileid: "73758278"
---
# <a name="commands-generating-multiple-rowset-results"></a>Команды, формирующие результаты с несколькими наборами строк
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB может возвращать несколько наборов строк из инструкций [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Инструкции [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращают результаты, содержащие несколько наборов строк, в следующих случаях.  
  
-   Пакетные инструкции SQL представляются как единая команда.  
  
-   Хранимые процедуры реализуют пакет инструкций SQL.  
  
## <a name="batches"></a>Пакеты  
 Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB распознает символ точки с запятой как разделитель пакетной службы для инструкций SQL:  
  
```  
WCHAR*       wSQLString = L"SELECT * FROM Categories; "  
                          L"SELECT * FROM Products";  
```  
  
 Отправка нескольких инструкций SQL в одном пакете более эффективна, чем выполнение каждой инструкции SQL по отдельности. Отправка одного пакета уменьшает количество циклов приема-передачи данных с клиента на сервер.  
  
## <a name="stored-procedures"></a>Хранимые процедуры  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращает результирующий набор для каждой инструкции в хранимой процедуре, поэтому большинство хранимых процедур [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращает несколько результирующих наборов.  
  
## <a name="in-this-section"></a>В этом разделе  
  
-   [Обработка нескольких результирующих наборов с помощью интерфейса IMultipleResults](../../relational-databases/native-client-ole-db-commands/using-imultipleresults-to-process-multiple-result-sets.md)  
  
## <a name="see-also"></a>См. также раздел  
 [Команды](../../relational-databases/native-client-ole-db-commands/commands.md)  
  
  
