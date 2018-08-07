---
title: Выполнение скриптов до и после применения моментального снимка | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- snapshots [SQL Server replication], scripts
- scripts [SQL Server replication], snapshots
- snapshot replication [SQL Server], scripts
- scripts [SQL Server replication]
ms.assetid: 9a6872c2-9bed-477f-9d2f-332d640edcf2
caps.latest.revision: 35
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: c2caf124d88c9a74990771d8a65ac0beb94ec1bd
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/06/2018
ms.locfileid: "39532994"
---
# <a name="execute-scripts-before-and-after-the-snapshot-is-applied"></a>Выполнение скриптов до и после применения моментального снимка
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Можно указать скрипты для выполнения на подписчике до и после применения моментального снимка. Скрипты могут использоваться по различным причинам, таким как создание учетных имен и схем (владельцы объекта) на каждом подписчике.  
  
 Вы указываете размещение файла для каждого скрипта, и агент моментальных снимков копирует файлы скриптов в текущую папку моментальных снимков при каждой обработке моментального снимка. При применении моментального снимка агент распространителя или агент слияния запускает скрипт, предшествующий моментальному снимку, перед любым из скриптов реплицируемых объектов. Агент распространителя или агент слияния запускает скрипт, следующий за моментальным снимком, после применения всех других скриптов реплицируемых объектов и применения данных. После того как применение моментального снимка завершено и файлы скриптов успешно выполнены, файлы скриптов удаляются из рабочего каталога на подписчике.  
  
 Скрипт запускается при помощи служебной программы **sqlcmd** . До развертывания скрипта запустите его с помощью **sqlcmd** , чтобы убедиться, что он выполняется должным образом. Содержимое скриптов, которые выполняются до и после применения моментального снимка, должно быть повторяемым. Например, если вы создаете таблицу в скрипте, необходимо сначала проверить ее существование и предпринять соответствующее действие, если таблица существует. Скрипт должен быть повторяемым, потому что, если необходимо повторно инициализировать подписку, для которой уже был применен скрипт, скрипт будет применен повторно, когда новый моментальный снимок будет применяться в процессе повторной инициализации.  
  
 При сжатии файла моментального снимка (посредством его помещения в CAB-файл [!INCLUDE[msCoName](../../includes/msconame-md.md)] ) скрипты так же сжимаются и помещаются в CAB-файл. После того как сжатый файл моментального снимка передан подписчику и распакован в рабочий каталог на подписчике, выполняются все скрипты, помеченные как скрипты, предшествующие моментальному снимку. Аналогично любой скрипт, выполняющийся после моментального снимка, распаковывается и выполняется на подписчике как последний шаг в применении моментального снимка.  
  
 **Выполнение скриптов до и после применения моментального снимка**  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]: [Практическое руководство: выполнение скриптов до и после применения моментального снимка \(среда SQL Server Management Studio\)](../../relational-databases/replication/execute-scripts-before-and-after-a-snapshot-is-applied.md)  
  
-   Программирование репликации на [!INCLUDE[tsql](../../includes/tsql-md.md)]: [Настройка свойств моментального снимка &#40;программирование репликации на языке Transact-SQL&#41;](../../relational-databases/replication/publish/configure-snapshot-properties-replication-transact-sql-programming.md)  
  
## <a name="see-also"></a>См. также:  
 [Инициализация подписки с помощью моментального снимка](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)   
 [Параметры моментального снимка](../../relational-databases/replication/snapshot-options.md)  
  
  
