---
title: Размещение файлов данных и файлов журнала на различных дисках | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 6cbedc27-4d77-44ad-bed2-c23b628475a7
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 54f469f8ab9f0daaf6f37c8f6bad1878bc716dbd
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "68086932"
---
# <a name="place-data-and-log-files-on-separate-drives"></a>Размещение файлов данных и файлов журнала на различных дисках
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
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
  
  
