---
title: 'Задача 16: Проверка с помощью диспетчера основных данных | Документация Майкрософт'
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
ms.assetid: 57ad9d3e-8f95-4df6-af01-c291ccf49164
caps.latest.revision: 6
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 7d0c5b2f72a04b1c1f99829e61ca2dca3fedc39a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37304654"
---
# <a name="task-16-verifying-with-master-data-manager"></a>Задача 16. Проверка с помощью диспетчера основных данных
  В этой задаче вы проверите состояние пакетного задания, отправленного пакетом служб SSIS, и убедитесь, что данные были переданы на сервер MDS с помощью диспетчера основных данных.  
  
1.  Запустите **диспетчера основных данных** ([http://localhost/MDS](http://localhost/MDS)). Если он уже открыт, нажмите кнопку **Microsoft SQL Server Master Data Services** вверху, чтобы переключиться в режим **Домашняя страница**.  
  
2.  Нажмите кнопку **управление интеграцией**.  
  
3.  Обратите внимание, что имеется пакет с **EIMBatch** , отправленное в списке. Нажмите кнопку **импорта данных** в строке меню, если вы не видите следующий экран.  
  
     ![Пакет EIM](../../2014/tutorials/media/et-verifyingwithmasterdatamanager.jpg "пакет EIM")  
  
4.  Переключитесь обратно на домашнюю страницу, щелкните **SQL Server 2012 Master Data Services** вверху.  
  
5.  Убедитесь, что **поставщики** выбрана модель **модели** и **VERSION_1** выбран для **версии**и нажмите кнопку  **Обозреватель**.  
  
6.  Вы можете просмотреть данные, импортированные пакетом служб SSIS в MDS. Данные должны быть очищены и не должны содержать повторяющихся **кода** значения (Примечание: **SupplierID** столбец в Excel соответствует **кода** атрибут сущности Supplier в MDS).  
  
## <a name="next-step"></a>Следующий шаг  
 [Задача 17. Обзор проекта очистки данных DQS, созданного пакетом служб SSIS](../../2014/tutorials/task-17-reviewing-dqs-cleansing-project-created-by-the-ssis-package.md)  
  
  
