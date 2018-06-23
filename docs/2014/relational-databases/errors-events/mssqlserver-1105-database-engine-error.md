---
title: MSSQLSERVER_1105 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 1105 (Database Engine error)
ms.assetid: e7f4ad02-8c7f-4bb9-9781-2c86253f2138
caps.latest.revision: 20
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: f05c9197c1a19625d4c9a7153543032a5e6bb72a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36191964"
---
# <a name="mssqlserver1105"></a>MSSQLSERVER_1105
    
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
>  Когда индекс располагается в нескольких файлах, `ALTER INDEX REORGANIZE` может вернуть ошибку 1105 при заполнении одного их файлов. Процесс реорганизации блокируется, если процесс пытается переместить строки в полный файл. Чтобы обойти это ограничение, выполните `ALTER INDEX REBUILD` вместо `ALTER INDEX REORGANIZE` или увеличьте ограничение на рост файла всех заполненных файлов.  
  
  