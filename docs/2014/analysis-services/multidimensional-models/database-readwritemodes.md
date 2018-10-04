---
title: Базы данных режимы ReadWriteModes | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- databases [Analysis Services], read/write
- databases [Analysis Services], read-only
ms.assetid: 03d7cb5c-7ff0-4e15-bcd2-7075d1b0dd69
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: cb52c0d634a93a92d45f10c5bdeb5e2123b30106
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48082694"
---
# <a name="database-readwritemodes"></a>Режимы ReadWriteModes базы данных
  Часто возникает ситуация, когда администратору базы данных (dba) служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] необходимо переключить базу данных из режима для чтения и записи в режим только для чтения или наоборот. Обычно это продиктовано производственной необходимостью, например, чтобы обеспечить общий доступ нескольким серверам к папке базы данных для масштабирования решения и повышения производительности. В подобных случаях `ReadWriteMode` базы данных позволяет свойство [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] администратор базы данных, чтобы легко изменять режим работы базы данных.  
  
## <a name="readwritemode-database-property"></a>Свойство ReadWriteMode базы данных  
 Свойство `ReadWriteMode` базы данных определяет режим базы данных: для чтения и записи или только для чтения. Эти значения являются единственными допустимыми для данного свойства. Пока база данных находится в режиме только для чтения, к ней не могут применяться операции изменения или обновления. В режиме для чтения и записи в базе данных выполняются операции изменения и обновления. `ReadWriteMode` Базы данных определено как свойство только для чтения; его можно задать только с помощью `Attach` команды.  
  
 Если база данных находится в режиме только для чтения, определенные ограничения влияют на обычный набор допустимых операций с базой данных. В следующей таблице приведены эти ограниченные операции.  
  
|Режим «только для чтения»|Ограничения на операции|  
|-------------------|---------------------------|  
|Команды XML/A<br /><br /> <br /><br /> Примечание. При выполнении любой из следующих команд возникает ошибка.|`Create`<br /><br /> `Alter`<br /><br /> `Delete`<br /><br /> `Process`<br /><br /> `MergePartitions`<br /><br /> `DesignAggregations`<br /><br /> `CommitTransaction`<br /><br /> `Restore`<br /><br /> `Synchronize`<br /><br /> `Insert`<br /><br /> `Update`<br /><br /> `Drop`<br /><br /> <br /><br /> Примечание. Обратная запись в ячейку для базы данных в режиме только для чтения является допустимой, однако нельзя зафиксировать изменения.|  
|Инструкции многомерных выражений<br /><br /> <br /><br /> Примечание. При выполнении любой из следующих инструкций происходит ошибка.|`COMMIT TRAN`<br /><br /> `CREATE SESSION CUBE`<br /><br /> `ALTER CUBE`<br /><br /> `ALTER DIMENSION`<br /><br /> `CREATE DIMENSION MEMBER`<br /><br /> `DROP DIMENSION MEMBER`<br /><br /> `ALTER DIMENSION`<br /><br /> <br /><br /> Примечание: Пользователи Excel не могут использовать функцию группирования в сводных таблицах, так как внутренне эта функция реализована с помощью `CREATE SESSION CUBE` команды.|  
|Инструкции расширений интеллектуального анализа данных<br /><br /> <br /><br /> Примечание. При выполнении любой из следующих инструкций происходит ошибка.|`CREATE [SESSION] MINING STRUCTURE`<br /><br /> `ALTER MINING STRUCTURE`<br /><br /> `DROP MINING STRUCTURE`<br /><br /> `CREATE [SESSION] MINING MODEL`<br /><br /> `DROP MINING MODEL`<br /><br /> `IMPORT`<br /><br /> `SELECT INTO`<br /><br /> `INSERT`<br /><br /> `UPDATE`<br /><br /> `DELETE`|  
|Фоновые операции|Отключены все фоновые операции, которые могут привести к изменению базы данных. В их число входят отложенная обработка и упреждающее кэширование.|  
  
## <a name="readwritemode-usage"></a>Использование свойства ReadWriteMode  
 Свойство `ReadWriteMode` базы данных должно использоваться как часть команды базы данных `Attach`. `Attach` Команда позволяет задать значение свойства базы данных `ReadWrite` или `ReadOnly`. Значение свойства `ReadWriteMode` базы данных не может быть изменено напрямую, поскольку оно определено как свойство только для чтения. У вновь создаваемых баз данных свойство `ReadWriteMode` установлено в значение `ReadWrite`. База данных не может быть создана в режиме только для чтения.  
  
 Для переключения `ReadWriteMode` свойства между базы данных `ReadWrite` и `ReadOnly`, необходимо выполнить последовательность `Detach/Attach` команды.  
  
 Всех операций базы данных, за исключением элемента `Attach`, Сохранить `ReadWriteMode` свойства в ее текущем состоянии базы данных. В частности, операции типа `Alter`, `Backup`, `Restore` и `Synchronize` не изменяют значение свойства `ReadWriteMode`.  
  
> [!NOTE]  
>  Локальные кубы могут быть созданы только из базы данных, находящейся в режиме только для чтения.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.AnalysisServices.Server.Attach%2A>   
 <xref:Microsoft.AnalysisServices.Database.Detach%2A>   
 [Присоединение и отсоединение баз данных служб Analysis Services](attach-and-detach-analysis-services-databases.md)   
 [Перемещение базы данных служб Analysis Services](move-an-analysis-services-database.md)   
 [Элемент detach](../xmla/xml-elements-commands/detach-element.md)   
 [Элемент Attach](../xmla/xml-elements-commands/attach-element.md)  
  
  
