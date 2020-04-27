---
title: Создание представления подписки (Master Data Services) | Документация Майкрософт
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
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "65479938"
---
# <a name="create-a-subscription-view-master-data-services"></a>Создание представления подписки (службы Master Data Services)
  Создайте представление подписки, если необходимо создать представление данных в [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] базе данных для использования в системах-подписчиках.  
  
## <a name="prerequisites"></a>Предварительные условия  
 Для выполнения этой процедуры:  
  
-   необходимо разрешение на доступ к функциональной области **Управление интеграцией** ;  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в разделе [administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
### <a name="to-create-a-subscription-view"></a>Создание представления подписки  
  
1.  В [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните область **Управление интеграцией**.  
  
2.  В строке меню щелкните **Создание представлений**.  
  
3.  На странице **представления подписки** щелкните **Добавить представление подписки**.  
  
4.  В области **Создание представления подписки** в поле **имя представления подписки** введите имя представления.  
  
5.  Выберите модель из списка **Модель** .  
  
6.  Выберите параметр **версия** или **флаг версии** , а затем выберите из соответствующего списка.  
  
    > [!TIP]  
    >  Создайте представление подписки на основе флага версии. При блокировании версии флаг можно переприсвоить открытой версии, не обновляя представления подписки.  
  
7.  Выберите параметр **сущность** или **производная иерархия** , а затем выберите из соответствующего списка.  
  
8.  Выберите формат представления подписки из списка **Формат** .  
  
9. Если выбрано значение из списка **Формат****Явные уровни** или **Производные уровни** , то введите число уровней в иерархии для включения в представление.  
  
10. Нажмите кнопку **Сохранить**.  
  
## <a name="see-also"></a>См. также  
 [Экспорт Master Data Services &#40;данных&#41;](overview-exporting-data-master-data-services.md)   
 [Удаление представления подписки &#40;Master Data Services&#41;](delete-a-subscription-view-master-data-services.md)   
 [Создание флага версии (службы Master Data Services)](create-a-version-flag-master-data-services.md)  
  
  
