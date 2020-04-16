---
title: Создание представления подписки (Master Data Services) Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- subscription views [Master Data Services], creating
- creating subscription views [Master Data Services]
ms.assetid: a5e28961-af16-414a-9845-d2e06aac5214
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: c4a2f747192b1cddefeac256d4470a2b345305de
ms.sourcegitcommit: a3f5c3742d85d21f6bde7c6ae133060dcf1ddd44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/15/2020
ms.locfileid: "65479938"
---
# <a name="create-a-subscription-view-master-data-services"></a>Создание представления подписки (службы Master Data Services)
  Создание представления подписки, когда требуется создать представление [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] данных в базе данных для использования с помощью подписных систем.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Для выполнения этой процедуры:  
  
-   необходимо разрешение на доступ к функциональной области **Управление интеграцией** ;  
  
-   необходимо быть администратором модели. Для получения дополнительной информаци [&#41;&#40;и см. ](administrators-master-data-services.md)  
  
### <a name="to-create-a-subscription-view"></a>Создание представления подписки  
  
1.  В [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните область **Управление интеграцией**.  
  
2.  В строке меню щелкните **Создание представлений**.  
  
3.  На странице **просмотров подписки** нажмите **«Добавить» просмотр подписки**.  
  
4.  В панели **просмотра подписки** в поле **представления подписки** введите имя для представления.  
  
5.  Выберите модель из списка **Модель** .  
  
6.  Выберите параметр **«Флаг версии»** или **«Флаг версии»,** а затем выберите из соответствующего списка.  
  
    > [!TIP]  
    >  Создайте представление подписки на основе флага версии. При блокировании версии флаг можно переприсвоить открытой версии, не обновляя представления подписки.  
  
7.  Выберите параметр иерархии **сущности** или **derived,** а затем выберите из соответствующего списка.  
  
8.  Выберите формат представления подписки из списка **Формат** .  
  
9. Если выбрано значение из списка **Формат****Явные уровни** или **Производные уровни** , то введите число уровней в иерархии для включения в представление.  
  
10. Выберите команду **Сохранить**.  
  
## <a name="see-also"></a>См. также:  
 [Экспорт данных &#40;мастер-службы данных&#41;](overview-exporting-data-master-data-services.md)   
 [Удалить представление подписок &#40;&#41;мастер-данных](delete-a-subscription-view-master-data-services.md)   
 [Создание флага версии (службы Master Data Services)](create-a-version-flag-master-data-services.md)  
  
  
