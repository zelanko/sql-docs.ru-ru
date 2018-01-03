---
title: "Диалоговое окно \"Обнаруженные синтаксические ошибки SQL\" (визуальные инструменты для баз данных) | Документация Майкрософт"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-visual-db
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vdt.dlgbox.sqlsyntaxerrorsencountered
- vdtsql.chm:69641
ms.assetid: bc9e5784-227e-4c5d-8084-24274fa6c14a
caps.latest.revision: "3"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: fd83cac5ef064cb5df226ecc94b5be954f506405
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="sql-syntax-errors-encountered-dialog-box-visual-database-tools"></a>Диалоговое окно «Обнаруженные синтаксические ошибки SQL» (визуальные инструменты для баз данных)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] Это диалоговое окно уведомляет о том, что конструктор не может выполнить синтаксический анализ инструкции SQL на панели SQL.  
  
Это диалоговое окно появляется при вводе или редактировании инструкции SQL на панели SQL, после чего следует или переключиться на другую панель, или проверить запрос, или попытаться выполнить запрос. При этом действительно одно из следующих условий.  
  
-   Инструкция SQL неполная или содержит одну или несколько синтаксических ошибок.  
  
-   Инструкция SQL допустима, но не поддерживается в графических панелях (например запрос объединения).  
  
-   Инструкция SQL допустима, но содержит синтаксические выражения, применимые только к используемому подключению к данным.  
  
> [!TIP]  
> Можно проверить, допустима ли инструкция, с помощью клавиши **Проверить синтаксис SQL** на панели инструментов **Запрос** .  
  
В диалоговом окне отображается сообщение, указывающее на причину, по которой нельзя выполнить анализ этой инструкции SQL. Чтобы продолжить, нажмите кнопку **ОК** .  
  
## <a name="see-also"></a>См. также:  
[Разделы по конструированию запросов и представлений (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
