---
title: Диалоговое окно "Обнаруженные синтаксические ошибки SQL" (визуальные инструменты для баз данных) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.sqlsyntaxerrorsencountered
- vdtsql.chm:69641
ms.assetid: bc9e5784-227e-4c5d-8084-24274fa6c14a
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 2f44636f7ccf2b8aad7794403199acfe68637b15
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/06/2019
ms.locfileid: "65105665"
---
# <a name="sql-syntax-errors-encountered-dialog-box-visual-database-tools"></a>Диалоговое окно «Обнаруженные синтаксические ошибки SQL» (визуальные инструменты для баз данных)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Это диалоговое окно уведомляет о том, что конструктор не может выполнить синтаксический анализ инструкции SQL на панели SQL.  
  
Это диалоговое окно появляется при вводе или редактировании инструкции SQL на панели SQL, после чего следует или переключиться на другую панель, или проверить запрос, или попытаться выполнить запрос. При этом действительно одно из следующих условий.  
  
-   Инструкция SQL неполная или содержит одну или несколько синтаксических ошибок.  
  
-   Инструкция SQL допустима, но не поддерживается в графических панелях (например запрос объединения).  
  
-   Инструкция SQL допустима, но содержит синтаксические выражения, применимые только к используемому подключению к данным.  
  
> [!TIP]  
> Можно проверить, допустима ли инструкция, с помощью клавиши **Проверить синтаксис SQL** на панели инструментов **Запрос** .  
  
В диалоговом окне отображается сообщение, указывающее на причину, по которой нельзя выполнить анализ этой инструкции SQL. Чтобы продолжить, нажмите кнопку **ОК** .  
  
## <a name="see-also"></a>См. также:  
[Разделы по конструированию запросов и представлений (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
