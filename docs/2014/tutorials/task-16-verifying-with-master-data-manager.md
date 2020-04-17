---
title: 'Задача 16: Проверка с помощью главного менеджера данных (ru) Документы Майкрософт'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 57ad9d3e-8f95-4df6-af01-c291ccf49164
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: d9828c02625ae2bc5a85859577a237b4c4fa99c5
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2020
ms.locfileid: "81484684"
---
# <a name="task-16-verifying-with-master-data-manager"></a>Задача 16. Проверка с помощью диспетчера основных данных
  В этой задаче вы проверите состояние пакетного задания, отправленного пакетом служб SSIS, и убедитесь, что данные были переданы на сервер MDS с помощью диспетчера основных данных.  
  
1.  Запуск **Мастер-менеджер данных** ().`http://localhost/MDS` Если он уже открыт, нажмите Microsoft **S'L Server Master Data Services** в верхней части, чтобы переключиться на **главную страницу.**  
  
2.  Нажмите **Управление интеграцией**.  
  
3.  Обратите внимание, что в списке есть партия с именем **EIMBatch.** Нажмите **на данные импорта** в панели меню, если вы не видите следующий экран.  
  
     ![Пакет EIM](../../2014/tutorials/media/et-verifyingwithmasterdatamanager.jpg "Пакет EIM")  
  
4.  Возвращайтесь на главную страницу, щелкните **s'L Server 2012 Master Data Services** в верхней части.  
  
5.  Убедитесь, что модель **поставщиков** выбрана для **модели** и **VERSION_1** выбрана для **версии,** и нажмите **Explorer**.  
  
6.  Вы можете просмотреть данные, импортированные пакетом служб SSIS в MDS. Данные должны быть очищены и не иметь дубликатов значений **кода** (Примечание: столбец **SupplierID** в Excel соответствует атрибуту **кода** сущности поставщика в MDS).  
  
## <a name="next-step"></a>Следующий шаг  
 [Задача 17. Проверка проекта очистки DQS, созданного пакетом SSIS](../../2014/tutorials/task-17-reviewing-dqs-cleansing-project-created-by-the-ssis-package.md)  
  
  
