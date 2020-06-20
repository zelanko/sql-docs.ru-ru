---
title: Убедитесь, что в процессе обновления нет файлов базы данных на сжатых дисках | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- compressed drives [SQL Server]
ms.assetid: 63be6853-c54a-42b2-ae1a-db2175f1d28e
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 9c04f7890ba8d8efe64afaf11b922af156c5de46
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85065133"
---
# <a name="verify-that-no-database-files-are-on-compressed-drives-during-the-upgrade-process"></a>Убедитесь, что во время процесса обновления на сжатых дисках отсутствуют файлы базы данных
  Помощник по обновлению обнаружил файлы базы данных на сжатом диске. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не может создавать или обновлять базы данных на сжатых дисках.  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Действие по исправлению  
 При установке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выберите несжатый диск для системных баз данных, а также убедитесь, что обновляемые базы данных не находятся на сжатых дисках. Однако обратите внимание, что после обновления базы данных можно записывать на диск со сжатой файловой системой NTFS базы данных и вторичные файловые группы, доступные только для чтения.  
  
## <a name="see-also"></a>См. также:  
 [Проблемы обновления ядро СУБД](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Советник по переходу SQL Server 2014 &#91;New&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
