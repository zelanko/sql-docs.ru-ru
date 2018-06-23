---
title: Параметры моментального снимка | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- snapshot replication [SQL Server], options
- snapshots [SQL Server replication], options
ms.assetid: 759fab42-66c7-4541-a7a3-bb6fb868493c
caps.latest.revision: 27
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 62f5f6550cc6696cab12ca838dcd34669ee18a0a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36193993"
---
# <a name="snapshot-options"></a>Параметры моментального снимка
  При инициализации подписки с помощью моментального снимка можно выполнить следующие действия:  
  
-   Указать другое расположение папки моментальных снимков вместо папки по умолчанию или в дополнение к ней. Дополнительные сведения см. в статье [Alternate Snapshot Folder Locations](alternate-snapshot-folder-locations.md).  
  
-   Сжать моментальные снимки для хранения на съемном носителе или для передачи по медленной сети. Дополнительные сведения см. в разделе [Compressed Snapshots](compressed-snapshots.md).  
  
-   Выполнить скрипты [!INCLUDE[tsql](../../includes/tsql-md.md)] до или после применения моментального снимка. Дополнительные сведения см. в статье [Выполнение скриптов до и после применения моментального снимка](execute-scripts-before-and-after-the-snapshot-is-applied.md).  
  
-   Передать файлы моментальных снимков с помощью протокола передачи файлов (FTP). Дополнительные сведения см. в статье [Передача моментальных снимков через FTP](transfer-snapshots-through-ftp.md).  
  
## <a name="see-also"></a>См. также  
 [Инициализация подписки с помощью моментального снимка](initialize-a-subscription-with-a-snapshot.md)  
  
  