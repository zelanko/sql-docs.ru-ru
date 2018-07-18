---
title: Занятие 2. Подготовка папки моментальных снимков | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: f286cde9-c0d0-43ef-b7ba-53c3cbb8906c
caps.latest.revision: 19
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 3bc3b7fa0367674ff5db39e3fab424cac0ea7380
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37246234"
---
# <a name="lesson-2-preparing-the-snapshot-folder"></a>Занятие 2. Подготовка папки моментальных снимков
  На этом занятии можно научиться настраивать папку моментальных снимков для создания и хранения моментального снимка публикации.  
  
### <a name="to-create-a-share-for-the-snapshot-folder-and-assign-permissions"></a>Создание ресурса для папки моментальных снимков и настройка разрешений  
  
1.  В проводнике Windows перейдите к папке данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Путь по умолчанию — «C:\Program Files\Microsoft SQL Server\MSSQL.X\MSSQL\Data».  
  
2.  Создайте папку с именем **repldata**.  
  
3.  Правой кнопкой мыши щелкните эту папку и выберите пункт **Свойства**.  
  
4.  В диалоговом окне **Свойства repldata** на вкладке **Общий доступ** щелкните **Открыть общий доступ**.  
  
5.  В диалоговом окне **Общий доступ к файлу** щелкните **Открыть общий доступ**, а затем — **Готово**.  
  
6.  На вкладке **Безопасность** нажмите **Изменить**.  
  
7.  В диалоговом окне **Разрешения** нажмите кнопку **Добавить**. В текстовом поле **Выбор пользователей, компьютеров, учетных записей служб или групп** введите имя учетной записи агента моментальных снимков, созданной на занятии 1, в виде \<*Имя_компьютера>***\repl_snapshot**, где \<* Имя_компьютера>* обозначает имя издателя. Щелкните **Проверить имена**и нажмите кнопку **ОК**.  
  
8.  Повторите предыдущий шаг, чтобы добавить разрешения для агента распространителя в формате \<*Имя_компьютера>***\repl_distribution** и для агента слияния в формате \<* Имя_компьютера>***\repl_merge**.  
  
9. Убедитесь в том, что следующие разрешения допустимы:  
  
    -   repl_snapshot — «Полный контроль»;  
  
    -   repl_distribution — «Чтение»;  
  
    -   repl_merge — «Чтение».  
  
10. Нажмите кнопку **ОК** , чтобы закрыть диалоговое окно **Свойства repldata** , и создайте ресурс repldata.  
  
## <a name="next-steps"></a>Следующие шаги  
 Настройка ресурса папки моментальных снимков выполнена успешно. Далее предстоит настроить распространение. См. [Занятие 3. Настройка распространения](lesson-3-configuring-distribution.md).  
  
## <a name="see-also"></a>См. также  
 [Защита папки моментальных снимков](security/secure-the-snapshot-folder.md)  
  
  
