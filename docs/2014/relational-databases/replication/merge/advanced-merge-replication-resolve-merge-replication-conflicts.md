---
title: Обнаружение и разрешение конфликтов репликации слиянием | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
helpviewer_keywords:
- merge replication conflict resolution [SQL Server replication], about conflict resolution
- default conflict resolver
- conflict resolution [SQL Server replication]
- viewing merge replication conflicts
- resolving merge replication conflicts
- articles [SQL Server replication], conflict resolution
- merge replication conflict resolution [SQL Server replication]
- conflict resolution [SQL Server replication], merge replication
ms.assetid: 0d033c76-e8c9-4e35-ab95-4d335abb18c1
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 7da5ae2c327410f7904f712ecd83516b983b894c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48170364"
---
# <a name="detect-and-resolve-merge-replication-conflicts"></a>Обнаружение и разрешение конфликтов репликации слиянием
  Когда издатель и подписчик соединяются и происходит синхронизация, агент слияния проверяет наличие конфликтов. При обнаружении конфликтов агент слияния использует сопоставитель конфликтов для определения данных, которые будут приняты и распространены на другие сайты.  
  
> [!NOTE]  
>  Несмотря на то, что подписчик обычно синхронизируется с издателем, конфликты возникают между обновлениями, осуществляемыми у различных подписчиков, а не между обновлениями, осуществляемыми у подписчика и издателя.  
  
 Репликация слиянием предлагает множество методов для обнаружения и разрешения конфликтов. Для большинства приложений подходит метод по умолчанию:  
  
-   Если конфликт возникает между издателем и подписчиком, принимается изменение издателя, а изменение подписчика отклоняется.  
  
-   Если конфликт происходит между двумя подписчиками, использующими клиентские подписки (тип подписок по запросу, используемых по умолчанию), принимается изменение первого подписчика для синхронизации с издателем, а изменение второго подписчика отклоняется. Сведения об указании клиентских и серверных подписок см. в статье [Указание типа подписки на публикацию слиянием и приоритета разрешения конфликтов (SQL Server Management Studio)](../specify-a-merge-subscription-type-and-conflict-resolution-priority.md).  
  
-   Если конфликт возникает между двумя подписчиками, использующими серверные подписки (тип принудительных подписок по умолчанию), принимается изменение подписчика с наибольшим значением приоритета, а изменение второго подписчика отклоняется. Если значения приоритетов равны, принимается изменение первого подписчика для синхронизации с издателем.  
  
 Дополнительные сведения об обнаружении и разрешении конфликтов репликации слиянием см. в разделе [Advanced Merge Replication Conflict Detection and Resolution](advanced-merge-replication-conflict-detection-and-resolution.md).  
  
## <a name="see-also"></a>См. также  
 [Параметры статьи для репликации слиянием](article-options-for-merge-replication.md)   
 [Подписка на публикации](../subscribe-to-publications.md)  
  
  
