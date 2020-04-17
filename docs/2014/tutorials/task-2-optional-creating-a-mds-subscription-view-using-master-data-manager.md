---
title: 'Задача 2 (необязательно): Создание представления подписки MDS с помощью Master Data Manager Документы Майкрософт'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: f3da8219-e0cb-4848-95ca-285a76ec1ba9
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: cc923792adc3fefb5ebaab9e225169648394c71f
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2020
ms.locfileid: "81484714"
---
# <a name="task-2-optional-creating-a-mds-subscription-view-using-master-data-manager"></a>Задача 2 (необязательно). Создание представления подписки MDS с помощью диспетчера основных данных
  В этой задаче создается представление о подписке, чтобы предоставить сущность **поставщика** в модели **Поставщиков** другим приложениям. Это представление в текущей версии учебника не используется.  
  
1.  Переключитесь на главную страницу **Master Data Manager** (),`http://localhost/MDS`нажав на **s'L Server 2012 Master Data Services** в верхней части.  
  
2.  Нажмите **Управление интеграцией**.  
  
3.  Нажмите **Создать Просмотры** в баре меню.  
  
     ![Кнопка «Добавить новое представление подписки»](../../2014/tutorials/media/et-creatingamdssubscriptionviewusingmdm-01.jpg "Кнопка «Добавить новое представление подписки»")  
  
4.  Нажмите значок **«Плюс»** на панели инструментов, чтобы создать представление подписки.  
  
5.  В панели **просмотра подписки** введите имя представления **подписки.** **Subscription view name**  
  
6.  Выберите **Поставщиков** для **модели**.  
  
7.  Выберите **VERSION_1** для **версии**.  
  
8.  Выберите **Поставщика** для **entity**.  
  
9. Выберите **участников Leaf** для **Формата**.  
  
     ![Кнопка «Сохранить представление подписки»](../../2014/tutorials/media/et-creatingamdssubscriptionviewusingmdm-02.jpg "Кнопка «Сохранить представление подписки»")  
  
10. Нажмите **Сохранить** на панели инструментов, чтобы сохранить представление подписки. Это действие создает представление в сервере S'L под названием **Поставщики**. Это можно проверить с помощью среды SQL Server Management Studio (SSMS).  
  
## <a name="next-step"></a>Следующий шаг  
 [Задача 3 &#40;Факультативное&#41;: Просмотр просмотров подписок](task-3-optional-reviewing-the-subscription-views.md)  
  
  
