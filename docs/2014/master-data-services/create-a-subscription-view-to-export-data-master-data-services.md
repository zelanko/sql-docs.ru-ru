---
title: Создание представления подписки (Master Data Services) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- master-data-services
ms.topic: conceptual
helpviewer_keywords:
- subscription views [Master Data Services], creating
- creating subscription views [Master Data Services]
ms.assetid: a5e28961-af16-414a-9845-d2e06aac5214
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 17df4d4f8d311be311907d18ad61cbbce05ea397
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48217596"
---
# <a name="create-a-subscription-view-master-data-services"></a>Создание представления подписки (службы Master Data Services)
  Создание представления подписки в том случае, если вы хотите создать представление данных в [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] базы данных для использования системами-подписчиками.  
  
## <a name="prerequisites"></a>предварительные требования  
 Для выполнения этой процедуры:  
  
-   необходимо разрешение на доступ к функциональной области **Управление интеграцией** ;  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в статье [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
### <a name="to-create-a-subscription-view"></a>Создание представления подписки  
  
1.  В [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните область **Управление интеграцией**.  
  
2.  В строке меню щелкните **Создание представлений**.  
  
3.  На **представления подписки** щелкните **добавить представление подписки**.  
  
4.  В **Создание представления подписки** области в **имя представления подписки** введите имя для представления.  
  
5.  Выберите модель из списка **Модель** .  
  
6.  Выберите либо **версии** или **флаг версии** параметр, а затем выберите из соответствующего списка.  
  
    > [!TIP]  
    >  Создайте представление подписки на основе флага версии. При блокировании версии флаг можно переприсвоить открытой версии, не обновляя представления подписки.  
  
7.  Выберите либо **сущности** или **производную иерархию** параметр, а затем выберите из соответствующего списка.  
  
8.  Выберите формат представления подписки из списка **Формат** .  
  
9. Если выбрано значение из списка **Формат**  **Явные уровни** или **Производные уровни** , то введите число уровней в иерархии для включения в представление.  
  
10. Нажмите кнопку **Сохранить**.  
  
## <a name="see-also"></a>См. также  
 [Экспорт данных &#40;службы Master Data Services&#41;](overview-exporting-data-master-data-services.md)   
 [Удаление представления подписки (службы Master Data Services)](delete-a-subscription-view-master-data-services.md)   
 [Создание флага версии &#40;службы Master Data Services&#41;](create-a-version-flag-master-data-services.md)  
  
  
