---
title: Убедитесь, что отсутствуют файлы базы данных на сжатых дисках, во время обновления | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- compressed drives [SQL Server]
ms.assetid: 63be6853-c54a-42b2-ae1a-db2175f1d28e
caps.latest.revision: 19
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 59370b953c377e983f58c3037a7920de0076bd56
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36087287"
---
# <a name="verify-that-no-database-files-are-on-compressed-drives-during-the-upgrade-process"></a>Убедитесь, что во время процесса обновления на сжатых дисках отсутствуют файлы базы данных
  Помощник по обновлению обнаружил файлы базы данных на сжатом диске. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не может создавать или обновлять базы данных на сжатых дисках.  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Действие по исправлению  
 При установке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выберите несжатый диск для системных баз данных, а также убедитесь, что обновляемые базы данных не находятся на сжатых дисках. Однако обратите внимание, что после обновления базы данных можно записывать на диск со сжатой файловой системой NTFS базы данных и вторичные файловые группы, доступные только для чтения.  
  
## <a name="see-also"></a>См. также  
 [Проблемы обновления компонента Database Engine](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Помощник по обновлению SQL Server 2014 &#91;new&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
