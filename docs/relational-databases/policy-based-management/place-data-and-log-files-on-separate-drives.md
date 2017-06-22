---
title: "Размещение файлов данных и файлов журнала на различных дисках | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 6cbedc27-4d77-44ad-bed2-c23b628475a7
caps.latest.revision: 9
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: d1105f11c98ac0b0c509f4c1d43a92ddd1a7a10c
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="place-data-and-log-files-on-separate-drives"></a>Размещение файлов данных и файлов журнала на различных дисках
  Это правило проверяет, размещаются ли файлы данных и файлы журнала на разных логических дисках. Размещение файлов данных И файлов журнала на одном устройстве может привести к состязанию, что вызовет снижение производительности. Размещение файлов на разных дисках позволяет выполнять операции ввода-вывода для файлов данных и файлов журнала параллельно.  
  
## <a name="recommendations"></a>Рекомендации  
 При создании новой базы данных укажите разные диски для данных и журналов. Чтобы переместить файлы после создания базы данных, ее необходимо перевести в режим «вне сети». Переместите файлы одним из следующих способов:  
  
> [!NOTE]  
>  Эта политика не может обнаружить отдельные физические устройства посредством точек подключения  
  
-   Восстановите базу данных из резервной копии, выполнив инструкцию RESTORE DATABASE с параметром WITH MOVE.  
  
-   Отсоедините и заново присоедините базу данных, указав различные расположения для хранения данных и журнала.  
  
-   Укажите новое расположение, выполнив инструкцию ALTER DATABASE с параметром MODIFY FILE, а затем перезапустив экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="for-more-information"></a>Дополнительные сведения см. в разделе  
 [Перемещение файлов базы данных](../../relational-databases/databases/move-database-files.md)  
  
 [Перемещение пользовательских баз данных](../../relational-databases/databases/move-user-databases.md)  
  
 [Присоединение и отсоединение базы данных (SQL Server)](../../relational-databases/databases/database-detach-and-attach-sql-server.md)  
  
## <a name="see-also"></a>См. также:  
 [Наблюдение с помощью управления на основе политик и принудительное применение рекомендаций с помощью управления на основе политик](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
