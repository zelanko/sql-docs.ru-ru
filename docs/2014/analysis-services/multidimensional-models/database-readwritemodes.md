---
title: Режимы readwritemodes базы данных | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- databases [Analysis Services], read/write
- databases [Analysis Services], read-only
ms.assetid: 03d7cb5c-7ff0-4e15-bcd2-7075d1b0dd69
author: minewiskan
ms.author: owend
ms.openlocfilehash: 723eb7c1c0e8547ee411fc54ecd4aca613011b38
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/09/2020
ms.locfileid: "84547116"
---
# <a name="database-readwritemodes"></a>Режимы ReadWriteModes базы данных
  Часто возникает ситуация, когда администратору базы данных (dba) служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] необходимо переключить базу данных из режима для чтения и записи в режим только для чтения или наоборот. Обычно это продиктовано производственной необходимостью, например, чтобы обеспечить общий доступ нескольким серверам к папке базы данных для масштабирования решения и повышения производительности. В таких ситуациях `ReadWriteMode` свойство Database позволяет [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] администратору базы данных легко изменять режим работы базы данных.  
  
## <a name="readwritemode-database-property"></a>Свойство ReadWriteMode базы данных  
 Свойство `ReadWriteMode` базы данных определяет режим базы данных: для чтения и записи или только для чтения. Эти значения являются единственными допустимыми для данного свойства. Пока база данных находится в режиме только для чтения, к ней не могут применяться операции изменения или обновления. В режиме для чтения и записи в базе данных выполняются операции изменения и обновления. Свойство `ReadWriteMode` базы данных определено как свойство только для чтения. Его можно задать только с помощью команды `Attach`.  
  
 Если база данных находится в режиме только для чтения, определенные ограничения влияют на обычный набор допустимых операций с базой данных. В следующей таблице приведены эти ограниченные операции.  
  
|Режим «только для чтения»|Ограничения на операции|  
|-------------------|---------------------------|  
|Команды XML/A<br /><br /> <br /><br /> Примечание. При выполнении любой из следующих команд возникает ошибка.|`Create`<br /><br /> `Alter`<br /><br /> `Delete`<br /><br /> `Process`<br /><br /> `MergePartitions`<br /><br /> `DesignAggregations`<br /><br /> `CommitTransaction`<br /><br /> `Restore`<br /><br /> `Synchronize`<br /><br /> `Insert`<br /><br /> `Update`<br /><br /> `Drop`<br /><br /> <br /><br /> Примечание. Обратная запись в ячейку для базы данных в режиме только для чтения является допустимой, однако нельзя зафиксировать изменения.|  
|Инструкции многомерных выражений<br /><br /> <br /><br /> Примечание. При выполнении любой из следующих инструкций происходит ошибка.|`COMMIT TRAN`<br /><br /> `CREATE SESSION CUBE`<br /><br /> `ALTER CUBE`<br /><br /> `ALTER DIMENSION`<br /><br /> `CREATE DIMENSION MEMBER`<br /><br /> `DROP DIMENSION MEMBER`<br /><br /> `ALTER DIMENSION`<br /><br /> <br /><br /> Примечание. Пользователи Excel не могут использовать функцию группирования в сводных таблицах, так как внутренне эта функция реализована с помощью команд `CREATE SESSION CUBE`.|  
|Инструкции расширений интеллектуального анализа данных<br /><br /> <br /><br /> Примечание. При выполнении любой из следующих инструкций происходит ошибка.|`CREATE [SESSION] MINING STRUCTURE`<br /><br /> `ALTER MINING STRUCTURE`<br /><br /> `DROP MINING STRUCTURE`<br /><br /> `CREATE [SESSION] MINING MODEL`<br /><br /> `DROP MINING MODEL`<br /><br /> `IMPORT`<br /><br /> `SELECT INTO`<br /><br /> `INSERT`<br /><br /> `UPDATE`<br /><br /> `DELETE`|  
|Фоновые операции|Отключены все фоновые операции, которые могут привести к изменению базы данных. В их число входят отложенная обработка и упреждающее кэширование.|  
  
## <a name="readwritemode-usage"></a>Использование свойства ReadWriteMode  
 Свойство `ReadWriteMode` базы данных должно использоваться как часть команды базы данных `Attach`. Команда `Attach` позволяет установить это свойство либо в значение `ReadWrite`, либо в значение `ReadOnly`. Значение свойства `ReadWriteMode` базы данных не может быть изменено напрямую, поскольку оно определено как свойство только для чтения. У вновь создаваемых баз данных свойство `ReadWriteMode` установлено в значение `ReadWrite`. База данных не может быть создана в режиме только для чтения.  
  
 Чтобы переключить `ReadWriteMode` свойство базы данных между `ReadWrite` и `ReadOnly` , необходимо выполнить последовательность `Detach/Attach` команд.  
  
 Ни одна из операций базы данных, за исключением `Attach`, не изменяет значение свойства базы данных `ReadWriteMode`. В частности, операции типа `Alter`, `Backup`, `Restore` и `Synchronize` не изменяют значение свойства `ReadWriteMode`.  
  
> [!NOTE]  
>  Локальные кубы могут быть созданы только из базы данных, находящейся в режиме только для чтения.  
  
## <a name="see-also"></a>См. также:  
 <xref:Microsoft.AnalysisServices.Server.Attach%2A>   
 <xref:Microsoft.AnalysisServices.Database.Detach%2A>   
 [Присоединение и отсоединение баз данных Analysis Services](attach-and-detach-analysis-services-databases.md)   
 [Перемещение базы данных Analysis Services](move-an-analysis-services-database.md)   
 [Detach, элемент](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/detach-element)   
 [Элемент Attach](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/attach-element)  
  
  
