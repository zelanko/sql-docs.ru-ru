---
title: 'Задача 2 (необязательно): Создание представления подписки MDS с помощью диспетчера основных данных | Документация Майкрософт'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: f3da8219-e0cb-4848-95ca-285a76ec1ba9
caps.latest.revision: 6
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: b1245beb168f2781e5acca344eb412bde104e4c9
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37284250"
---
# <a name="task-2-optional-creating-a-mds-subscription-view-using-master-data-manager"></a>Задача 2 (дополнительно). Создание представления подписки MDS с помощью диспетчера основных данных
  В этой задаче вы Создание представления подписки для предоставления **поставщика** сущности в **поставщики** модели для других приложений. Это представление в текущей версии учебника не используется.  
  
1.  Переключиться на главную страницу **диспетчера основных данных** ([http://localhost/MDS](http://localhost/MDS)), щелкнув **SQL Server 2012 Master Data Services** вверху.  
  
2.  Нажмите кнопку **управление интеграцией**.  
  
3.  Нажмите кнопку **создание представлений** в строке меню.  
  
     ![Добавить новую кнопку представления подписки](../../2014/tutorials/media/et-creatingamdssubscriptionviewusingmdm-01.jpg "добавить новую кнопку представления подписки")  
  
4.  Нажмите кнопку **+ (плюс)** значок на панели инструментов, чтобы создать представление подписки.  
  
5.  В **Создание представления подписки** введите **поставщики** для **имя представления подписки**.  
  
6.  Выберите **поставщики** для **модели**.  
  
7.  Выберите **VERSION_1** для **версии**.  
  
8.  Выберите **поставщика** для **сущности**.  
  
9. Выберите **конечных элементов** для **формат**.  
  
     ![Кнопка "Сохранить" представление подписки](../../2014/tutorials/media/et-creatingamdssubscriptionviewusingmdm-02.jpg "подписки представление кнопка \"Сохранить\"")  
  
10. Нажмите кнопку **Сохранить** на панели инструментов, чтобы сохранить представление подписки. Это действие создает представление в SQL Server с именем **поставщики**. Это можно проверить с помощью среды SQL Server Management Studio (SSMS).  
  
## <a name="next-step"></a>Следующий шаг  
 [Задача 3 &#40;необязательно&#41;: Просмотр представлений подписки](task-3-optional-reviewing-the-subscription-views.md)  
  
  
