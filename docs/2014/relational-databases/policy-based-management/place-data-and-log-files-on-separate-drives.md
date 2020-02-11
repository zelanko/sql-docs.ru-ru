---
title: Размещение файлов данных и файлов журнала на различных дисках | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 6cbedc27-4d77-44ad-bed2-c23b628475a7
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: b957cfa6416b9c557123a235bc62832057f907c6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62691755"
---
# <a name="place-data-and-log-files-on-separate-drives"></a>Размещение файлов данных и файлов журнала на различных дисках
  Это правило проверяет, размещаются ли файлы данных и файлы журнала на разных логических дисках. Размещение файлов данных и файлов журнала на одном устройстве может привести к состязанию, что вызовет снижение производительности. Размещение файлов на разных дисках позволяет выполнять операции ввода-вывода для файлов данных и файлов журнала параллельно.  
  
## <a name="best-practices-recommendations"></a>Рекомендации  
 При создании новой базы данных укажите разные диски для данных и журналов. Чтобы переместить файлы после создания базы данных, ее необходимо перевести в режим «вне сети». Переместите файлы одним из следующих способов.  
  
> [!NOTE]  
>  Эта политика не может обнаружить отдельные физические устройства посредством точек подключения  
  
-   Восстановите базу данных из резервной копии, выполнив инструкцию RESTORE DATABASE с параметром WITH MOVE.  
  
-   Отсоедините и заново присоедините базу данных, указав различные расположения для хранения данных и журнала.  
  
-   Укажите новое расположение, выполнив инструкцию ALTER DATABASE с параметром MODIFY FILE, а затем перезапустив экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="for-more-information"></a>Дополнительные сведения см. в разделе  
 [Перемещение файлов базы данных](../databases/move-database-files.md)  
  
 [Перемещение пользовательских баз данных](../databases/move-user-databases.md)  
  
 [Присоединение и отсоединение базы данных (SQL Server)](../databases/database-detach-and-attach-sql-server.md)  
  
## <a name="see-also"></a>См. также:  
 [Наблюдение с помощью управления на основе политик и принудительное применение рекомендаций с помощью управления на основе политик](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
