---
title: 'Задача 16: Проверка с помощью диспетчера основных данных | Документы Microsoft'
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
ms.topic: article
ms.assetid: 57ad9d3e-8f95-4df6-af01-c291ccf49164
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 36220f21f3e2e28d75ff546857fd87b1e71436f1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36097840"
---
# <a name="task-16-verifying-with-master-data-manager"></a>Задача 16. Проверка с помощью диспетчера основных данных
  В этой задаче вы проверите состояние пакетного задания, отправленного пакетом служб SSIS, и убедитесь, что данные были переданы на сервер MDS с помощью диспетчера основных данных.  
  
1.  Запустите **диспетчера основных данных** ([http://localhost/MDS](http://localhost/MDS)). Если он уже открыт, нажмите кнопку **Microsoft SQL Server Master Data Services** в верхней части, чтобы переключиться на **Домашняя страница**.  
  
2.  Нажмите кнопку **управление интеграцией**.  
  
3.  Обратите внимание, что пакет с именем **EIMBatch** , отправленные вами в списке. Нажмите кнопку **импорта данных** в строке меню, если вы не видите следующий экран.  
  
     ![Пакет EIM](../../2014/tutorials/media/et-verifyingwithmasterdatamanager.jpg "пакет EIM")  
  
4.  Перейдите на домашнюю страницу, нажмите кнопку **SQL Server 2012 Master Data Services** вверху.  
  
5.  Убедитесь, что **поставщики** выбрана модель **модель** и **VERSION_1** выбран для **версии**и нажмите кнопку  **Обозреватель**.  
  
6.  Вы можете просмотреть данные, импортированные пакетом служб SSIS в MDS. Данные должны быть очищены и не быть дубликатов **кода** значения (Примечание: **SupplierID** столбец в Excel соответствует **кода** атрибут сущности Supplier в MDS).  
  
## <a name="next-step"></a>Следующий шаг  
 [Задача 17. Обзор проекта очистки данных DQS, созданного пакетом служб SSIS](../../2014/tutorials/task-17-reviewing-dqs-cleansing-project-created-by-the-ssis-package.md)  
  
  