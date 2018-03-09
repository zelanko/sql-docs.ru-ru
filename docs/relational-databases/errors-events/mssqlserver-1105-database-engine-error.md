---
title: "MSSQLSERVER_1105 | Документация Майкрософт"
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 1105 (Database Engine error)
ms.assetid: e7f4ad02-8c7f-4bb9-9781-2c86253f2138
caps.latest.revision: "19"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 28cb37ebdca0e3bb0078c591a78ff099ac44c5a7
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver1105"></a>MSSQLSERVER_1105
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|1105|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|NO_MORE_SPACE_IN_FG|  
|Текст сообщения|Не удалось выделить место для объекта '%.*ls'%.\*ls в базе данных '%.\*ls', так как файловая группа '%.\*ls' переполнена. Выделите место на диске, удалив ненужные файлы или объекты в файловой группе, добавив дополнительные файлы в файловую группу или указав параметр автоматического увеличения размера для существующих файлов в файловой группе.|  
  
## <a name="explanation"></a>Объяснение  
Нет свободного места на диске в файловой группе.  
  
## <a name="user-action"></a>Действие пользователя  
Место в файловой группе можно освободить следующим образом.  
  
-   Включить автоувеличение.  
  
-   Добавить файлы в файловую группу.  
  
-   Освободить место на диске, удалив ненужные индексы или таблицы.  
  
-   Дополнительные сведения см. в разделе «Диагностика недостатка места на диске» электронной документации по SQL Server.  
  
> [!NOTE]  
> Когда индекс располагается в нескольких файлах, **ALTER INDEX REORGANIZE** может вернуть ошибку 1105 при заполнении одного их файлов. Процесс реорганизации блокируется, если процесс пытается переместить строки в полный файл. Чтобы обойти это ограничение, выполните **ALTER INDEX REBUILD** вместо **ALTER INDEX REORGANIZE** или увеличьте ограничение на размер файла для файлов, которые достигают этого ограничения.  
  
